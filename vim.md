Vim 에디터
==============
## vim의 장점
1. 텍스트 기반으로 동작하기 때문에 가볍고 속도가 빠르다.
2. 키보드만 사용해서 모든 작업을 처리할 수 있다. (기본키를 사용하여 커서 이동을 할 수 있다.)

## vim 의  모드 및 모드 전환
  ![ vim mode](http://blogthumb2.naver.net/20150506_203/nfwscho_1430858095202XwXLw_PNG/%B9%E3%BE%D3%B0%B3_vim_%B8%F0%B5%E5_00.png?type=w2)
* 명령라인 모드(command line),  명령모드(command mode), 편집모드(edit mode), 비주얼 모드(visual mode)
*  처음에는 무조건 **명령모드(command mode)부터 시작**한다.
명령모드에서 편집을 하려면 i (insert) 혹은 a(append)를 눌러서 편집모드로 들어가야 한다.
* **모드의 전환**은 위 그림에서의 단축키들을 통해 가능하다.
ex) 명령모드에서 편집모드로의 변환은 i키를 통해 가능하다.

#### 1. **명령라인 모드(command line)**
명령라인 모드는 **명령 입력으로 여러 일을 수행할 수 있는 모드**이다. vim의 설정을 바꾼다거나, 다른 파일을 열거나, 저장을 하는 등의 명령을 수행 가능하다.
ex) vim을 종료하려면 명령라인 모드에서 q를 입력한다.

#### 2. **명령 모드(command mode)**
명령 모드는 **키 입력을 통해 vim에 명령을 내리는 모드**이다. 커서를 이동하거나, 삭제, 복사, 붙여넣기 등의 작업을 수행한다.

#### 3. **편집 모드(edit mode)**
편집 모드는 **실제로 문서를 편집하기 위한 모드**이다. 입력 모드에서 키보드로 타이핑을 하면 화면에 글자들이 출력되면서 편집되는 것을 볼 수 있다. 일반적인 다른 에디터의 기본 모드와 같다고 볼 수 있다.

#### 4. **비주얼 모드(Visual mode)**
비주얼 모드는 **범위를 지정할 때 범위의 시작과 끝을 명시해줘야 할 때, 마우스로 드래그 해서 범위를 지정하듯 커서 이동을 통해 블록 단위로 범위를 지정할 수 있다.**

--------------------
## vim 설치 및 시작하기
#### vim 설치하기
 vim을 설치하기 위해 터미널에
> sudo apt-get install vim

을 입력한다.(하단 이미지 참고)

