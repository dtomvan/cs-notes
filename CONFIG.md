```space-lua
config.set {
  silversearch = {
    ignore = {
      "**.pdf"
    }
  }
}

editor.invokeCommand("Navigate: Tree")
```

```space-style
html {
  --ui-font: "Inter", sans-serif!important;
  --editor-font: "AporeticSansM Nerd Font", monospace!important;
}
```

${config.get("sync.documents")}
${system.}
```space-lua
config.set("sync.documents", system.getProfile().username == "tom")
```
