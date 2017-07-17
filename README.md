# Study Swift Class


1. 변수
2. 자료형
3. 연산자
4. 흐름제어구문(반복문, if else, guard, switch)
5. 집단자료형(배열, 집합, 튜플, 딕셔너리)
6. 옵셔널
7. enum
8. 함수
9. 클래스와 구조체
10. 프로토콜


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


## Bool

true/false의 값을 가질 수 있는 자료형이다.


## String

아마 모든 언어에서 제일 많이 쓰는 자료형일 것이다.(C 제외)


## Character

한 개 문자를 저장하는 자료형이다. 앞서 언급했듯이 큰따옴표(“ “)를 사용한다.


# 3. 연산자

## 비교 연산자
> 같음 (a == b)
같지 않음 (a != b)
b 보다 크다 (a > b)
b 보다 작다 (a < b)
b 보다 크거나 작다 (a >= b)
b 보다 작거나 같다 (a <= b)


## 삼항 조건 연산자

```swift
let a = 1
let isAequal1: String = a == 1 ? "1입니다." : "1이 아닙니다."
```


## Nil 결합 연산자

```swift
let defaultColorName = "red"
var userDefinedColorName: String? // defaults to nil
var colorNameToUse = userDefinedColorName ?? defaultColorName
```


## 범위 연산자

### 폐쇄된 범위 연산자
> 폐쇄된 범위 연산자(closed range operator)(a...b)는 a에서 b까지의 범위를 정의하고, a와 b를 포함한다.
a의 값은 반드시 b보다 크기 않다.

```swift
for index in 1...5 {
    print("\(index) times 5 is \(index * 5)")
}
```


### 반 개방 범위 연산자
> 반-개방 범위 연산자(half-open range operator)(a..<b)는 a에서 b까지의 범위를 정의하지만 b를 포함하지 않습니다.
반-개방(half-open)은 첫번째 값은 포함하지만, 마지막 값은 포함하지 않습니다.
폐쇄 범위 연산자처럼 a의 값이 반드시 b보다 크지 않습니다. a가 b의 값이 같으면, 결과 범위는 비어있을 것입니다.

```swift
let names = ["Anna", "Alex", "Brian", "Jack"]
let count = names.count
for i in 0..<count {
    print("Person \(i + 1) is called \(names[i])")
}
```


## 논리 연산자

> 논리 연산자(Logical operator)는 Boolean 논리 값 true와 false를 수정하거나 결합합니다. Swift는 C기반 언어에서 3개의 표준 논리 연산자들을 지원합니다.

1. NOT 논리 연산자 (!a)
2. AND 논리 연산자 (a && b)
3. OR 논리 연산자 (a || b)



# 4. 흐름제어구문(반복문, if else, guard, switch)

## for 문
```swift
for i in 0...10 {
  print(i)
}
0부터 10까지 출력

for i in 0..<10 {
  print(i)
}
0부터 10미만까지 출력

for _ in 0..<10 {
  print("Hello!")
}
상수를 사용하지 않고 단순반복할시
```

## while 문

while은 조건문의 값이 true일 때 계속 반복

```swift
var i = 1024
while i < 1000 {
  i += 1
}
print(i) //1024
```


```swift
var i = 1024
repeat {
  i = i * 2
}
while i < 1000

print(i) //2048
```
repeat~while 구문은 이미 실행블록이 한번 수행된 상태에서 조건식을 평가한다.
repeat~while 구문은 받나드시 한 번은 실행할 필요가 있는 조건에 사용된다.


## switch

```swift
var age = 19
var student = ""
switch age {
case 8..<14:
  student = "초등학생"
case 14..<17:
  student = "중학생"
case 17..<20:
  student = "고등학생"
default:
  student = "기타"
}
```
범위연산자 사용가능
break를 쓰지않음
default는 항상 써야함


## guard

```swift
var age = 10

if age > 19 {
    print("성인입니다.")
}else{
    print("성인이 아닙니다.")
}

guard age > 19 else{
    print("성인이 아닙니다.")
    return
}

print("성인입니다.")
```
guard 문에서 else 안에 꼭 return 을 시켜서 코드가 실행되지 않도록 주의한다.


```swift
var myVar = 10

func checkNumGuard(X:Int?) {
    guard let X = X where X != 10 else {
        print("Error: X is 10!")
        return
    }
    print ("all this code will be executed when X is not 10")
}
checkNumGuard(myVar)
```

# 5. 집단자료형(배열, 집합, 튜플, 딕셔너리)

## 배열

```swift
var shoppingList: [String] = ["Eggs", "Milk"]
또한, [String]에 영향을 받아 타입 추론을 통해 변수에 배열을 초기화하여 할당할 수 있음.
```

```swift
var shoppingList = ["Eggs", "Milk"]
배열의 접근과 수정(Accessing and Modifying an Array)
```