![vim install](https://drive.google.com/uc?id=1pTRWSdRitbg79Clrh8v5lB-WRmo5cRcW)

#### vim 시작하기
hello.txt라는 파일을 실행(hello.txt 파일이 존재하지 않는다면 새로 생성)하려면
> vim hello.txt

를 입력한다.(하단 이미지 참고)
![hello.txt](https://drive.google.com/uc?id=1FS__wL_GKTUiNZiiWkqMQBtxg4WVE73Y)

새로 생성하게 되면 하단에 "hello.txt"[새 파일]이라고 표시가 되며, **명령 모드(command mode)로 시작**이 되므로 바로 편집을 할 수는 없다.
![hellotxt_open](https://drive.google.com/uc?id=1Pgvy6dWnD_2GcB0l88anYDf17cufMKNv)
위 이미지는 **'명령 모드(command mode)'**,
편집을 하기 위해서는 **i 키를 통해 편집 모드(edit mode)로 전환**한다.
아래 이미지(예시)는 **'편집 모드(edit mode)'**로 편집이 가능하다.
![hellotxt_editmode_prac](https://drive.google.com/uc?id=14kEAVmm5IaRzX2YS0PhFCcOajOcOsTEZ)
 '명령 모드(command mode)'에서, **: 를 입력하면 '명령라인 모드(command line)'**로 전환된다.
 (:표시가 아래에 생기면서 커서가 제일 아래로 이동한다)
 아래 이미지가 명령라인 모드.
 ![hellotxt_commandline mode](https://drive.google.com/uc?id=1oryifxiSbd9qkJjyN2u_uFQF2ivM0u4e)
  * 어떤 모드라도 esc키로 '명령 모드(commmand mode)'로 전환 가능하다.

## 커서 이동(h,j,k,l) / 글자 추가 및 삭제(i,a,o,x)
#### 커서 이동하기
* vim은 화살표 이동키를 사용하지 않고, h,i,k,l키를 사용하여 커서를 이동시킨다.
  * **h는 왼쪽, j은 아래쪽, k는 위쪽, l은 오른쪽**
  * **vim 명령어는 대소문자를 구분**하므로, caps lock키가 켜진 상태에서는 이동이 되지 않는다.
#### 글자 편집하기
* 글자 편집 관련하여  i, a, o, x 키를 사용한다.
  * **a는 커서의 뒷부분에 글자를 추가(append)할 때, i는 현재 커서가 있는 부분에 글자를 삽입할 때, x는 글자를 지울 때, o는 새로운 줄을 삽입할 때** 사용한다.
* **커서 이동, 글자 추가 및 삭제는 모두 '명령 모드'에서** 이루어진다. 따라서, 가급적 vim에서 입력이 끝났으면 ESC키를 눌러 명령모드로 복귀해 놓는 것이 좋다. 명령 모드에서 다양한 명령키를 가지고 많은 일을 할 수 있기 때문이다.
* 여러가지 글자를 입력하고 지우면서 익숙해 질 때까지 연습해 보는 것이 좋다.

![hellotxt_hjkl](https://drive.google.com/uc?id=1bmLJV97fUeEwvWHoz3wZgv-CJOXP_Ly1)

## 저장하기(:w), 현재 위치(:cd), 파일 읽기(:o)
* 저장하기, 저장된 파일의 현재 위치 알기, 파일 읽기를 하기 위해서는 명령라인모드(command line mode)로 진입해야 한다. (명령모드에서 :을 입력)

![vim저장하기](https://drive.google.com/uc?id=1MhCnFpc1BPacPai6pv8BNZBN3gnaxY1H)
![vim저장오류-이름지정안했을때](https://drive.google.com/uc?id=1PFPDk5oicvS5yfW7bMFv-437NCutzvPW)
 * 먼저 파일을 저장하기 위해서는, 명령라인 모드에서 **:w**을 입력하면 된다. 이 때, 처음에 저장 파일 이름을 입력하지 않았을 경우 에러가 뜬다.

* 파일에 이름을 지정해 저장하려면,  **:w (파일이름)**을 입력하면 된다. (하단 이미지 참고) 또한  명령라인모드에서** :cd를 입력하면 현재 경로를 확인**할 수 있다.
![이름 지정해서 저장하기](https://drive.google.com/uc?id=1obJs91SM2zAGpPtroG8lG_TyX7U-8pGg)
![저장 완료](https://drive.google.com/uc?id=1d8Z3gA63l4-7HrpnRQhJJiZyAAEkvoPv)
> 파일이름을 지정한 후 저장(**:w hellovim.txt**)이 완료되면 위와 같이 저장되었음을 확인할 수 있다.


* 지정된 경로에 있는 파일을 불러오기 위해서는, vim을 열고, 명령라인모드에서  **:o d:(경로)(파일명)**을 입력한다.
![](https://drive.google.com/uc?id=1vjJfsNfa5nQ5LqNwID6Kn4pRozJ5l5cF)

## 종료(:q), 강제종료(:q!), 저장 후 종료하기(:wq)
* 명령라인 모드에서 종료, 강제종료, 저장 후 종료를 실행할 수 있다. 먼저 종료할 때는 **:q**를 입력한다.
![](https://drive.google.com/uc?id=119yfEWqnFCRPsDUIOMFE7UGFSdzR0tfR)
> 저장하지 않고 끝내려 했을 때 오류가 발생하기도 하는데 이 때는 **:q!**을 입력해 종료할 수 있다. (뒤에 !을 붙이는 것은 강제로 수행한다는 의미 )
* 저장 후 종료는, **:wq**으로 가능하다.
![](https://drive.google.com/uc?id=1Xv1Upx2FMMAX64iMc7TrtdwWPNmhwAtI)
> 현재 사용하는 파일명이 없으면 오류가 발생하기도 한다. 이 때는 경로 지정과 함께 파일명을 지정하면서 저장 후 종료를 하면 저장이 가능하다. (ex-  :wq d:\home\hs\hello.txt)
--------------------------

## 한줄복사(yy), 붙여넣기(p), 반복작업
* y는 yank의 약자로, vim에서는 copy라는 말 대신 사용한다. yank는 붙잡아 둔다는 뜻으로, yy를 하면 한줄을 붙잡아 두는 명령이다.
* (**명령 모드에서** - 명령라인 모드가 아니다!)** y명령키를 2번 누르면, 해당 커서가 있는 한 줄이 복사**된다. 화면에서는 yy가 입력되지는 않는다.
![](https://drive.google.com/uc?id=1aWzNiLZgcnOfXsBswp4OBd2BZ4-EYpll)
* 이 상태에서, p를 입력하면 복사된 한 줄이 붙여넣기된다. (p는 put의 약자이다)
![](https://drive.google.com/uc?id=1MCmc4xurRbjR0-LuTPRUCIW5Ekps3VCH)
* 이 때, **한번에 여러번 붙여넣기를 하고 싶다면 앞에 숫자를 붙여 p를 입력**하면 된다. 예를 들어 7p를 입력한 경우, 아래와 같이 해당 상태에서, 7줄이 붙여넣기 된다.  ![](https://drive.google.com/uc?id=1xnnIH7pYn0QjzkRyKs39FPLGcHD51_a6)

## 취소(u), 다시실행(ctrl+r)
* 취소(undo), 다시실행(redo)의 기능은 기타 다른 편집기의 ctrl+z, ctrl+shift+z와 같은 기능이다. 주로 vim에서는 undo 가 자주 사용된다. 명령어를 잘못 입력했을 경우, u를 눌러 undo할 수 있다.
* **명령 모드**에서, **u를 누르면 취소, ctrl+r은 다시실행**이다.

## 찾기, 역방향찾기, 다음찾기, 이전찾기
* vim에서 명령라인모드(command-line mode)로 진입하려면, :를 입력하는 것 말고도 /, ?, ! 의 방법들이 있다. 이 중 / ?는 search command 라고 한다. (!는 추후에 배운다.)
* **/ 명령어는 '정방향 찾기'** 로서 /기호는 향후 리눅스 및 정규표현식 등에서 search로 사용될 때 많이 쓰는 기호이다.
  * 입력하고자 하는 텍스트를 입력한 후, esc키를 눌러 명령모드로 빠져나온 후 **/(찾고자 하는 단어)**를 입력하고 엔터를 누른다.
  ![](https://drive.google.com/uc?id=128m2aPMwsH40kKxGChgcnwitvAUHC4nC)
  ![](https://drive.google.com/uc?id=1DHUb1JdEIgyerB_conqV1jcRF4vMznWH)


* **?는 역방향 찾기**의 기능이다.(자주 사용되지는 않는다.)
  * 마찬가지로, 명령 모드에서 **?(찾을 단어)**를 입력하고 엔터를 누른다.
   ![](https://drive.google.com/uc?id=1iCcyjEasJm9R-dd-HIrf2I_9uZAYTcYN)
   ![](https://drive.google.com/uc?id=1SRLyAUKw-oPAbbXK8--ZhjOLO14pCmpg)


* **순방향 찾기와, 역방향 찾기 모두에서 n을 누르면 다음 찾기 명령**이다.
순방향 찾기에서 n을 한 번 누르면, 첫번째 찾은 단어로부터 바로 다음 찾기이므로 두 번 째 단어를 찾게 된다.
![](https://drive.google.com/uc?id=1B6GXUhZ-Acc_p6xrS3lpVqTzDnONyeVo)

## 커서이동 첫글자, 끝글자, 단어이동, 앞단어이동
* 명령 모드에서, **$를 누르면 커서가 현재 위치한 라인의 제일 뒤로 이동**한다.
* **^를 누르면 커서가 현재 위치한 라인의 제일 앞으로 이동**한다.
* **w을 누르면 다음 단어의 제일 앞글자로,
b를 누르면 이전 단어의 제일 앞글자로,
e는 다음 단어의 끝으로 이동**한다.
  * 이 때 대문자 W, B, E는 ,  - 등의 기호를 한 단어로 취급하지 않고, 소문자는 기호 역시 한 단어로 취급한다.
* 명령어 정리
![](https://mblogthumb-phinf.pstatic.net/20150506_19/nfwscho_1430849486574uECfF_PNG/%BE%D3%B0%B3_vim_%C4%BF%BC%AD%C0%CC%B5%BF_00_0.png?type=w420)

## 커서이동 반화면 아래, 반화면 위로, 문서처음, 문서마지막 이동, 특정 줄 이동
* 반화면 아래로 이동하는 명령어는  CTRL + D, 반화면 위로 이동하는 명령어는  CTRL+U 이다. (한화면 아래, 위로 이동하는 키는 CTRL+B, CTRL+F이다.)
  *  CTRL+D를 하면 반화면 아래로 이동한다. (순서대로 전,후 캡처)
  ![](https://drive.google.com/uc?id=1zffKb-aPWirOg8qPqwy_X8_Qjpi_cY2d)  
    ![](https://drive.google.com/uc?id=1-5mGwQOpig-UsKdZ-cPwGe1X4snljnOS)

  *   CTRL+U를 하면 반화면 위로 이동한다. (순서대로 전,후 캡처)
   ![](https://drive.google.com/uc?id=1VdDc23Fhp15Ii_Q_KnMdUo5EhqumbwA-)
   ![](https://drive.google.com/uc?id=1-5mGwQOpig-UsKdZ-cPwGe1X4snljnOS)


* 문서 맨 처음으로 이동하는 명령어는 gg, 문서의 제일 끝으로 이동하는 명령어는 G이다. (순서대로 gg, G)

![](https://drive.google.com/uc?id=1WHRc_f9xwZ33T_BeriuyLLtkwhHNNYfU)

![](https://drive.google.com/uc?id=1cLQr958D3EqRHFm5Oy-43vbWAr6VY8cA)

* 명령어 정리

![](https://mblogthumb-phinf.pstatic.net/20150506_273/nfwscho_1430852614992MURHx_PNG/%B9%E3%BE%D3%B0%B3_vim_%C8%AD%B8%E9%C0%CC%B5%BF_00.png?type=w420)


## 삭제, 줄삭제, 단어삭제, 커서앞줄삭제, 커서뒷줄삭제, 선택삭제
* :help d 를 하면 많은 도움말을 볼 수 있다.
* d는 키 하나만 누르는 것으로 명령이 완성되는 것이 아니다. d 이후에 이동키를 눌러주면 커서부터 이동키까지 간 곳 까지 지워주는 것이다. (x로는 한 글자를 지우는 것이라면, d는 대량으로 삭제할 때 혹은 찾아서 삭제할 때 사용한다.)
* 잘못 삭제했을 경우 u로 복구할 수 있다.

* 기본적으로 삭제 명령어는 d이고, 이후 방향키(h,j,k,l)을 통해 방향을 지정해 주면 해당 방향의 한 글자를 삭제한다.
*  dd는 한줄 삭제 명령으로, 커서가 있는 줄을 삭제한다. (차례로 한줄 삭제 전, 후)
![](https://drive.google.com/uc?id=1ae5APNv3tGQ8e8ly4mqSEi6SWBOT0oZL)
![](https://drive.google.com/uc?id=11z9wfFjiOunT48ir1NYgbXP8sMJMPFmQ)
* dw는 커서로부터 한 단어를 지우는 키이다. (차례로 삭제 전, 후) - 이 때, dw는 단어 뒤의 공백을 포함하여 지운다.
![](https://drive.google.com/uc?id=1ME9tNo1C2M111tbBVsBWsiv5JMc3Gn5P)
![](https://drive.google.com/uc?id=1-DF-3g9Bj3F6Ksd4vEj5D2gbjfdaD3k-)
* de는 커서로부터 한 단어를 지우는데, 단어 뒤의 공백을 포함하지 않는다. (차례로 삭제 전, 후)
![](https://drive.google.com/uc?id=1MhYVu45m2SIxwz_kRpeXOrlT8I1CFTX9)
![](https://drive.google.com/uc?id=1YAFOHsYQFIxHPhbeulJrd8WPQYHaX6DA)
* 이 외에도 응용을 통해, bde는 b(단어앞이동), de(단어 끝까지 삭제)하여 커서가 단어의 중간에 있을 때 한 단어를 삭제 가능하다.
* 응용을 통해, ^는 현재 줄의 맨 앞으로 이동하는 명령이므로, d^을 하면 해당 줄의 맨 앞부분까지 지울 수 있다. (마찬가지로, d$를 누르면 줄의 뒷부분을 지울 수 있다.)
* 그 외의 삭제 명령어는 매우 다양하므로, :help d를 하여 도움말을 볼 수 있다.

## 비주얼 모드
* 일반 비주얼: v  비주얼 라인: V   비주얼 블럭: ctrl-v or ctrl-q
* 비주얼 모드로 진입해서 h, j, k, l (좌, 하, 상, 우) 이동 키로 범위를 선택할 수 있다.
* 이런 식으로해서 복사 가능!

## vim 에디터 커스터 마이징
* .vimrc파일을 수정해서 vim 에디터의 설정을 바꿀 수 있다

* 첫째로 자신의 홈 디렉토리 최상위에 .vimrc 파일을 작성한다
> $ vi ~/.vimrc

* Syntax HIghlighting
~~~
if has(“syntax”)
   syntax on
endif
~~~
* 자동 인덴트 설정
~~~
set autoindent
set cindent
~~~
* 줄번호 표시
~~~
set nu
~~~
