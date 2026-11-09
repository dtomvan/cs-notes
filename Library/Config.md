

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

```

#meta

```space-lua
-- managed-by: configuration-manager
-- boot: true
config.set("frontmatterFolding.foldByDefault", "always")
config.set("fonts.ui", "gelasio")
config.set("fonts.editor", "gelasio")
```
