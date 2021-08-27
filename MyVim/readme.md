# My Vim

# My Vim Setting

window환경

1) gvim  설치 

[gvim 설치](https://www.vim.org/)

- 왼쪽 Download 버튼 클릭

<img src="https://user-images.githubusercontent.com/56623911/131155172-62fcd1ad-467d-4325-a2ff-061953f9ca8e.png">

- PC MS-DOS and MS-Windows  버튼 클릭

![제목_없음](https://user-images.githubusercontent.com/56623911/131155235-fc6167b3-5857-4288-8438-952699813fc6.png)

2) __Vimrc setting 하기 

처음 환경 설정 Default 값으로 설정된 환경

```Shell
" Vim with all enhancements
source $VIMRUNTIME/vimrc_example.vim

" Use the internal diff if available.
" Otherwise use the special 'diffexpr' for Windows.
if &diffopt !~# 'internal'
  set diffexpr=MyDiff()
endif
function MyDiff()
  let opt = '-a --binary '
  if &diffopt =~ 'icase' | let opt = opt . '-i ' | endif
  if &diffopt =~ 'iwhite' | let opt = opt . '-b ' | endif
  let arg1 = v:fname_in
  if arg1 =~ ' ' | let arg1 = '"' . arg1 . '"' | endif
  let arg1 = substitute(arg1, '!', '\!', 'g')
  let arg2 = v:fname_new
  if arg2 =~ ' ' | let arg2 = '"' . arg2 . '"' | endif
  let arg2 = substitute(arg2, '!', '\!', 'g')
  let arg3 = v:fname_out
  if arg3 =~ ' ' | let arg3 = '"' . arg3 . '"' | endif
  let arg3 = substitute(arg3, '!', '\!', 'g')
  if $VIMRUNTIME =~ ' '
    if &sh =~ '\<cmd'
      if empty(&shellxquote)
        let l:shxq_sav = ''
        set shellxquote&
      endif
      let cmd = '"' . $VIMRUNTIME . '\diff"'
    else
      let cmd = substitute($VIMRUNTIME, ' ', '" ', '') . '\diff"'
    endif
  else
    let cmd = $VIMRUNTIME . '\diff'
  endif
  let cmd = substitute(cmd, '!', '\!', 'g')
  silent execute '!' . cmd . ' ' . opt . arg1 . ' ' . arg2 . ' > ' . arg3
  if exists('l:shxq_sav')
    let &shellxquote=l:shxq_sav
  endif
endfunction
```

아래 것은 My setting Gvim  더 설정할 것이 있으면 밑에다가 점점 쌓아가면된다. 

```shell
" Vim with all enhancements
source $VIMRUNTIME/vimrc_example.vim

" Use the internal diff if available.
" Otherwise use the special 'diffexpr' for Windows.
if &diffopt !~# 'internal'
  set diffexpr=MyDiff()
endif
function MyDiff()
  let opt = '-a --binary '
  if &diffopt =~ 'icase' | let opt = opt . '-i ' | endif
  if &diffopt =~ 'iwhite' | let opt = opt . '-b ' | endif
  let arg1 = v:fname_in
  if arg1 =~ ' ' | let arg1 = '"' . arg1 . '"' | endif
  let arg1 = substitute(arg1, '!', '\!', 'g')
  let arg2 = v:fname_new
  if arg2 =~ ' ' | let arg2 = '"' . arg2 . '"' | endif
  let arg2 = substitute(arg2, '!', '\!', 'g')
  let arg3 = v:fname_out
  if arg3 =~ ' ' | let arg3 = '"' . arg3 . '"' | endif
  let arg3 = substitute(arg3, '!', '\!', 'g')
  if $VIMRUNTIME =~ ' '
    if &sh =~ '\<cmd'
      if empty(&shellxquote)
        let l:shxq_sav = ''
        set shellxquote&
      endif
      let cmd = '"' . $VIMRUNTIME . '\diff"'
    else
      let cmd = substitute($VIMRUNTIME, ' ', '" ', '') . '\diff"'
    endif
  else
    let cmd = $VIMRUNTIME . '\diff'
  endif
  let cmd = substitute(cmd, '!', '\!', 'g')
  silent execute '!' . cmd . ' ' . opt . arg1 . ' ' . arg2 . ' > ' . arg3
  if exists('l:shxq_sav')
    let &shellxquote=l:shxq_sav
  endif
endfunction

colorscheme desert	       
set guifont=D2Coding:h20   

set number relativenumber

set tabstop=4
set encoding=cp949
set fileencodings=utf-8,cp949
set langmenu=cp949
set hi=50
set si
set visualbell
set nu
set scs
syntax on
filetype on
```

```shell
c:\Program Files\Vim\_vimrc 파일을 열어
아래 설정 구문 중, 원하는 것만 집어넣으면 된다.

syntax on              # 언어에 따른 자동 문법, 구문의 색을 다르게 표시
filetype on            # 파일 종류를 자동으로 인식
colorscheme torte      # 컬러스킴을 변경
set ru                 # 화면 우측 하단에 현재 커서의 위치(줄,칸)를 표시 (ruler)
set sc                 # 완성중인 명령을 표시
set vb                 # 키를 잘못눌렀을 때 삑 소리를 내는 대신 번쩍임 (visualbell)
set hls                # 검색된 스트링의 하이라이트 (hlsearch)
set ci                 # C 형태의 들여쓰기 (cindent)
set ai                 # 자동 들여쓰기 (autoindent)
set si                 # 좀더 똑똑한 들여쓰기 (smartindent)
set sw=4               # 자동들여쓰기를 4칸으로 설정 (shift width)
set ts=4               # TAB 간격을 4칸으로 설정 (tab stop)
set scs                # 똑똑한 대소문자 구별 기능 사용
set hi=50              # 명령어 기록을 남길 개수 지정 (history)
set cul                # 커서가 있는 라인 하이라이트

# GUI Mode 일 때만 수행...
if has("gui_running")
    set lines=56
    set columns=150
    set gfn=GulimChe
endif

set gfn=GulimChe 구문 대신 아래 구문을 써도 된다.
set guifont=돋움체:h9:cHANGEUL

==================
==== 추가 내용 ====
==================

출처 : http://namomo.egloos.com/1660114

""""""""""""""""""""""""""""""""""""""""""""""""
" GUI 설정
""""""""""""""""""""""""""""""""""""""""""""""""
" 폰트 설정. 폰트와 폰트 크기를 지정한다.
if has( "gui_running" )
set gfn=ProFontWindows:h12
" set gfn=gulimche:h12
" set gfn=sans-serif12
" set gfn=Lucida_Console:h12
" set gfn=돋음체12
" set gfn=Terminal12

" 초기 VI 시작시 크기 설정 w * h
au GUIEnter * winsize 90 50

" 초기 VI 시작 위치 설정
au GUIEnter * winpos 550 0
endif

""""""""""""""""""""""""""""""""""""""""""""""""
" VI 기본 설정
""""""""""""""""""""""""""""""""""""""""""""""""
" 자동 들여쓰기를 설정합니다.
set ai

" 경고 소리를 화면 깜빡임으로 대체
set visualbell

" 들여쓰기 폭을 정합니다.
set shiftwidth=2

" 탭의 폭을 정합니다.
set tabstop=2

" 탭을 스페이스로 태체합니다.
set et

" C의 구문에 맞게 들여쓰기 합니다
set cindent

" 라인수를 표시해 줍니다
set nu

" 각 파일에 해당하는 문법(Syntax)를 적용시켜줍니다.
" C나 Java등 사용시 색상등..
syntax on

" 파일 편집시 undo 할수 있는 최대 횟수 설정
set history=100

" 함수 닫기표시
set sm

" 타이핑시 마우스 커서 감추기
set mousehide

" 최소한 2줄 이하로는 자동 스크롤
set scrolloff=2

" 정의되어진 색상을 선택해서 보여줍니다
colors sdh

" ESC키를 누르면 한글 모드가 해제
" 입력모드에서 이전 언어 설정 모드 유지
inoremap <ESC> <ESC>:set imdisable<CR>
nnoremap i :set noimd<CR>i
nnoremap I :set noimd<CR>I
nnoremap a :set noimd<CR>a
nnoremap A :set noimd<CR>A
nnoremap o :set noimd<CR>o
nnoremap O :set noimd<CR>O
```

Vim 배울 때 도움이 되는 사이트 

[Vim 공부](https://opentutorials.org/course/730)

