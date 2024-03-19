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
### init.lua
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

```
-- tabs & indentation
opt.tabstop = 2
opt.shiftwidth = 2
opt.expandtab = true
opt.autoindent = true
```

```
-- line wrapping
opt.wrap = false

-- search settings
opt.ignorecase = true
opt.smartcase = true
```
```
-- cursor line
opt.cursorline = false

-- appearance
opt.termguicolors = false
-- opt.background = "dark"
-- opt.signcolumn = "yes"

-- backspace
opt.backspace = "indent,eol,start"

-- clipboard
opt.clipboard:append("unnamedplus")
 
-- split windows
opt.splitright = true
opt.splitbelow = true
  
-- 把-连接的词,当作一个词
opt.iskeyword:append("-")
```
### plugins-setup.lua
```
cd ..
ls
```

```
nvim plugins-setup.lua
```

### `https://github.com/wbthomason/packer.nvim?tab=readme-ov-file#bootstrapping`


```
local ensure_packer = function()
  local fn = vim.fn
  local install_path = fn.stdpath('data')..'/site/pack/packer/start/packer.nvim'
  if fn.empty(fn.glob(install_path)) > 0 then
    fn.system({'git', 'clone', '--depth', '1', 'https://github.com/wbthomason/packer.nvim', install_path})
    vim.cmd [[packadd packer.nvim]]
    return true
  end
  return false
end

local packer_bootstrap = ensure_packer()

return require('packer').startup(function(use)
  use 'wbthomason/packer.nvim'
  -- My plugins here
  -- use 'foo1/bar1.nvim'
  -- use 'foo2/bar2.nvim'

  -- Automatically set up your configuration after cloning packer.nvim
  -- Put this at the end after all plugins
  if packer_bootstrap then
    require('packer').sync()
  end
end)
```

```
vim.cmd([[
  augroup packer_user_config
    autocmd!
    autocmd BufWritePost plugins-setup.lua source <afile> | PackerCompile
  augroup end
]])
```