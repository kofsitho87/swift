# Study Swift Class


1. 변수
2. 자료형
3. 연산자
4. 흐름제어구문(반복문, if else, guard, switch)
5. 집단자료형(배열, 집합, 튜플, 딕셔너리)
6. 옵셔널
7. 함수
8. 클래스


# 1. 변수와 상수
> 변수: var
상수: let


```swift
var a = 1
var b = "B"
var c = 5 + 6
c = c + a


let d = 100
d = 200 (x)
```

아예 생성자를 이용해 초기화 시키는 것도 가능하다.
```swift
var a = Int(1)
var b = String("B")
```

>선언과 초기화
변수는 선언과 초기화를 분리해서 사용할 수 있지만 상수는 안된다.
상수는 선언과 초기화를 동시에 해야한다.

생성 시 타입을 별도로 결정 해 줄 수도 있다.
```swift
var a: Int
a = 1

var b: String
b = "string"


let c: String = "hello"
```


> 타입이 다른 변수끼리의 결합

```swift
var study = "스위프트 스터디"
var time = 1
var studyTime = study + String(time)
```


> 변수와 상수이름 정의하기
> 연산자와 혼동할 수 있는 +, -, *, / 및 공백은 사용할수 없다!
> _(언더바는 사용가능)

```swift
var abc+t = "abc plus t" //(x)
var abc-t = "abc minus t" //(x)
var abc t = "abc space t" //(x)

var abc_t = "abc space t" //(o)
```

> 스위프트 예약어나 키워드로 등록되어 있는 단어는 사용할 수 없다!

```swift
var Class = 1 //(o)
var class = 1 //(x)

var Enum = 2 //(o)
var enum = 2 //(x)

var Struct = 3 //(o)
var struct = 3 //(x)


var Extension = 4 //(o)
var extension = 4 //(x)

var Protocol = 5 //(o)
var protocol = 5 //(x)

var As = 6 //(o)
var as = 6 //(x)
```

> 첫번째 자리에 숫자가 올 수 없다!

```swift
var 1abc = 123 //(x)
```



# 2. 자료형

## Int
Integer. 부호 있는 정수값 (127 ~ -128 까지 저장이 가능하다.)

자료형	저장할 수 있는 값 범위	크기
Int8	127 ~ -128	8bit
Int16	32767 ~ -32768	16bit
Int32	2147483647 ~ -2147483648	32bit
Int64	9223372036854775807 ~ -9223372036854775808	64bit


## UInt
Integer와 유사하지만 부호가 없는 정수. (0 ~ 255)

음수의 범위를 양수가 가져간다고 보면 되겠다.


## Double, Float

실수 범위이다. Float는 32bit, Double은 그 두 배인 64bit까지 표현 가능하다.


##Bool

true/false의 값을 가질 수 있는 자료형이다.


##String

아마 모든 언어에서 제일 많이 쓰는 자료형일 것이다.(C 제외)


##Character

한 개 문자를 저장하는 자료형이다. 앞서 언급했듯이 큰따옴표(“ “)를 사용한다.
