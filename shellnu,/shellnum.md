# 쉴 연산자

## 종류

- 산술 연산자
- 관계 연산자
- Boolean 연산자
- 문자열 연산자
- 파일 테스트 연산자

## bash에서 진행하는 간단한 숫자 계산

### bash 변수 처리

```
x=3
y=4
z=$((x+y))
echo $z
# 7
```
```
echo $((x-y))
echo $((x*y))
echo $((x/y))
# -1
# 12
# 0
echo $((12/5))
# 2
```

### let 명령어
```
x=3
y=4
let z=$x+$y
echo $z
# 7
```
```
let z=$x-$y
echo $z
# -1
```
```
let z=$x*$y
echo $z
# 1
```

### expr 명령어

- 숫자와 연산자 사이를 반드시 띄어써야 한다. 예를 들어 2+2 형식으로 하면 동작하지 않으며 2 + 2 형식으로 작성해야 한다. 또한 쉘 스크립트 내에서 연산을 적용하기 위해서는 `` backtick을 추가해야 한다.
```
#!/bin/sh

val=`expr 2 + 2`
echo "Total value : $val"
```
```
x=3
y=4
expr $x + $y
# 7

```
```
expr $x - $y
expr $x \* $y
expr $x / $y
# -1
# 12
# 0
expr 12 / 5
# 2
```
### awk 명령어
```x=3
y=4
echo $x $y | awk '{print $1+$2}'
# 7
echo $x $y | awk '{print $1-$2}'
# -1
echo $x $y | awk '{print $1*$2}'
# 12
echo $x $y | awk '{print $1/$2}'
# 0.75
```
### bc 명령어

- basic calculator의 약자로 리눅스 bc가 설치되어야 한다. 인터랙티브 모드와 배치 모드 둘다 사용이 가능하고, 실수, 사칙연산, 거듭제곱 등의 연산과 같은 고급 기능이 있으며 가볍다는 특징이 있다.
```
$ bc --version
bc 1.07.1
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006, 2008, 2012-2017 Free Software Foundation, Inc.
```
```
$ echo '12+34' | bc
46
$ echo '12-34' | bc
-22
$ echo '12*34' | bc
408
```
```
$ echo '12/34' | bc
0
$ echo 'scale=2;12/34' | bc
.35
$ echo '43/21' | bc
2
$ echo 'scale=5;43/21' | bc
2.04761
```
```
$ echo '4^4^4' | bc
13407807929942597099574024998205846127479365820592393377723561443721\
76403007354697680187429816690342769003185818648605085375388281194656\
9946433649006084096
```

## 정리


|Operator|	Description	|Example|
|------------|-------|--------------|
|+ (Addition)|	덧셈	|expr $a + $b|
|- (Subtraction)|	뺄셈|	expr $a - $b|
|- (Subtraction)	|곱셈	|expr $a \* $b|
|/ (Division)	|나누기|	expr $b / $a|
|% (Modulus)	|나머지 반환	|expr $b % $a|
|= (Assignment)|	값 할당|	a = $b|
|== (Equality)	|비교|	[ $a == $b ]|
|!= (Not Equality)	|비교|	[ $a != $b ]|

