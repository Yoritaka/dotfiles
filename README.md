# make

    $ cd ~
    $ mkdir dotfiles
    $ git submodule add https://github.com/Shougo/neobundle.vim.git bundle/neobundle.vim

# install

    $ git clone --recursive https://github.com/Yoritaka/dotfiles.git


# sample
    " Note: Skip initialization for vim-tiny or vim-small.
    if 0 | endif
    
    if &compatible
      set nocompatible               " Be iMproved
    endif
    
    " Required:
    set runtimepath+=~/dotfiles/bundle/neobundle.vim/
    
    " Required:
    call neobundle#begin(expand('~/dotfiles/bundle/'))
    
    " Let NeoBundle manage NeoBundle
    " Required:
    NeoBundleFetch 'Shougo/neobundle.vim'
    
    " My Bundles here:
    " Refer to |:NeoBundle-examples|.
    " Note: You don't set neobundle setting in .gvimrc!
    
    " 以下は必要に応じて追加
    NeoBundle 'Shougo/unite.vim'
    NeoBundle 'Shougo/unite-outline'
    NeoBundle 'Align'
    
    " ファイルオープンを便利に
    NeoBundle 'Shougo/unite.vim'
    " Unite.vimで最近使ったファイルを表示できるようにする
    NeoBundle 'Shougo/neomru.vim'
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    " ファイルをtree表示してくれる
    " 
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    NeoBundle 'scrooloose/nerdtree'
    
    let g:NERDTreeShowBookmarks=1
    autocmd vimenter * NERDTree
    autocmd StdinReadPre * let s:std_in=1
    autocmd VimEnter * if argc() == 0 && !exists("s:std_in") | NERDTree | endif
    
    " NERDTress File highlighting
    function! NERDTreeHighlightFile(extension, fg, bg, guifg, guibg)
     exec 'autocmd filetype nerdtree highlight ' . a:extension .' ctermbg='. a:bg .' ctermfg='. a:fg .' guibg='. a:guibg .' guifg='. a:guifg
     exec 'autocmd filetype nerdtree syn match ' . a:extension .' #^\s\+.*'. a:extension .'$#'
    endfunction
    call NERDTreeHighlightFile('py',     'yellow',  'none', 'yellow',  '#151515')
    call NERDTreeHighlightFile('md',     'blue',    'none', '#3366FF', '#151515')
    call NERDTreeHighlightFile('yml',    'yellow',  'none', 'yellow',  '#151515')
    call NERDTreeHighlightFile('config', 'yellow',  'none', 'yellow',  '#151515')
    call NERDTreeHighlightFile('conf',   'yellow',  'none', 'yellow',  '#151515')
    call NERDTreeHighlightFile('json',   'yellow',  'none', 'yellow',  '#151515')
    call NERDTreeHighlightFile('html',   'yellow',  'none', 'yellow',  '#151515')
    call NERDTreeHighlightFile('styl',   'cyan',    'none', 'cyan',    '#151515')
    call NERDTreeHighlightFile('css',    'cyan',    'none', 'cyan',    '#151515')
    call NERDTreeHighlightFile('rb',     'Red',     'none', 'red',     '#151515')
    call NERDTreeHighlightFile('js',     'Red',     'none', '#ffa500', '#151515')
    call NERDTreeHighlightFile('php',    'Magenta', 'none', '#ff00ff', '#151515')
    
    let g:NERDTreeDirArrows = 1
    " let g:NERDTreeDirArrowExpandable  = ''
    " let g:NERDTreeDirArrowCollapsible = ''
    
    " シングルクオートとダブルクオートの入れ替え等
    NeoBundle 'tpope/vim-surround'
    " ステータスライン
    NeoBundle 'itchyny/lightline.vim'
    
    
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    " html5 setting
    " 
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    NeoBundle 'othree/html5.vim'
    
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    " css setting
    " 
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    " md setting
    " 
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    NeoBundle 'plasticboy/vim-markdown'
    NeoBundle 'kannokanno/previm'
    NeoBundle 'tyru/open-browser.vim'
    NeoBundle 'h1mesuke/vim-alignta'
    au BufRead,BufNewFile *.md set filetype=markdown
    
    
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    " howm setting
    " 
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    NeoBundle 'fuenor/qfixgrep'
    NeoBundle 'fuenor/qfixhowm'
    
    "" qfixhowm {{{
    " ファイル拡張子をmdにする
    let howm_filename = '%Y/%m/%Y-%m-%d-%H%M%S.md'
    " ファイルタイプをmarkdownにする
    let QFixHowm_FileType = 'markdown'
    " タイトル記号
    let QFixHowm_Title = '#'
    " タイトル行検索正規表現の辞書を初期化
    let QFixMRU_Title = {}
    " MRUでタイトル行とみなす正規表現(Vimの正規表現で指定)
    let QFixMRU_Title['mkd'] = '^###[^#]'
    " grepでタイトル行とみなす正規表現(使用するgrepによっては変更する必要があります)
    let QFixMRU_Title['mkd_regxp'] = '^###[^#]'
    " }}}
    
    
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    " color scheme theme
    " 
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    NeoBundle 'ujihisa/unite-colorscheme'
    NeoBundle 'tomasr/molokai'
    let g:molokai_original = 1
    let g:rehash256 = 1
    
    
    
    call neobundle#end()
    
    " Required:
    filetype plugin indent on
    
    " If there are uninstalled bundles found on startup,
    " this will conveniently prompt you to install them.
    NeoBundleCheck
    
    
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    " color scheme setting
    " 
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    
    colorscheme molokai
    if &term =~ "xterm-256color" || "screen-256color"
      set t_Co=256
      set t_Sf=[3%dm
      set t_Sb=[4%dm
    elseif &term =~ "xterm-color"
      set t_Co=8
      set t_Sf=[3%dm
      set t_Sb=[4%dm
    endif
    
    syntax enable
    hi PmenuSel cterm=reverse ctermfg=33 ctermbg=222 gui=reverse guifg=#3399ff guibg=#f0e68c
    
    
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    " 透過 setting
    " 
    """""""""""""""""""""""""""""""""""""""""""""""""""""""""
    
    autocmd GUIEnter * set transparency=240
    
    "半角文字の設定
    set guifont=Rounded_Mgen+_1mn_regular:h9
    
    "全角文字の設定
    set guifontwide=Rounded_Mgen+_1mn_regular:h9
    set number
    
    nnoremap sj <C-w>j
    nnoremap sk <C-w>k
    nnoremap sl <C-w>l
    nnoremap sh <C-w>h
    nnoremap sw <C-w>w
    

