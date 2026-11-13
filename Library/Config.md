```space-style
html {
  --sb-tree-indent: .8rem;
}
```

```space-lua
-- boot: true
tag.define {
  name = "course",
  transform = function(o)
    o.pageDecoration = { icon = "book-open" }
    return o
  end
}

tag.define {
  name = "week",
  schema = {
    type = "object",
    properties = {
      parentCourse = {
        type = "string",
        description = "Parent course."
      },
      required = {"parentCourse"},
    },
  },
  transform = function(o)
    o.pageDecoration = { icon = "airplay" }
    return o
  end,
  renderFrontmatter = function(meta)
      return widget.new {
        markdown = spacelua.interpolate([==[
**Up:** ${parent}
]==], {parent=meta.parentCourse}),
        cssClasses = { "gotoParentCourse" }
      }
  end,
}
```

```space-lua
-- boot: true
view.define {
  name = "courses",
  title = "Courses",
  command = "Navigate: Courses",
  dock = "lhs",
  supportedDocks = { "lhs", "rhs", "modal" },
  followEditor = true,
  defaultOpen = true,
  refreshOn = { "index" },
  source = function()
    local pages = {}
    for _, page in ipairs(query[[from index.contentPages("course")]]) do
      -- HACK: get rid of Courses/ prefix, because we are guaranteed to be in that folder because of how I structured my shit
      page.name = string.gsub(page.name, "^Courses/", "")
      table.insert(pages, page)
    end
    return pages
  end,
  presentation = {
    mode = "tree",
    foldersFirst = false,
    expandAll = true,
    row = {
      icon = function(o)
        return "book-open"
      end,
    },
  },
  onSelect = function(o)
    if o.ref then
      editor.navigate(o.ref)
    end
    -- Opening a section page also unfolds its node in the tree.
    if o.hasChildren then
      return "navigator:expand"
    end
  end,
}

config.set("view.defaults", {
  ["courses"] = {
    dock = "lhs",
    open = true,
  },
  ["std.linkedMentions"] = {
    open = false,
  },
  ["std.toc"] = {
    dock = "page-top",
    open = true,
  }
})

for action, fn in pairs { ["Copy link to"] = editor.copyToClipboard, ["Open in"] = editor.openUrl } do
  for domain in each { "cs", "cs-mini" } do
    command.define {
      name = ("Navigate: %s %s.toostveen.nl"):format(action, domain),
      run = function()
        local meta = editor.getCurrentPageMeta()
        local ref
        if meta then
          ref = meta.ref or meta.name
        else
          ref = string.gsub(editor.getCurrentPath(), '\\.md$', '')
        end
        pcall(fn, ([[https://%s.toostveen.nl/%s]]):format(domain, ref))
      end,
    }
  end
end

actionButton.define {
  description = "Open in cs-mini.toostveen.nl",
  command = "Navigate: Open in cs-mini.toostveen.nl",
  icon = "external-link",
}
```

## Rounded code blocks

```space-style
.sb-code {
  padding: 2px;
  border: var(--base02) 1px solid;
  border-radius: 5px;
}
```

Really hacky: detect top line by the fact it has the copy button on it, and the bottom line that it has \`\`\` and no copy button...

```space-style
.sb-line-code-outside:has(.sb-actions) {
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}
.sb-line-code-outside:not(:has(.sb-actions)) {
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
}
```

```space-lua
-- managed-by: configuration-manager
-- boot: true
config.set("frontmatterFolding.foldByDefault", "always")
config.set("fonts.ui", "ia-writer-quattro")
config.set("fonts.editor", "ia-writer-quattro")
```

```space-style
.sb-modal:has(> .sb-nav-root-modal) {
  box-shadow: none;
}
```

# Snippets

## Matrix
```space-lua
slashCommand.define {
  name = "matrix",
  description = "insert a latex equation with a bmatrix in it",
  run = function()
    editor.insertAtCursor([==[
$$
\begin{bmatrix}
    |^|
\end{bmatrix}
$$
]==], false, true)
  end
}
```