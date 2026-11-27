# vis-oil

edit a folder like a buffer in [vis](https://github.com/martanne/vis), a port of [oil.nvim](https://github.com/stevearc/oil.nvim)

### install

needs vis `0.9` or later and `vis-menu`

```sh
git clone https://github.com/w0x7y/vis-oil ~/.config/vis/plugins/vis-oil
```

then in `visrc.lua`:

```lua
local oil = require("plugins/vis-oil")
vis:map(vis.modes.NORMAL, "-", oil.open_parent, "Edit parent folder")
```

### usage

~ `oil.open_parent` opens the current file's folder as a buffer, or the parent folder when already in an oil buffer\
~ dot folders come first, then folders, dot files and files; folders end in `/`\
~ `<Enter>` opens the file or folder under the cursor\
~ edit the buffer like normal text: rename a line to rename (`sub/name` moves it into `sub`), `dd` to delete, add a line to create a file (end it in `/` for a folder)\
~ `:w` lists the planned changes on the bottom line and asks before applying them

### config

```lua
local oil = require("plugins/vis-oil")
oil.styles.dir = "fore:blue"
```

`oil.folder(win)` returns the folder path shown in an oil window (with `~/` for `$HOME`), or `nil`, for status line plugins

### layout

```text
init.lua   vis plugin, buffer management and filesystem ops
plan.lua   pure lua diff planner (buffer edits -> rename/create/delete ops)
test.lua   unit tests for plan.lua (run with `lua test.lua`)
LICENSE    mit
```

_license: [mit](./LICENSE)_
