```space-lua
slashcommand.define {
  name = "date",
  run = function()
    editor.insertAtCursor(date.today())
  end
}
```

#meta