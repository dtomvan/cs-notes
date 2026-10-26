
```space-lua

utils = utils or {}
function utils.getPageDirectory(page)
  return string.gsub(page, "/*[^/]+$", "")
end

function utils.getPageName(page)
  local split = string.split(page, "/")
  local last = page
  for part in split do
    last = part
  end
  return last
end

command.define {
  name = "Page: Create Page",
  run = function()
    local current = editor.getCurrentPage()
    local path = utils.getPageDirectory(current)
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