set nocompatible              " be iMproved, required
filetype off                  " required

" git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim

call vundle#begin()

" let Vundle manage Vundle, required
Plugin 'gmarik/Vundle.vim'

" plugin on GitHub repo
Plugin 'scrooloose/nerdtree'                   "目录管理
Plugin 'kien/ctrlp.vim'                        "模糊搜索
Plugin 'bling/vim-airline'                     "状态栏增强
Plugin 'scrooloose/nerdcommenter'              "快速注释
Plugin 'vim-scripts/bufexplorer.zip'           "可以打开历史文件列表以达到快速切换文件的目的
Plugin 'vim-scripts/cscope.vim'                "找到某个函数或变量的定义位置,需要安装cscope
Plugin 'vim-scripts/taglist.vim'               "标签（宏, 全局变量, 函数名等）管理，需要安装ctags

call vundle#end()

" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal

filetype plugin on    " required

syntax on " 自动语法高亮
set number " 显示行号
set cursorline " 突出显示当前行
" set ruler " 打开状态栏标尺
set shiftwidth=4 " 设定 << 和 >> 命令移动时的宽度为 4
set tabstop=4 expandtab " 设定 tab 长度为 4 个空格
set nobackup " 覆盖文件时不备份
" set autochdir " 自动切换当前目录为当前文件所在的目录
set backupcopy=yes " 设置备份时的行为为覆盖
set ignorecase smartcase " 搜索时忽略大小写，但在有一个或以上大写字母时仍保持对大小写敏感
set nowrapscan " 禁止在搜索到文件两端时重新搜索
" set incsearch " 输入搜索内容时就显示搜索结果
set hlsearch " 搜索时高亮显示被找到的文本
set noerrorbells " 关闭错误信息响铃
set novisualbell " 关闭使用可视响铃代替呼叫
set t_vb= " 置空错误铃声的终端代码
set magic " 设置魔术
set hidden " 允许在有未保存的修改时切换缓冲区，此时的修改由 vim 负责保存
set guioptions-=T " 隐藏工具栏
set guioptions-=m " 隐藏菜单栏
set smartindent " 开启新行时使用智能自动缩进
set backspace=indent,eol,start " 不设定在插入状态无法用退格键和 Delete 键删除回车符
set cmdheight=1 " 设定命令行的行数为 1
set laststatus=2 " 显示状态栏 (默认值为 1, 无法显示状态栏)
set statusline=\ %<%F[%1*%M%*%n%R%H]%=\ %y\ %0(%{&fileformat}\ %{&encoding}\ %c:%l/%L%)\  " 设置在状态行显示的信息
set errorformat=%m\ in\ %f\ on\ line\ %l
set autoindent 
set softtabstop=4 " 使得按退格键时可以一次删掉 4 个空格

" https://github.com/mayer2014/.vimToIDE/blob/master/colors/gruvbox.vim
colorscheme gruvbox 
set background=dark

" 用户目录变量$VIMFILES
let $VIMFILES = $HOME.'/.vim'
set backupdir=/tmp

" 配置多语言环境
if has("multi_byte")
	set encoding=utf-8
	set termencoding=utf-8
	set formatoptions+=mM
	set fencs=utf-8,gbk
	if v:lang =~? '^\(zh\)\|\(ja\)\|\(ko\)'
		set ambiwidth=double
	endif
endif

" 光标到上方窗口,需要<c-w><c-w>k,非常麻烦,现在重映射为<c-k>
nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l

"一些不错的映射转换语法（如果在一个文件中混合了不同语言时有用）
nnoremap <leader>1 :set filetype=xhtml<CR>
nnoremap <leader>2 :set filetype=css<CR>
nnoremap <leader>3 :set filetype=javascript<CR>
nnoremap <leader>4 :set filetype=php<CR>

"-----------------------------------------------------------------
" 折叠配置
"------------------------------------------------------------------
set foldenable
set foldmethod=manual
set foldlevel=100 " 启动vim时不要自动折叠代码
set foldcolumn=0 " 设置折叠栏宽度

"-----------------------------------------------------------------
" plugin - NERDTree 配置
"-----------------------------------------------------------------
let NERDTreeWinPos="left"
let NERDTreeWinSize=30
" let NERDTreeChDirMode=1 " 改变tree目录的同时改变工程的目录
nnoremap <silent><F6> :NERDTreeToggle<CR>


"-----------------------------------------------------------------
" plugin - ctags程序
"-----------------------------------------------------------------
let Tlist_Ctags_Cmd = '/usr/bin/ctags'
set tags=~/acl/tags;
nnoremap <silent><F8> :!ctags -R --exclude=*.js --c++-kinds=+p --fields=+iaS --extra=+q .<CR>


"-----------------------------------------------------------------
" plugin - taglist.vim 
"-----------------------------------------------------------------
let Tlist_Show_One_File = 1 " 不同时显示多个文件的tag，只显示当前文件的
let Tlist_Exit_OnlyWindow = 1 " 如果taglist窗口是最后一个窗口，则退出vim
let Tlist_Use_Right_Window = 1 " 在右侧窗口中显示taglist窗口
let Tlist_File_Fold_Auto_Close=1 " 自动折叠当前非编辑文件的方法列表
let Tlist_Auto_Open = 0
let Tlist_Auto_Update = 1
let Tlist_Hightlight_Tag_On_BufEnter = 1
let Tlist_Enable_Fold_Column = 0
let Tlist_Compact_Format = 1
" let Tlist_Display_Prototype = 0
nnoremap <silent><F7> :TlistToggle<CR>


"-----------------------------------------------------------------
" plugin - cscope设置
"-----------------------------------------------------------------
set cscopequickfix=s-,c-,d-,i-,t-,e-    
if has("cscope")    
	set csprg=/usr/bin/cscope    
	set csto=1    
	set cst    
	set nocsverb    

	" add any database in current directory     
	" if filereadable("cscope.out")    
	" 	cs add cscope.out    
	" endif    
	" 	set csverb    
	" endif    
	     
	nmap <C-@>s :cs find s <C-R>=expand("<cword>")<CR><CR>
	nmap <C-@>g :cs find g <C-R>=expand("<cword>")<CR><CR>
	nmap <C-@>c :cs find c <C-R>=expand("<cword>")<CR><CR>
	nmap <C-@>t :cs find t <C-R>=expand("<cword>")<CR><CR>
	nmap <C-@>e :cs find e <C-R>=expand("<cword>")<CR><CR>
	nmap <C-@>f :cs find f <C-R>=expand("<cfile>")<CR><CR>
	nmap <C-@>i :cs find i <C-R>=expand("<cfile>")<CR><CR>
	nmap <C-@>d :cs find d <C-R>=expand("<cword>")<CR><CR>
endif

"-----------------------------------------------------------------
" plugin - NERD_commenter.vim 注释代码用的，
"-----------------------------------------------------------------
let NERDSpaceDelims=1 " 让注释符与语句之间留一个空格
let NERDCompactSexyComs=1 " 多行注释时样子更好看

"-----------------------------------------------------------------
" plugin - ctrlp 设置
"-----------------------------------------------------------------
nnoremap <silent> <C-p> :ClearAllCtrlPCache<CR>\|:CtrlP<CR>
