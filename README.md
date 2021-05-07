# Git for Neovim (In Development)

Visual Git Plugin for Neovim to enhance your git experience.

### Features
- [x] Hunk signs

 ![hunk_signs](https://user-images.githubusercontent.com/25164326/117380418-a3741f80-aea7-11eb-87f8-1eb0093cb6a5.gif)

- [x] Reset a hunk

![hunk_reset](https://user-images.githubusercontent.com/25164326/117384279-9dcf0780-aeb0-11eb-96d8-0b85239d94f7.gif)

- [x] Hunk preview

![hunk_preview](https://user-images.githubusercontent.com/25164326/117380403-9a834e00-aea7-11eb-9117-f90cb4ab2ff1.gif)

- [x] Hunk navigation in current buffer

![hunk_navigation](https://user-images.githubusercontent.com/25164326/117380412-9f480200-aea7-11eb-8630-c70781e7e2ce.gif)

- [x] Show original file and current file in a split window with diffs highlighted

![diff_preview](https://user-images.githubusercontent.com/25164326/117380396-95be9a00-aea7-11eb-8fad-f9b6c6b87a5f.gif)

- [x] Reset changes in a buffer

![buffer_reset](https://user-images.githubusercontent.com/25164326/117384280-9e679e00-aeb0-11eb-850a-551925c81d3e.gif)

- [x] Blame a line

![blame](https://user-images.githubusercontent.com/25164326/117380374-8dfef580-aea7-11eb-8349-ff7941337419.gif)


## Prerequisites
- [Git](https://git-scm.com/)
- [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter)
- [plenary.nvim](https://github.com/nvim-lua/plenary.nvim)

## Installation

| Plugin Manager                                       | Command                                                                        |
|------------------------------------------------------|--------------------------------------------------------------------------------|
| [Packer](https://github.com/wbthomason/packer.nvim)  | `use { 'tanvirtin/vgit.nvim', requires = 'nvim-lua/plenary.nvim' }`            |
| [Vim-plug](https://github.com/junegunn/vim-plug)     | `Plug 'tanvirtin/vgit.nvim'`                                                   |
| [NeoBundle](https://github.com/Shougo/neobundle.vim) | `NeoBundle 'tanvirtin/vgit.nvim'`                                              |
| [Vundle](https://github.com/VundleVim/Vundle.vim)    | `Bundle 'tanvirtin/vgit.nvim'`                                                 |
| [Pathogen](https://github.com/tpope/vim-pathogen)    | `git clone https://github.com/tanvirtin/vgit.nvim.git ~/.vim/bundle/vgit.nvim` |
| [Dein](https://github.com/Shougo/dein.vim)           | `call dein#add('tanvirtin/vgit.nvim')`                                         |

You also use in the built-in package manager:
```bash
$ git clone --depth 1 https://github.com/tanvirtin/vgit.nvim $XDG_CONFIG_HOME/nvim/pack/plugins/start/vgit.nvim
```

### Configure Mappings
```
vim.api.nvim_set_keymap('n', '<leader>gh', ':lua require("git").hunk_preview()<CR>', { noremap = true, silent = true })
vim.api.nvim_set_keymap('n', '<leader>gr', ':lua require("git").hunk_reset()<CR>', { noremap = true, silent = true })
vim.api.nvim_set_keymap('n', '<space>]', ':lua require("git").hunk_up()<CR>', { noremap = true, silent = true })
vim.api.nvim_set_keymap('n', '<space>[', ':lua require("git").hunk_down()<CR>', { noremap = true, silent = true })
vim.api.nvim_set_keymap('n', '<space>gd', ':lua require("git").buffer_preview()<CR>', { noremap = true, silent = true })
vim.api.nvim_set_keymap('n', '<space>gd', ':lua require("git").buffer_reset()<CR>', { noremap = true, silent = true })
```

### API
| Function Name | Description |
|---------------|-------------|
| setup | Sets up the plugin to run necessary git commands on loaded buffers |
| hunk_preview | If a file has a hunk of diff associated with it, invoking this function will reveal that hunk if it exists on the current cursor |
| hunk_reset | Resets the hunk the cursor is on right now to it's previous step
| hunk_down | Navigate downward through a github hunk |
| hunk_up | Navigate upwards through a github hunk |
| buffer_preview | Opens two windows, showing cwd and origin buffers and the diff between them |
| buffer_reset | Resets a current buffer you are on |
