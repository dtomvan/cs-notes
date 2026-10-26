```space-lua
slashcommand.define {
  name = "date",
  run = function()
    editor.insertAtCursor(os.date("%Y-%M-%d"))
  end
}
```

#meta