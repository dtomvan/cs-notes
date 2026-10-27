```space-lua
-- priority: 10
actionButton.define {
  icon = "sidebar",
  description = "Sidebar",
  command = "Navigate: Tree",
}

```

```space-style
html {
  --ui-font: "Inter", sans-serif!important;
  --editor-font: "Inter", sans-serif;
}

code, pre, .sb-line-fenced-code, .sb-code {
  font-family: "AporeticSansM Nerd Font", monospace;
}

#sb-current-page {
  font-size: large!important;
  margin: auto;
}

.sb-frontmatter:not(.gotoParentCourse) {
  opacity: .5;
}

.sb-frontmatter-preview:has(.gotoParentCourse) {
  background-color: var(--subtle-background-color);
  padding: 2em;
  padding-bottom: 2em!important;
}
```

```space-lua
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
-- priority: 50
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
      table.insert(pages, page)
    end
    return pages
  end,
  presentation = {
    mode = "tree",
    foldersFirst = false,
    limit = 500,
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

view.open("courses")
```

#meta

```space-lua
-- managed-by: configuration-manager
config.set("frontmatterFolding.foldByDefault", "always")
```
