![VIM Logo](https://i.imgur.com/K1z5WHQ.jpg)

# 

![screenshot](https://i.imgur.com/IRFUAWk.png)

Table of contents
=================

  * [Getting Started](#getting-started)
    * [Bash](#bash)
    * [Fish](#fish)
    * [Compile YCM](#compile-ycm)
    * [Base16](#base16-optional)
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
sh -c "$(curl -fsSL https://raw.githubusercontent.com/jarolrod/vim-python-ide/master/setup.sh)"
```
### Fish
```
curl -fsSL https://raw.githubusercontent.com/jarolrod/vim-python-ide/master/setup.sh | sh       
```
### Compile YCM
 * The YouCompleteMe Plugin must be compiled before use:
   * Navigate to the YouCompleteMe Folder which is found in:
     ```
     cd .vim/bundle/YouCompleteMe/
     ```
   * Next execute the following command:
     ```
     ./install.sh --clang-completer --system-libclang    
     ```
### Base16 (Optional)
Base16 is used to theme vim, it can also theme your terminal. Follow these steps to install, note that this part is optional:
 * Installing Base16
   Curl the base16 shell
   ```
   git clone https://github.com/chriskempson/base16-shell.git ~/.config/base16-shell
   ```
   * Add the following to your shell config (Themes terminal + vim):
     * FBASH + ZSH
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
Alternatively:
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
* [Syntastic](https://github.com/vim-syntastic/syntastic) - Syntax
* [Python Combined](https://github.com/mitsuhiko/vim-python-combined) - Extra handling
* [YouCompleteMe](https://github.com/Valloric/YouCompleteMe) - Code auto-completion
  * Navigate to bundle folder and execute command:
     ```
     ~/.vim/bundle/YouCompleteMe/install.py --clang-completer
     ```
  * Make sure to add the ycm_extra_conf.py file to:
    ```
     ~/.vim/
    ```

### Code and Project Navigation
* [NerdTree](https://github.com/scrooloose/nerdtree) - Project and File navigation
* [Tagbar](https://github.com/majutsushi/tagbar) - Class outline
* [CtrlSpace](https://github.com/vim-ctrlspace/vim-ctrlspace) - Bookmarks/Workspaces/Fuzzy Search/ File management
* [Ack](https://github.com/mileszs/ack.vim) - Search tool
* [Airline](https://github.com/vim-airline/vim-airline) - Tabline
* [Powerline](https://github.com/powerline/powerline) - Used for fonts
* [Fixed Task List](https://github.com/fisadev/FixedTaskList.vim) - Pending tasks
* [Conque Term](https://github.com/rosenfeld/conque-term) - Console as buffer
* [Comfortable Motion](https://github.com/yuttie/comfortable-motion.vim) - Physics based scrolling
* [Bookmarks](https://github.com/MattesGroeger/vim-bookmarks) - Bookmark code
* [Indent Guides](https://github.com/nathanaelkane/vim-indent-guides) - Visual repesentation of indents

### Snippets
* [Snippets](https://github.com/honza/vim-snippets) - Snippets
* [Snip-Mate](https://github.com/garbas/vim-snipmate) - Snippet Manager
* [NerdCommenter](https://github.com/scrooloose/nerdcommenter) - Easy code documentation
* [Commentary](https://github.com/tpope/vim-commentary) - Comment stuff out
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
  * Must install the base16 shell with the following:
    ```
    git clone https://github.com/chriskempson/base16-shell.git ~/.config/base16-shell
    ```
  * Add the following to your shell config (Themes terminal + vim):
    * FBASH + ZSH
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
      
* [Dev Icons](https://github.com/ryanoasis/vim-devicons) - File icons in NerdTree
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
    ```
* [TMUXLine](https://github.com/edkolev/tmuxline.vim) - Applies AirlineTheme to Tmux

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

