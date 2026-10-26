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
  --editor-font: "AporeticSansM Nerd Font", monospace!important;
}

#sb-current-page {
  font-size: large!important;
  margin: auto;
}
```


```space-lua
view.define {
  name = "courses",
  title = "Courses",
  command = "Navigate: Courses",
  dock = "lhs",
  supportedDocks = { "lhs", "rhs", "modal" },
  followEditor = true,
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
```

#meta