# make 유틸리티

## 1. make 유틸리티란?
일반적으로 애플리케이션 제작은 프로젝트 기반으로 진행되는데 하나의 프로젝트에는 아주 많은 수의 소스 코드가 사용되고 소스 코드들은 서로 관계를 가지고 있다. 이러한 소스 코드를 하나하나 컴파일하기에는 너무 많은 작업과 시간이 소요되고, 한 파일만 수정했다 하더라도 해당 파일과 연관된 다른 파일들도 모두 새롭게 컴파일되어야 한다. 이러한 번거롭고 복잡한 소스 코드의 빌드 작업을 자동화하는 도구가 바로 make 유틸리티이다.
makefile에 의존 규칙(dependency rule)들을 표시하고, 이를 기준으로 소스 코드 자동 빌드할 수 있다.

**기능:** 프로그램을 컴파일 할 때  새롭게 컴파일되어야 하는 부분을 자동으로 판단해서 그들을 재 컴파일 시킨다.

## 2. 사용
- make 유틸리티를 사용하기 위해서는 makefile이 필요
- '$ make'를 입력하면 자동으로 빌드가 실행
- 이름을 별도 지정하고 싶으면 '--makefile' 또는 '-f'옵션 사용

```bash
$ make [--makefile=파일명]
```

## 3. 생성
makefile은 목표(target), 의존관계(dependency), 명령(command) 크게 세 부분으로 나눌 수 있다.

```
targetList: dependencyList
            commandList
```

| 요소 | 내용 |
| :--- | :--- |
| 목표(target) | 명령(command)이 수행되어 생성될 결과 파일(목적파일 or 실행파일)을 지정. 혹은 clean 등의 간단한 레이블 기능을 제공 |
| 의존관계(dependency) | 목표를 수행하기 위해 필요한 의존 관계를 설정 |
| 명령(command) | 의존관계(dependency)에 정의된 파일의 내용이 바뀌었거나, 목표(target)에 해당하는 파일이 없을 때 여기에 정의된 내용이 차례대로 실행. 쉘에서 쓸 수 있는 모든 명령어 사용 가능. |

**주의:** 명령 부분은 꼭 TAB글자로 시작해야한다. 아니면 에러남!

## 4. 기본 접근
예제환경: main.c print.c input.c 구성. 모두 io.h 헤더파일 사용

make를 사용하지 않고 터미널에서 이 프로그램을 빌드하여 실행파일을 생성시키려면 다음과 같은 과정을 거쳐야한다.
```bash
$ gcc -c main.c
$ gcc -c print.c
$ gcc -c input.c
$ gcc -o test main.o print.o input.o

```
※ gcc 사용방법은 [03_GCC](https://github.com/simba328/CLUG-Textbook/blob/master/03_GCC.md)에서 참고하자.

아래의 두 문서는 똑같은 일을 수행하는  makefile이다.

**makefile 파일_1**
```
test :
        gcc -o test main.c print.c input.c
```
make 실행결과
```bash
$ make
gcc -o test main.c print.c input.c
```
---
**makefile 파일_2**
```
test : main.o print.o input.o
        gcc -o test main.o print.o input.o

main.o : io.h main.c
        gcc -c main.c

print.o : io.h print.c
        gcc -c print.c

input.o : io.h input.c
        gcc -c input.c
```
make 실행결과
```bash
$ make
gcc -c main.c
gcc -c print.c
gcc -c input.c
gcc -o test main.o print.o input.o
```

* 프로젝트 일부를 수정하고 make할 때 빌드 흐름

ex1) main.c 변경: main.c 재컴파일 -> main.o파일 갱신 -> test 갱신

ex2) io.h 변경: 모든 c파일 재컴파일 -> 모든 오브젝트파일 갱신 -> test 갱신


## 5. 매크로
반복작업을 매크로를 이용해 처리해보자.
형태 : '${매크로}', **'$(매크로)'**, '$매크로'

- '$(매크로)' - 가장 일반적
- 대문자 사용
- '='을 이용해 값 설정

오브젝트 파일들을 매크로로 치환해보자.

**makefile 파일_3**  
> *OBJECTS - object파일 지정*  

```
OBJECTS = main.o print.o input.o
test : $(OBJECTS)
    gcc -o test $(OBJECTS)
        .........
```

```
매크로 X
test : main.o print.o input.o
        gcc -o test main.o print.o input.o
        .........
```


위에서 다뤘던 makefile_2를 다양한 매크로로 치환해보자.
**makefile 파일_4**  
> *OBJECTS - object파일 지정*  
> *SRCS - 소스파일 지정*  
> *CFLAGS - 컴파일 시 플래그 지정 (CFLAGS는 C컴파일러의 플래그)*  
> *TARGET - 타겟 지정*  

```
OBJECTS = main.o print.o input.o
SRCS = main.c print.c input.c

CFLAGS = -g
TARGET = test

$(TARGET) : $(OBJECTS)
    $(CC) -o $(TARGET) $(OBJECTS)

main.o : main.c
print.o : print.c
input.o : input.c
```

## 6. 레이블
목표(target)부분에 목적파일이나 실행파일을 명시하는 것 말고 레이블이라는 것을 사용할 수도 있다.

```
clean :
        rm $(OBJECTS)
```
make clean 실행결과
```bash
$ make clean
rm main.o print.o input.o
```
