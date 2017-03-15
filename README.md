# mivim-go
the option of vim go

## Install vundle
1. Set up [Vundle]:
    `$ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim`
2. Put this at the top of your `.vimrc` to use Vundle. Remove plugins you don't need, they are for illustration purposes.
    ```vim
    set nocompatible
    set rtp+=~/.vim/bundle/Vundle.vim
    call vundle#begin()
    Plugin 'VundleVim/Vundle.vim'
    Plugin 'fatih/vim-go'
    Plugin 'Valloric/YouCompleteMe'
    Plugin 'kien/ctrlp.vim'
    Plugin 'majutsushi/tagbar'
    Plugin 'vim-scripts/Syntastic'
