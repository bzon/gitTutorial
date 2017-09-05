# VIM

Full documentation: https://vim.sourceforge.io/docs.php  

Create a file and open it in a vim editor  
```bash
vim hello_world.sh
```

# Commands Table of Contents
- [Inserting and Deleting text](#inserting-and-deleting-text)
- [Saving Changes & Quit](#saving-changes-and-exit)
- [Challenge 1](#challenge-1)
- [Challenge 2](#challenge-2)
---

## Inserting and Deleting text
 
Press `ESC` + `I`, then type the text. 

You can use `backspace` or `delete` to delete a text.  

![img](./img/vim_insert.gif)

## Saving Changes and Exit

Press `ESC` + `:` + `w`, hit `Enter` to save  
Press `ESC` + `:` + `q`, hit `Enter` to exit  
__OR__
Press `ESC` + `:` + `wq`, hit `Enter` to save and then exit  

![gif](./img/vim_save_and_quit.gif)

## Challenge 1

Create a .vimrc file in your HOME directory and the following content.  

```
set paste

filetype plugin indent on
" show existing tab with 4 spaces width
set tabstop=4
" when indenting with '>', use 4 spaces width
set shiftwidth=4
" On pressing tab, insert 4 spaces
set expandtab

syntax on
let &t_Co=256
```

__HINTS:__ 
- use `vim $HOME/.vimrc` to create and open the file. 
- `Shift` + `Insert`, to paste a copied text.  

## Challenge 2

Update your `$HOME/.gitconfig file using vim by adding the following configurations.  

```bash
[user]
    name = John Bryan Sazon
    email = john.bryan.j.sazon@accenture.com
[alias]
    gl = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
    dt = !sh -c 'git diff-tree --no-commit-id --name-only -r $1' -
    s = status
    b = branch
    c = checkout
    autocrlf = false
    editor = vim
[core]
    longpaths = true
[credential]
    helper = store
```

__HINTS:__ 
- use `vim $HOME/.gitconfig` to create and open the file. 
- `Shift` + `Insert`, to paste a copied text.  
- `ESC` + `dd`, to delete the a line.  