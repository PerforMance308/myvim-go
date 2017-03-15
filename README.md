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
    call vundle#end()            " required
    filetype plugin indent on    " required
    ```
3. Install Plugins:

    Launch `vim` and run `:PluginInstall`
   
4. make YouCompleteMe

    ```
    cd ~/.vim/bundle/YouCompleteMe
    ./install.py --all
    ```

5. install vim go deps
    
    Launch `vim` and run `:GoInstallBinaries` or `:GoUpdateBinaries`
