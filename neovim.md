### install neovim

```
brew install neovim
```
### `~`
```
mkdir -p ~/.config/nvim/lua
cd ~/.config/nvim
touch init.lua

cd -
mkdir kevin/
cd kevin/
mkdir core/ plugins/

touch plugins-setup.lua

cd core/
touch colorscheme.lua keymaps.lua options.lua
```

```
cd ~/.config/nvim
nvim init.lua
```

```
require("kevin.core.options")
require("kevin.core.keymaps")
require("kevin.core.colorscheme")
:wq
```

```
cd lua/kevin/core
nvim options.lua
```

```
-- for conciseness
local opt = vim.opt 

-- line numbers
opt.relativenumber = true
opt.number = true
:wq
```

