set nocompatible            " 关闭 vi 兼容模式
syntax on                   " 自动语法高亮
set number                  " 显示行号
set nobackup                " 覆盖文件时不备份
set autochdir               " 自动切换当前目录为当前文件所在的目录
set ignorecase smartcase    " 搜索时忽略大小写，但在有一个或以上大写字母时仍保持对大小写敏感
set nowrapscan              " 禁止在搜索到文件两端时重新搜索
set incsearch               " 输入搜索内容时就显示搜索结果
set hlsearch                " 搜索时高亮显示被找到的文本
set smartindent             " 开启新行时使用智能自动缩进
set tabstop=4               " tab等于4空格
set expandtab               " 不要用空格代替制表符
set shiftwidth=4            " 设置tab的宽度
set softtabstop=4           " 敲入tab键时实际占有的列数
set encoding=utf-8          " 设置Vim的内部编码
set autoindent              " 设置自动对齐(缩进):即每行的缩进值与上一行相等
set cindent                 " 设置使用 C/C++ 语言的自动缩进方式