> 다음은 배열의 개수를 확인하는 읽기 전용 count 속성임.

```swift
print("The shopping list contains \(shoppingList.count) items.")
```

> count 속성을 이용하지 않고 isEmpty 속성을 통해 빠르게 배열이 비었는지 확인이 가능.

```swift
if shoppingList.isEmpty {
    println("The shopping list is empty.")
} else {
    println("The shopping list is not empty.")
}
```


> 배열에 append 메소드를 통해 배열 끝에 새로운 값을 추가할 수 있음.

```swift
shoppingList.append("Flour")
// shoppingList now contains 3 items, and someone is making pancakes
하나 이상 적절한 값을 가진 배열을 추가 할당 연산자(+=)를 이용하여 추가할 있음.

shoppingList += ["Baking Powder"]
// shoppingList now contains 4 items
shoppingList += ["Chocolate Spread", "Cheese", "Butter"]
// shoppingList now contains 7 items
```

> 배열에 인덱스로 접근하여 값을 얻을 수 있음. 또한, 인덱스로 접근하여 값을 변경할 수 있음.

```swift
var firstItem = shoppingList[0]
// firstItem is equal to "Eggs"

shoppingList[0] = "Six eggs"
// the first item in the list is now equal to "Six eggs" rather than "Eggs"
배열에 인덱스 범위를 통해 접근하여 값을 변경하거나 배열을 대체함.

shoppingList[4...6] = ["Bananas", "Apples"]
// shoppingList now contains 6 items
// replace "Chocolate Spread", "Cheese" and "Butter" to "Bananas" and "Apples"
```

> 배열의 insert(atIndex:) 메소드를 호출하여 특정 인덱스에 삽입할 수 있음.

```swift
shoppingList.insert("Maple Syrup", atIndex: 0)
// shoppingList now contains 7 items
// "Maple Syrup" is now the first item in the list
```

> removeAtIndex 메소드를 호출하여 특정 인덱스의 값을 제거할 수 있음.

```swift
let mapleSyrup = shoppingList.removeAtIndex(0)
// the item that was at index 0 has just been removed
// shoppingList now contains 6 items, and no Maple Syrup
// the mapleSyrup constant is now equal to the removed "Maple Syrup" string
배열의 마지막 값을 삭제하고자 한다면 removeAtIndex 보다 removeLast 메소드를 이용하여 삭제하기 더 좋음. count 속성을 호출하는 것을 안하기 때문.

let apples = shoppingList.removeLast()
// the last item in the array has just been removed
// shoppingList now contains 5 items, and no apples
// the apples constant is now equal to the removed "Apples" string
```


> 배열에서 반복문 사용하기(Iterating Over an Array)
for-in 문을 사용하여 배열의 모든 값을 접근할 수 있음.

```swift
for item in shoppingList {
    print(item)
}
```

> 각 아이템에 정수 인덱스와 그 값이 필요하다면, enumerate 전역 함수를 사용함. enumerate 함수는 배열에 각 아이템의 인덱스와 값으로 구성된 튜플을 반환함.

```swift
for (index, value) in shoppingList.enumerated() {
    print("Item \(index + 1): \(value)")
}
```


> 배열 생성과 초기화
초기화 문법을 사용하여 특정 타입의 빈 배열을 만듬.

var someInts = [Int]()
print("someInts is of type [Int] with \(someInts.count) items.")
// prints "someInts is of type [Int] with 0 items."
someInt 변수는 [Int]에 영향을 받음. 이는 [Int] 초기화의 결과물에 설정됨.
한번이라도 타입이 설정되면 []로 초기화하여도 타입은 유지됨.

someInts.append(3)
// someInts now contains 1 value of type Int
someInts = []
// someInts is now an empty array, but is still of type [Int]
Swift에 배열 타입은 특정 크기와 그 크기에 기본 값으로 설정할 수 있는 생성자를 제공. 이 생성자에 몇 개의 아이템을 넣을 것인지(count 호출), 적합한 타입의 기본 값(repeatedValue 호출)을 넘겨줌.

var threeDoubles = [Double](count: 3, repeatedValue: 0.0)
// threeDoubles is of type [Double], and equals [0.0, 0.0, 0.0]
서로 같은 타입의 배열이 있으면 덧셈 연산자(+)를 이용하여 배열을 생성. 이 배열 타입은 앞에 배열에서 영감받아 같은 타입.

var anotherThreeDoubles = [Double](count: 3, repeatedValue: 2.5)
// anotherThreeDoubles is inferred as [Double], and equals [2.5, 2.5, 2.5]

var sixDoubles = threeDoubles + anotherThreeDoubles
// sixDoubles is inferred as [Double], and equals [0.0, 0.0, 0.0, 2.5, 2.5, 2.5]


# 6. 옵셔널
