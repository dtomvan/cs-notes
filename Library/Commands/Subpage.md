
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
  name = "Create Subpage",
  run = function()
    newpath = sub.dir()
    editor.prompt("Create ")
    editor.navigate(newpath..'New')
  end
}
```

#meta