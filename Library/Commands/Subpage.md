
```space-lua
command.define {
  name = "Page: Create Page",
  run = function()
    local current = editor.getCurrentPage()
    local path = string.gsub(current, "/*[^/]+$", "")
    if path ~= "" then path = path .. "/" end
    local name = editor.prompt("Enter name of new page", path)
    if not name then return else editor.navigate(name) end
  end
}

command.define {
  name = "Page: Create Subpage",
  run = function()
    local current = editor.getCurrentPage()
    local name = editor.prompt("Enter name of new subpage", current .. "/")
    if not name then return else editor.navigate(name) end
  end
}
```

#meta