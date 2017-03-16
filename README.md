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
    Plugin 'scrooloose/nerdtree'
    call vundle#end()
    filetype plugin indent on
    ```
3. Install Plugins:

    Launch `vim` and run `:PluginInstall`
   
4. make YouCompleteMe

    ```
    cd ~/.vim/bundle/YouCompleteMe
    ./install.py --gocode-completer
    ```

5. install vim go deps
    
    Launch `vim` and run `:GoInstallBinaries` or `:GoUpdateBinaries`
    
6. Put this at the end of your `.vimrc`
    
    ```
    map <C-n> :NERDTreeToggle<CR>
    autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif
    let g:NERDTreeDirArrowExpandable = '▸'
    let g:NERDTreeDirArrowCollapsible = '▾'

    if !executable('ctags')
        finish
    elseif globpath(&rtp, 'plugin/tagbar.vim') == ""
        finish
    endif

    if !exists("g:go_gotags_bin")
        let g:go_gotags_bin = "gotags"
    endif

    function! s:SetTagbar()
    let bin_path = go#path#CheckBinPath(g:go_gotags_bin)
    if empty(bin_path)
        return
    endif

    if !exists("g:tagbar_type_go")
    let g:tagbar_type_go = {
          \ 'ctagstype' : 'go',
          \ 'kinds'     : [
          \ 'p:package',
          \ 'i:imports',
          \ 'c:constants',
          \ 'v:variables',
          \ 't:types',
          \ 'n:interfaces',
          \ 'w:fields',
          \ 'e:embedded',
          \ 'm:methods',
          \ 'r:constructor',
          \ 'f:functions'
          \ ],
          \ 'sro' : '.',
          \ 'kind2scope' : {
          \ 't' : 'ctype',
          \ 'n' : 'ntype'
          \ },
          \ 'scope2kind' : {
          \ 'ctype' : 't',
          \ 'ntype' : 'n'
          \ },
          \ 'ctagsbin'  : bin_path,
          \ 'ctagsargs' : '-sort -silent'
          \ }
    endif
    endfunction

    call s:SetTagbar()
    syntax on
    au BufRead,BufNewFile *.go set filetype=go
    set nu

    
7. install molokai color

    ```
    cd ~/.vim
    git clone https://github.com/tomasr/molokai.git
    mv molokai/colors ./
    ```
    
    put `colorscheme molokai` to your .vimrc
