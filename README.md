![VIM Logo](https://i.imgur.com/wQgLi2F.jpg)

![screenshot](https://i.imgur.com/KoKH5aA.png)

Table of contents
=================

  * [Getting Started](#getting-started)
    * [Bash](#bash)
    * [Fish](#fish)
    * [Neovim](#neovim)
    * [Deoplete](#deoplete)
    * [Neomake](#neomake)
    * [Base16](#base16-optional)
    * [DevIcons](#devicons-optional)
    * [Manual Install](#alternatively)
  * [Plugins](#plugins)
    * [Python](#python)
    * [Code + Project Navigation](#code-and-project-navigation)
    * [Snippets](#snippets)
    * [Extra](#extra)
  * [Key Bindings](#key-bindings)
    * [Python](#python)
    * [Switching Between Buffers](#switching-between-buffers)
    * [Toggle Relative Numbering](#toggle-relative-numbering)
    * [Comfortable Motion Scrolling](#comfortable-motion-scrolling)
    * [NerdTree Toggle](#nerdtree-toggle)
    * [Disable Arrow Keys](#disable-arrow-keys)
  
## Getting Started

A script shell will get a copy of the vimrc up and running on your local machine for testing purposes:
### Bash 
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/sjzcv/vim-python-ide/master/setup.sh)"
```
### Fish
```
curl -fsSL https://raw.githubusercontent.com/sjzcv/vim-python-ide/master/setup.sh | sh       
```
### Neovim
* Dependency for Deoplete and NeoMake
* Installation:
 * ```
   pip3 install neovim
   ```
### Deoplete
 * An Asynchronous Completion Engine for Vim
 * Requirements:
  * Python 3
  * Vim 8+
  * [Neovim](#neovim) (to be used as a server)
  
### Neomake
 * Asynchronous Linting Engine for Vim 
 * Same requirements as [Deoplete](#deoplete)
 
### Base16 (Optional)
Base16 is used to theme vim, it can also theme your terminal. Follow these steps to install:
* Installing Base16
   ```
   git clone https://github.com/chriskempson/base16-shell.git ~/.config/base16-shell
   ```
   * Add the following to your shell config (Themes terminal + vim):
     * Bash + ZSH
       ```
       BASE16_SHELL=$HOME/.config/base16-shell/
       [ -n "$PS1" ] && [ -s $BASE16_SHELL/profile_helper.sh ] && eval "$($BASE16_SHELL/profile_helper.sh)"
       ```
     * Fish
       ```
       # Base16 Shell
       if status --is-interactive
           eval sh $HOME/.config/base16-shell/scripts/base16-default-dark.sh
       end
       ```
   * Add the following to your vimrc (Only theme vim):
     ```
     if filereadable(expand("~/.vimrc_background"))
       let base16colorspace=256
       source ~/.vimrc_background
     endif
     ```
* If you dont want this feature simply remove this plugin from your vimrc and execute :PluginUpdate in vim, for proper removal delete the base16 plugin folder 

### DevIcons (Optional)
This plugin is used to show file icons in NerdTree and requires additional steps to install:
* Must install a patched font that contains required glyphs: 
    * [Arch Linux](https://aur.archlinux.org/packages/nerd-fonts-complete/)
    * [Everyone Else](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts)
  * Set vim encoding to UTF-8
    ```
    set encoding=utf8
    ```
  * Set vim font to NerdFont
    ```
    set guifont=<FONT_NAME> <FONT_SIZE>
    ```
  * Add glyphs to Airline
    ```
    let g:airline_powerline_fonts = 1
* If you dont want this feature simply remove this plugin from your vimrc and execute :PluginUpdate in vim, for proper removal delete the devicons plugin folder

### Alternatively:
* Cherry pick the parts you like from my vimrc and add it to yours

## Plugins
### Python
* [Python Mode](https://github.com/python-mode/python-mode) - Python mode
  * Add the following to the bottom of your vimrc to prevent errors:
    ```
     python3 << EOF
     import vim
     import git
     def is_git_repo():
           try:
               _ = git.Repo('.', search_parent_directories=True).git_dir
               return "1"
           except:
               return "0"
     vim.command("let g:pymode_rope = " + is_git_repo())
     EOF                 
    ```
* [PEP 8 Indentation](https://github.com/Vimjas/vim-python-pep8-indent) - Python Indentation
* [Jinja](https://github.com/lepture/vim-jinja) - Syntax and Indentation
* [Neomake](https://github.com/neomake/neomake) - An Asynchronous version of Syntastic
* [Deoplete](https://github.com/Shougo/deoplete.nvim) - Asynchronous Compeletion Engine
* [Python Combined](https://github.com/mitsuhiko/vim-python-combined) - Extra handling


### Code and Project Navigation
* [NerdTree](https://github.com/scrooloose/nerdtree) - Project and File navigation
* [Tagbar](https://github.com/majutsushi/tagbar) - Class outline
* [CtrlSpace](https://github.com/vim-ctrlspace/vim-ctrlspace) - Bookmarks/Workspaces/Fuzzy Search/ File management
* [Ack](https://github.com/mileszs/ack.vim) - Search tool
* [Airline](https://github.com/vim-airline/vim-airline) - Tabline
* [Powerline](https://github.com/powerline/powerline) - Used for fonts
* [Fixed Task List](https://github.com/fisadev/FixedTaskList.vim) - Pending tasks
* [Comfortable Motion](https://github.com/yuttie/comfortable-motion.vim) - Physics based scrolling
* [Bookmarks](https://github.com/MattesGroeger/vim-bookmarks) - Bookmark code
* [Indent Guides](https://github.com/nathanaelkane/vim-indent-guides) - Visual repesentation of indents

### Snippets
* [Snippets](https://github.com/honza/vim-snippets) - Snippets
* [Snip-Mate](https://github.com/garbas/vim-snipmate) - Snippet Manager
* [NerdCommenter](https://github.com/scrooloose/nerdcommenter) - Easy code documentation
* [Utility Functions](https://github.com/tomtom/tlib_vim) - Add-on
* [Add-on](https://github.com/MarcWeber/vim-addon-mw-utils) - interpret file by function

### Extra 
* [Sparkup](https://github.com/rstacruz/sparkup) - Condensed HTML parser
* [Riv](https://github.com/Rykka/riv.vim) - Take notes in RST
* [Surround](https://github.com/tpope/vim-surround) - Add parentheses + etc. in pairs
* [Colorscheme](https://github.com/flazz/vim-colorschemes) - Change vim colorscheme
* [Rainbow-Parantheses](https://github.com/kien/rainbow_parentheses.vim) - Rianbow Parentheses
* [Vim-Wiki](https://github.com/vimwiki/vimwiki) - Personal Vim wiki
* [Vimagit](https://github.com/jreybert/vimagit) - Git operations from buffer
* [Base16](https://github.com/chriskempson/base16-vim) - Base16 Themes
  * [Base16 Installation](#base16-optional)
* [Dev Icons](https://github.com/ryanoasis/vim-devicons) - File icons in NerdTree
  * [DevIcons Installation](#devicons-optional)

## Key-Bindings
### Python 
```
let g:pymode_run_bind='<F5>'
imap <F5> <Esc>:w<CR>:!clear;python %<CR>
```
### Switching Between Buffers
```
nmap <F9> :bprev<CR>
nmap <F10> :bnext<CR>
```
### Toggle Relative Numbering
```
nnoremap <F4> :set relativenumber!<CR>
```
### Comfortable Motion Scrolling
```
let g:comfortable_motion_scroll_down_key = "j"
let g:comfortable_motion_scroll_up_key = "k"  
```
```
nnoremap <silent> <C-d> :call comfortable_motion#flick(g:comfortable_motion_imp    ulse_multiplier * winheight(0) * 2)<CR>
nnoremap <silent> <C-u> :call comfortable_motion#flick(g:comfortable_motion_imp    ulse_multiplier * winheight(0) * -2)<CR>
nnoremap <silent> <C-f> :call comfortable_motion#flick(g:comfortable_motion_imp    ulse_multiplier * winheight(0) * 4)<CR>
nnoremap <silent> <C-b> :call comfortable_motion#flick(g:comfortable_motion_imp    ulse_multiplier * winheight(0) * -4)<CR>
```

### NerdTree Toggle
* NerdTree wil automatically open when vim is launched in terminal without a file
```
nmap " :NERDTreeToggle<CR>
```
### Disable Arrow Keys
```
no <down> <Nop>
no <left> <Nop>
no <right> <Nop>
no <up> <Nop>

ino <down> <Nop>
ino <left> <Nop>
ino <right> <Nop>
ino <up> <Nop>
                                                                               
vno <down> <Nop>
vno <left> <Nop>
vno <right> <Nop>
vno <up> <Nop>
```

