# makefile_(2)

### 내부 매크로(Internal macro)
내부 매크로란 사용자가 마음대로 정할 수 없고, 매크로를 내부적으로 연산 및 처리하는데 사용되는 매크로이다.
~~~c
$*      : 현재의 목표 파일(target)에서 확장자를 없앤 것
$@      : 현재의 목표 파일 (target)
$<, $?  : 현재의 목표 파일(target)보다 더 최근에 갱신된 파일이름
~~~

###### 예시
~~~c
main.o : main.c io.h
  gcc -c $*.c   //여기서 $*.c는 main에 해당한다
~~~
~~~c
test : $(OBJS)
  gcc -o $@ $*.c  //여기서 $@는 test에 해당, $*.c는 test.c에 해당
~~~
~~~c
.c.o :
  gcc -c $<   //$<는 현재의 목표 파일보다 더 최근에 갱신된 이름이므로 ,
              //.c나 .o 보다 더 최근에 갱신된 .o .c 파일은 자동적으로 컴파일이 된다.
              //즉  main.o를 만든 후 main.c를 수정하고 저장하면, $<에 의해 자동적으로 새롭게 컴파일.
~~~

* 참고로, makefile 작성 후 명령어 make를 치면, makefile의 내용 중 가장 첫 번째로 나오는 목표 파일에 해당하는 것을 실행하게 된다. Ex> clean에 관한 라벨을 가장 먼저 작성 시 make 하면 make clean이 된다.
* 강제로 특정 목표 파일을 실행하기 위해서는 make [target명]으로 명령해 주어야 한다.

## Makefile 작성 시 tip
### 긴 명령어를 여러 라인으로 표시 (  ' \   '을 이용)
###### 예시
 ~~~c
OBJECTS = input.o \
output.o \
main.o
 ~~~

### 매크로 치환
 이미 지정한 매크로의 값의 일부(또는 전체)를 바꾸어야 할 때는 $(매크로 이름: 고칠 글자 = 바꿔 지정할 글자)의 형식을 이용한다.
 ###### 예시
 ~~~c
OBJECTS = main.o input.o print.o
SRCS = $(OBJECTS: .o = .c)      //즉 SRCS = main.c input.c print.c 로 바뀐다.
 ~~~

### gccmakedep (dependency 자동 생성)

일반적인 make의 구조는 target, dependency, command로 이루어져 있으며 형태는 아래와 같다.
```
target : dependency
    command
```
이 때 target이 어느 파일에 의존하고 있는지 알려주는 부분이 dependency인데, dependency 설정을 자동으로 해 주는 유틸리티가 gccmakedep이다. gccmakedep은 어떤 파일의 의존 관계를 조사 후 Makefile의 뒷부분에 자동으로 붙여준다.

```
gccmakedep main.c input.c print.c

```
라고 터미널에 명령어를 입력한 후 다시 makefile에 들어가보면, 가장 아래 부분에 의존관계가 형성되었음을 알 수 있다.

### Multiple target(다중 타겟)
몇몇의 파일들을 각각 묶어, 여러 개의 실행파일을 만들고 싶을 때 이를 하나의 Makefile에서 할 수 있는 방법이 다중 타겟을 지정하는 방법이다.

### Recursive make(순환 make)
실행 파일을 만들고자 하는 소스코드들이 같은 한 디렉토리에 존재할 경우, 그들을 다중 타겟으로 지정하여 한 번의 make로 여러 개의 실행파일을 만들 수 있다. 하지만 규모가 큰 프로그램의 경우 파일들이 각각 다른 디렉토리에 정리되어 있을 수 있다. 이 경우, 각각의 하위 디렉토리에 각각의 Makefile이 존재한다고 할 때 서브디렉토리의 Makefile들을 상위 디렉토리에서, make를 통해 실행시킬 수 있다.

### 불필요한 재컴파일 방지
파일 하나가 바뀌었을 때, 아무 영향을 주지도 받지도 않는 파일들까지 재컴파일하는 것은 시간 낭비이다. 따라서 make -t 옵션을 이용하면(t는 touch를 의미하는 옵션으로, 새로 컴파일 된 것처럼 컴파일을 하지는 않고 생성 날짜만 가장 최근으로 바꾸어 준다) 불필요한 재컴파일을 막을 수 있다.

### makefile 작성 순서
1. 매크로 정의
2. 명령어 부분
3. 의존관계 생성
