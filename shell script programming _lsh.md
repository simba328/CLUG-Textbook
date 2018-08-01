## 제어문

### 조건문

#### if-else 구문

* 기본 문법 형식  
```bash
if [ 조건1 ]
then
    조건1 만족시
elif [ 조건2 ]
then
    조건2 만족시
else
    모든 조건 불만족시
fi
```

* **문자열 체크**
> [ stringName ] - 문자열이 널(Null) 인지 체크, Null이 아니면 참
> [ -n stringName ] - 문자열의 사이즈가 0 이상인지 체크, 0 이상이면 참
> [ -z stringName ] - 문자열의 사이즈가 0인지 체크, 0이면 참
> [ stringNameA = stringNameB ] - A 문자열과 B 문자열이 같은지 체크, 같으면 참
> [ stringNameA != stringNameB ] - A 문자열과 B 문자열이 다른지 체크, 다르면 참

* **숫자 대소 관계 체크**
>[ intA -ge 100 ] - 숫자 A가 100보다 크거나 같은지 체크, 100 이상이면 참
> [ intA -gt 100 ] - 숫자 A가 100보다 큰지 체크, 100이 넘으면 참
> [ intA -le 100 ] - 숫자 A가 100보다 작거나 같은지 체크, 100 이하이면 참
> [ intA -lt 100 ] - 숫자 A가 100보다 작은지 체크, 100 미만이면 참

* **파일체크**
>[ -r filename ] - 해당 파일이 읽기 가능한지 체크
> [ -w filename ] - 해당 파일이 쓰기 가능한지 체크
> [ -x filename ] - 해당 파일이 실행 가능한지 체크
> [ -s filename ] - 해당 파일의 사이즈가 제로 이상인지 체크
> [ -d filename ] - 해당 파일이 디렉토리 파일인지 체크
> [ -f filename ] - 해당 파일이 보통 파일인지 체크
> [ -h filename ] - 해당 파일이 링크 파일인지 체크

* **조건문의 결합**
>[ 조건문A -a 조건문B ] - 조건문 A와 조건문 B가 모두 참인지 체크, -a는 AND와 동일
> [ 조건문A -o 조건문B ] - 조건문 A와 B 중 참이 하나라도 있는지 체크, OR과 동일

#### case문
```bash
case $변수 in
선택지1)
    command1 ;;
선택지2)
    command2 ;;
선택지3)
    command3 ;;
*)
    Default command ;;
esac
```

**tip!**
>'||'연산자와 '&&' 연산자를 이용하여 조건에 따른 실행 명령문을 만들 수도 있다.
>'||' : 앞의 명령어가 실패했을 때만 뒤의 명령어가 실행
>'&&' : 앞의 명령어가 성공했을 때만 뒤의 명령어가 실행
>
>ex) 명령어 실행이 실패했을 때 로그를 남기는 작업
>```bash
>command1 || echo 첫번째 명령어 실행 실패 >> log.txt
>command2 || echo 두번째 명령어 실행 실패 >> log.txt
>```


## 반복문
#### while문
```bash
while [ 조건 ]
do
    명령어 구문
done
```

#### until문
: 조건이 거짓인 동안 반복
```bash
until [ 조건 ]
do
    명령어 구문
done
```

#### for문
```bash
for 변수명 in value1 value2 ...
do
    명령어 구문
done
```

### 함수

함수를 사용하려면 정의된 함수의 이름만 호출하면 된다.
인자를 넘기고 싶으면? 함수 이름 옆에 넘길 인자들 나열해주면 된다.
함수내부에서 인자를 사용하는 법은 쉘 프로그램을 호출하면서 인자를 넘겨받았을 때 사용하는 법과 동일하다.
```bash
func1()
{
    #statements
}
funct2()
{
    arg1=$1
    arg2=$2
}
func1
func2 Hello World
```
