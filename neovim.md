# neovim安装

1. `brew install nvim`

2. [LazyVim](http://www.lazyvim.org/installation)

3. `cd ~/.config/nvim/lua/plugins`

4. `vi neo-tree.lua`

5. ```bash
   return {
           "folke/snacks.nvim",
           opts = {
                   explorer = {},
                   picker = {
                           sources = {
                                   explorer = {
                                           layout = {
                                                   preset = "sidebar",
                                               		preview = false,
                                                   layout = {
                                                           position = "right";
                                                   }
                                            },
                                   },
                           },
                   },
   
                   layout = {
                           sidebar = { position = "right" },
                   },
           },
   }
   ```

   