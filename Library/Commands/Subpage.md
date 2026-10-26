
```space-lua
sub=sub or {}

-- Return the current directory path
function sub.dir()
  dir = editor.getCurrentPageMeta()
  -- Find last occurence of /
  i = string.find(dir.name, "/[^/]*$")
  path = string.sub(dir.name,1,i)
  return path
end

command.define {
  name = "Create sibling page",
  run = function()
    local newpath = sub.dir()
    editor.navigate(editor.prompt("Create new page under "..newpath, newpath))
  end
}

command.define {
  name = "Create subpage",
  run = function()
    local newpath = editor.getCurrentPage()
    editor.navigate(editor.prompt("Create new page under "..newpath, newpath .. "/"))
  end
}
```

#meta