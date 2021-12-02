```bash
set nocompatible
syntax on
filetype plugin indent on
set ic
set hlsearch
set encoding=utf-8
set fileencodings=utf-8,ucs-bom,GB2312,big5

"set cursorline"
set autoindent
set smartindent
set scrolloff=4
set showmatch
set nu
set tabstop=2
set softtabstop=2
set shiftwidth=2

" for python file"

let python_highlight_all=1
au Filetype python set tabstop=4
au Filetype python set softtabstop=4
au Filetype python set shiftwidth=4
au Filetype python set textwidth=79
au Filetype python set expandtab
au Filetype python set autoindent
au Filetype python set fileformat=unix
autocmd Filetype python set foldmethod=indent
autocmd Filetype python set foldlevel=99

" GoTo code navigation."
nmap <silent> gv :call CocAction('jumpDefinition', 'vsplit')<cr>
nmap <silent> gd :call CocAction('jumpDefinition')<cr>
" Search workspace symbols."
nnoremap <silent><nowait> <space>s  :<C-u>CocList -I symbols<cr>
"git"
function GitDiff()
    :silent write
    :silent execute '!git diff --color=always -- ' . expand('%:p') . ' | less --RAW-CONTROL-CHARS'
    :redraw!
endfunction
nnoremap <silent> gt :call GitDiff()<cr>

"plugin setup"
call plug#begin('~/.vim/plugged')

"js & ts"
Plug 'pangloss/vim-javascript'
Plug 'leafgarland/typescript-vim'
Plug 'maxmellon/vim-jsx-pretty'

"lsp"
Plug 'neoclide/coc.nvim' , { 'branch' : 'release','do': { -> coc#util#install() } }

" Git Support"
Plug 'kablamo/vim-git-log'
Plug 'gregsexton/gitv'
Plug 'tpope/vim-fugitive'

" Markdown / Writting"
Plug 'reedes/vim-pencil'
Plug 'tpope/vim-markdown'
Plug 'jtratner/vim-flavored-markdown'

" Utility"
Plug 'scrooloose/nerdtree'
Plug 'vim-airline/vim-airline'

call plug#end()
```