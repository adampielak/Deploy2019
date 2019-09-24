#### User settings
```bash
:checkhealth
# file name : init.vim
# file path ~/.config/nvim/init.vim
```
#### Plugin install
```vim
wget https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
mkdir -p ~/.config/nvim/autoload
mv plug.vim ~/.config/nvim/autoload
```
#### Sample configuration
```bash
syntax on                                                                                       
set number relativenumber                                                      
set cursorline                                                                  
set colorcolumn=80                                                              
                                                                                
set foldlevel=0                                                                 
set history=500                                                                 
set title

let g:VIM_PLUG_PATH = expand(stdpath('config') . '/autoload/plug.vim')          
let g:PLUGIN_HOME = expand(stdpath('config') . '')                         
                                                                                
call plug#begin(g:PLUGIN_HOME)                                                  
Plug 'Shougo/deoplete.nvim', { 'do': ':UpdateRemotePlugins' }                   
Plug 'vim-airline/vim-airline'                                                  
Plug 'sheerun/vim-polyglot'                                                     
Plug 'sainnhe/vim-color-desert-night'                                           
call plug#end()                                                                             
colo desert-night 
```
#### Resources
```bash
https://devtechnica.com/vim-neovim/best-neovim-plugins-for-software-development-in-2019
```
