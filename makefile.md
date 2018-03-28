# make 유틸리티
## 1. make 유틸리티란?
일반적으로 애플리케이션 제작은 프로젝트 기반으로 진행되는데 하나의 프로젝트에는 아주 많은 수의 소스 코드가 사용된다. 이러한 소스 코드를 gcc를 이용해서 하나하나 컴파일하기에는 너무 많은 작업과 시간이 소요된다. 번거롭고 복잡한 소스 코드의 빌드 작업을 자동화하는 도구가 바로 make 유틸리티이다.
makefile에 의존 규칙(dependency rule)들을 표시하고, 이를 기준으로 소스 코드 자동 빌드할 수 있다.
## 2. 사용
- make 유틸리티를 사용하기 위해서는 makefile이 필요
- '$ make'를 입력하면 자동으로 빌드가 실행
- 이름을 별도 지정하고 싶으면 '--makefile' 또는 '-f'옵션 사용

```$ make [--makefile=파일명]```

## 3. 생성
makefile은 목표(target), 의존관계(dependency), 명령(command) 크게 세 부분으로 나눌 수 있다.

```
targetList: dependencyList
            commandList
```

| 요소 | 내용 |
| :--- | :--- |
| 목표(target list) | 명령(command list)이 수행되어 생성될 결과 파일(목적파일 or 실행파일)을 지정 |
| 의존관계(dependency list) | 목표를 수행하기 위해 필요한 의존 관계를 설정 |
| 명령(command list) | 의존관계(dependency list)에 정의된 파일의 내용이 바뀌었거나, 목표(target list)에 해당하는 파일이 없을 때 여기에 정의된 내용이 차례대로 실행 |

## 4. 기본 접근
main.c print.c input.c 세 파일을 빌드해보자
```$ gcc -o test main.c print.c input.c```
위의 방식은 makefile 없이 단순히 명령어를 주어 실행파일을 생성하는 방식이다.

아래의 두 makefile은 똑같은 일을 수행하는 내용이다.
**makefile 파일**
```
test :
    gcc -o test main.c print.c input.c
```
make 실행결과
```
$ make
gcc -o test main.c print.c input.c
```
---
**makefile 파일**
```
test : main.o print.o input.o
    gcc -o test main.o print.o input.o

main.o : main.c
    gcc -c main.c

print.o : print.c
    gcc -c print.c

input.o : input.c
    gcc -c input.c
```
make 실행결과
```
$ make
gcc -c main.c
gcc -c print.c
gcc -c input.c
gcc -o test main.o print.o input.o
```
각각의 c 소스 코드들 설정하고 gcc -c 옵션을 이용해 컴파일 한 후, 다시 하나로 링크해서 실행파일 test 생성


## 5. 매크로
반복작업을 매크로를 이용해 처리해보자.
형태 : '${매크로}', **'$(매크로)'**, '$매크로'

- '$(매크로)' - 가장 일반적
- 대문자 사용
- '='을 이용해 값 설정

**makefile 파일**
```
OBJECTS = main.o print.o input.o
test : $(OBJECTS)
    gcc -o test $(OBJECTS)

main.o : main.c
    gcc -c main.c

print.o : print.c
    gcc -c print.c

input.o : input.c
    gcc -c input.c
```
OBJECTS - object파일 지정

**makefile 파일**
```
OBJECTS = main.o print.o input.o
SRCS = main.c print.c input.c

CFLAGS = -g
TARGET = test

$(TARGET) : $(OBJECTS)
    $(CC) -o $(TARGET) $(OBJECTS)

test : $(OBJECTS)
    gcc -o test $(OBJECTS)

main.o : main.c
print.o : print.c
input.o : input.c
```

SRCS - 소스파일 지정
CFLAGS - 컴파일 시 플래그 지정 (CFLAGS는 C컴파일러의 플래그)
TARGET - 타겟 지정
