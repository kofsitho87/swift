# Study Swift Class


1. 변수
2. 자료형
3. 연산자
4. 흐름제어구문(반복문, if else, guard, switch)
5. 집단자료형(배열, 집합, 튜플, 딕셔너리)
6. 옵셔널
7. enum
8. 함수와 클로저
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
연산자와 혼동할 수 있는 +, -, *, / 및 공백은 사용할수 없다!
_(언더바는 사용가능)

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

## 배열 Array

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


## 집합 Set

> Set은 배열과 거의 유사하지만 차이점이라고 한다면 중복된 값을 허용하지 않다는다는 점이다.

```swift
var genres: Set = ["클래식", "락", "발라드"]
```

## 튜플

> 튜플Tuple은 어떠한 값들의 묶음입니다. 배열과 비슷하다고 볼 수 있는데요. 배열과는 다르게 길이가 고정되어있답니다. 값에 접근할 때에도 [] 대신 .을 사용한다

```swift
var coffeeInfo = ("아메리카노", 5100)
coffeeInfo.0 // 아메리카노
coffeeInfo.1 // 5100
coffeeInfo.1 = 5100

// 튜플의 파라미터에 이름을 붙일 수도 있어요.
var namedCoffeeInfo = (coffee: "아메리카노", price: 5100)
namedCoffeeInfo.coffee // 아메리카노
namedCoffeeInfo.price // 5100
namedCoffeeInfo.price = 5100
```

> 튜플을 조금 응용하면, 아래와 같이 여러 변수에 값을 지정할 수도 있습니다.

```swift
let (coffee, price) = ("아메리카노", 5100)
coffee // 아메리카노
price // 5100
```

> 튜플이 가진 값을 가지고 변수에 값을 지정할 때, 무시하고 싶은 값이 있다면 _ 키워드를 사용해서 할 수 있습니다. 아래 코드에서는 "라떼"라는 첫 번째 값을 무시합니다.

```swift
let (_, latteSize, lattePrice) = ("라떼", "Venti", 5600)
latteSize // Venti
lattePrice // 5600
```

## 딕셔너리




# 6. 옵셔널

## 옵셔널
> Swift가 가지고 있는 가장 큰 특징 중 하나가 바로 옵셔널Optional입니다. 직역하면 '선택적인' 이라는 뜻이 되는데요. 값이 있을 수도 있고 없을 수도 있는 것을 나타냅니다.
예를 들어볼까요? 문자열의 값이 있으면 "가나다"가 될 것입니다. 그럼, 값이 없다면 ""일까요? 땡. ""도 엄연히 값이 있는 문자열입니다. 정확히는 '값이 없다'가 아니고 '빈 값'이죠. 값이 없는 문자열은 바로 nil입니다.+

또 다른 예를 들어볼게요. 정수형의 값이 있으면 123과 같은 값이 있을 것입니다. 값이 없다면 0일까요? 마찬가지로 0은 0이라는 숫자 '값'입니다. 이 경우에도 값이 없는 정수는 nil입니다.
마찬가지로, 빈 배열이나 빈 딕셔너리라고 해서 '값이 없는'것이 아닙니다. 다만 '비어 있을' 뿐이죠. 배열과 딕셔너리의 경우에도 '없는 값'은 nil입니다.
이렇게, 값이 없는 경우를 나타낼 때에는 nil을 사용합니다. 그렇다고 해서 모든 변수에 nil을 넣을 수 있는 것은 아닙니다. 예로, 우리가 위에서 정의한 name이라는 변수에 nil을 넣으려 하면 에러가 발생합니다.


> 값이 있을 수도 있고 없을 수도 있는 변수를 정의할 때에는 타입 어노테이션에 ?를 붙여야 합니다. 이렇게 정의한 변수를 바로 옵셔널Optional이라고 하고요. 옵셔널에 초깃값을 지정하지 않으면 기본값은 nil입니다.

```swift
var email: String?
print(email) // nil

email = "devxoul@gmail.com"
print(email) // Optional("devxoul@gmail.com")
```

## 옵셔널 바인딩 (Optional Binding)

> 옵셔널 바인딩은 옵셔널의 값이 존재하는지를 검사한 뒤, 존재한다면 그 값을 다른 변수에 대입시켜줍니다. if let 또는 if var를 사용하는데요. 옵셔널의 값을 벗겨서 값이 있다면 if문 안으로 들어가고, 값이 nil이라면 그냥 통과하게 됩니다.

```swift
if let email = optionalEmail {
  print(email) // optionalEmail의 값이 존재한다면 해당 값이 출력됩니다.
}
// optionalEmail의 값이 존재하지 않는다면 if문을 그냥 지나칩니다.
```

> 하나의 if문에서 콤마(,)로 구분하여 여러 옵셔널을 바인딩할 수 있습니다. 이곳에 사용된 모든 옵셔널의 값이 존재해야 if문 안으로 진입합니다.

```swift
var optionalName: String? = "전수열"
var optionalEmail: String? = "devxoul@gmail.com"

if let name = optionalName, email = optionalEmail {
  // name과 email 값이 존재
}
```

> 옵셔널을 바인딩할 때 ,를 사용해서 조건도 함께 지정할 수 있습니다. , 이후의 조건절은 옵셔널 바인딩이 일어난 후에 실행됩니다. 즉, 옵셔널이 벗겨진 값을 가지고 조건을 검사하게 됩니다.

```swift
var optionalAge: Int? = 22

if let age = optionalAge, age >= 20 {
  // age의 값이 존재하고, 20 이상입니다.
}
```


## 옵셔널 체이닝 (Optional Chaining)

```swift
let array: [String]? = []
var isEmptyArray = false

if let array = array, array.isEmpty {
  isEmptyArray = true
} else {
  isEmptyArray = false
}
```


> 옵셔널 체이닝을 사용하면 이 코드를 더 간결하게 쓸 수 있습니다.

```swift
let isEmptyArray = array?.isEmpty == true
```


## 옵셔널 해재하기

> 옵셔널을 사용할 때마다 옵셔널 바인딩을 하는 것이 가장 바람직합니다. 하지만, 개발을 하다보면 분명히 값이 존재할 것임에도 불구하고 옵셔널로 사용해야 하는 경우가 종종 있는데요. 이럴 때에는 옵셔널에 값이 있다고 가정하고 값에 바로 접근할 수 있도록 도와주는 키워드인 !를 붙여서 사용하면 됩니다.

```swift
print(optionalEmail) // Optional("devxoul@gmail.com")
print(optionalEmail!) // devxoul@gmail.com
```

> !를 사용할 때에는 주의할 점이 있는데, 옵셔널의 값이 nil인 경우에는 런타임 에러가 발생한다는 것입니다. Java의 NullPointerException과 비슷하다고 생각하시면 될 듯 합니다.

```swift
var optionalEmail: String?
print(optionalEmail!) // 런타임 에러!
```


## 암묵적으로 벗겨진 옵셔널 (Implicitly Unwrapped Optional)

> 만약, 옵셔널을 정의할 때 ? 대신 !를 붙이면 ImplicitlyUnwrappedOptional이라는 옵셔널로 정의됩니다. 이름이 굉장히 길죠. 직역하면 '암묵적으로 벗겨진 옵셔널'입니다.

```swift
var email: String! = "devxoul@gmail.com"
print(email) // devxoul@gmail.com
```

> 이렇게 정의된 옵셔널은 nil을 포함할 수 있는 옵셔널이긴 한데, 접근할 때 옵셔널 바인딩이나 옵셔널을 벗기는 과정을 거치지 않고도 바로 값에 접근할 수 있다는 점에서 일반적인 옵셔널과 조금 다릅니다.
옵셔널 벗기기와 마찬가지로, 값이 없는데 접근을 시도하면 런타임 에러가 발생합니다.

```swift
var email: String!
print(email) // 런타임 에러!
```



# 7. enum

> 열거라는 뜻을 가진 Enumeration에서 따온 용어입니다. 한글로 번역할 때에는 열거형이라는 말을 많이 사용합니다

```swift
enum Month: Int {
  case january = 1
  case february
  case march
  case april
  case may
  case june
  case july
  case august
  case september
  case october
  case november
  case december

  func simpleDescription() -> String {
    switch self {
    case .january:
      return "1월"
    case .february:
      return "2월"
    case .march:
      return "3월"
    case .april:
      return "4월"
    case .may:
      return "5월"
    case .june:
      return "6월"
    case .july:
      return "7월"
    case .august:
      return "8월"
    case .september:
      return "9월"
    case .october:
      return "10월"
    case .november:
      return "11월"
    case .december:
      return "12월"
    }
  }
}

let december = Month.december
print(december.simpleDescription()) // 12월
print(december.rawValue)
```


> 위 예시에서 작성한 Month는 Int를 원시값Raw Value으로 가지도록 정의되었습니다. 그렇기 때문에 각 케이스들은 1부터 12까지의 값을 가지고 있습니다. rawValue 속성이 바로 그 값을 나타내는데요. 반대로, 원시값을 가지고 Enum을 만들 수도 있습니다.

```swift
let october = Month(rawValue: 10)
print(october) // Optional(Month.october)
```

> Month(rawValue:)의 반환값이 옵셔널인 이유는, Enum에서 정의되지 않은 원시값을 가지고 생성할 경우 nil을 반환하기 때문입니다.
Month(rawValue: 13) // nil

> 일반적으로 Enum은 Int만을 원시값으로 가질 수 있다고 생각합니다. 다른 프로그래밍 언어에서는 모두 그렇거든요. 하지만, Swift의 Enum은 조금 독특합니다. (독특한게 좀 많죠?) 아래 예시는 String을 원시값으로 가지는 Enum입니다.

```swift
enum IssueState: String {
  case open = "open"
  case closed = "closed"
}
```

> 만약 어떤 API의 응답에서 내려주는 state의 값이 open 또는 closed라면, if-else 없이도 IssueState(rawValue:)를 사용해서 Enum을 생성할 수 있습니다.
Enum은 원시값을 가지지 않을 수도 있습니다. 원시값을 가져야 할 필요가 없다면 굳이 만들지 않아도 돼요.

```swift
enum Spoon {
  case dirt
  case bronze
  case silver
  case gold

  func simpleDescription() -> String {
    switch self {
    case .dirt:
      return "흙수저"
    case .bronze:
      return "동수저"
    case .silver:
      return "은수저"
    case .gold:
      return "금수저"
    }
  }
}
```

> Enum을 예측할 수 있다면 Enum의 이름을 생략할 수 있습니다. 코드가 굉장히 간결해지겠죠?
let spoon: Spoon = .gold // 변수에 타입 어노테이션이 있기 때문에 생략 가능

func doSomething(with spoon: Spoon) {
  // ...
}
doSomething(with: .silver) // 함수 정의에 타입 어노테이션이 있기 때문에 생략 가능



# 8. 함수와 클로저




# 9. 클래스와 구조체

> 클래스Class는 class로 정의하고, 구조체Structure는 struct로 정의합니다.

```swift
class Dog {
  var name: String?
  var age: Int?

  func simpleDescription() -> String {
    if let name = self.name {
      return "🐶 \(name)"
    } else {
      return "🐶 No name"
    }
  }
}

struct Coffee {
  var name: String?
  var size: String?

  func simpleDescription() -> String {
    if let name = self.name {
      return "☕️ \(name)"
    } else {
      return "☕️ No name"
    }
  }
}
```

```swift
var myDog = Dog()
myDog.name = "찡코"
myDog.age = 3
print(myDog.simpleDescription()) // 🐶 찡코

var myCoffee = Coffee()
myCoffee.name = "아메리카노"
myCoffee.size = "Venti"
print(myCoffee.simpleDescription()) // ☕️ 아메리카노


> 클래스는 상속이 가능합니다. 구조체는 불가능합니다.

```swift
class Animal {
  let numberOfLegs = 4
}

class Dog: Animal {
  var name: String?
  var age: Int?
}
```

```swift
var myDog = Dog()
print(myDog.numberOfLegs) // Animal 클래스로부터 상속받은 값 (4)
클래스는 참조Reference하고, 구조체는 복사Copy합니다.
var dog1 = Dog()  // dog1은 새로 만들어진 Dog()를 참조합니다.
var dog2 = dog1   // dog2는 dog1이 참조하는 Dog()를 똑같이 참조합니다.
dog1.name = "찡코" // dog1의 이름을 바꾸면 Dog()의 이름이 바뀌기 때문에,
print(dog2.name)  // dog2의 이름을 가져와도 바뀐 이름("찡코")이 출력됩니다.

var coffee1 = Coffee()   // coffee1은 새로 만들어진 Coffee() 그 자체입니다.
var coffee2 = coffee1    // coffee2는 coffee1을 복사한 값 자체입니다.
coffee1.name = "아메리카노" // coffee1의 이름을 바꿔도
coffee2.name             // coffee2는 완전히 별개이기 때문에 이름이 바뀌지 않습니다. (nil)
```


## 생성자 (Initializer)

> 클래스와 구조체 모두 생성자를 가지고 있습니다. 생성자에서는 속성의 초깃값을 지정할 수 있습니다.

```swift
class Dog {
  var name: String?
  var age: Int?

  init() {
    self.age = 0
  }
}

struct Coffee {
  var name: String?
  var size: String?

  init() {
    self.size = "Tall"
  }
}
```


> 만약 속성이 옵셔널이 아니라면 항상 초깃값을 가져야 합니다. 만약 옵셔널이 아닌 속성이 초깃값을 가지고 있지 않으면 컴파일 에러가 발생합니다.

```swift
class Dog {
  var name: String?
  var age: Int // 컴파일 에러!
}
stored property 'age' without initial value prevents synthesized initializers
```


> 속성을 정의할 때 초깃값을 지정해 주는 방법과,

```swift
class Dog {
  var name: String?
  var age: Int = 0 // 속성을 정의할 때 초깃값 지정
}
```


> 생성자에서 초깃값을 지정해주는 방법이 있습니다.

```swift
class Dog {
  var name: String?
  var age: Int

  init() {
    self.age = 0 // 생성자에서 초깃값 지정
  }
}
```

> 생성자도 함수와 마찬가지로 파라미터를 받을 수 있습니다.

```swift
class Dog {
  var name: String?
  var age: Int

  init(name: String?, age: Int) {
    self.name = name
    self.age = age
  }
}

var myDog = Dog(name: "찡코", age: 3)
```

> 만약 상속받은 클래스라면 생성자에서 상위 클래스의 생성자를 호출해주어야 합니다. 만약 생성자의 파라미터가 상위 클래스의 파라미터와 같다면, override 키워드를 붙여주어야 합니다. super.init()은 클래스 속성들의 초깃값이 모두 설정 된 후에 해야 합니다. 그리고 나서부터 자기 자신에 대한 self 키워드를 사용할 수 있습니다.

```swift
class Dog: Animal {
  var name: String?
  var age: Int

  override init() {
    self.age = 0 // 초깃값 설정
    super.init() // 상위 클래스 생성자 호출
    print(self.simpleDescription()) // 여기서부터 `self` 접근 가능
  }

  func simpleDescription() -> String {
    if let name = self.name {
      return "🐶 \(name)"
    } else {
      return "🐶 No name"
    }
  }
}
```

> 만약, 위 예시 코드를 아래처럼 바꿔서 super.init()을 하기 전에 self에 접근한다면 컴파일 에러가 발생합니다.

override init() {
  self.age = 0
  print(self.simpleDescription()) // 컴파일 에러!
  super.init()
}
error: use of 'self' in method call 'simpleDescription' before super.init initializes self
deinit은 메모리에서 해제된 직후에 호출됩니다.

class Dog {
  // ...

  deinit {
    print("메모리에서 해제됨")
  }
}


## 속성 (Properties)

> 속성은 크게 두 가지로 나뉩니다. 값을 가지는 속성Stored Property과 계산되는 속성Computed Property인데요.
속성이 값 자체를 가지고 있는지, 혹은 어떠한 연산을 수행한 뒤 그 결과를 반환하는지의 차이입니다.
우리가 지금까지 정의하고 사용한 name, age와 같은 속성들은 모두 Stored Property입니다. Computed Property는 get, set을 사용해서 정의할 수 있습니다. set에서는 새로 설정될 값을 newValue라는 예약어를 통해 접근할 수 있습니다.

```swift
struct Hex {
  var decimal: Int?
  var hexString: String? {
    get {
      if let decimal = self.decimal {
        return String(decimal, radix: 16)
      } else {
        return nil
      }
    }
    set {
      if let newValue = newValue {
        self.decimal = Int(newValue, radix: 16)
      } else {
        self.decimal = nil
      }
    }
  }
}

var hex = Hex()
hex.decimal = 10
hex.hexString // "a"

hex.hexString = "b"
hex.decimal // 11
```

> 위 코드에서 hexString은 실제 값을 가지고 있지는 않지만, decimal로부터 값을 받아와 16진수 문자열로 만들어서 반환합니다. decimal은 Stored Property, hexString은 Computed Property입니다.
참고로, get만 정의할 경우에는 get 키워드를 생략할 수 있습니다. 이런 속성을 읽기 전용Read Only이라고 합니다.

```swift
class Hex {
  // ...

  var hexCode: String? {
    if let hex = self.hexString {
      return "0x" + hex
    }
    return nil
  }
}
get, set과 비슷한 willSet, didSet을 이용하면 속성에 값이 지정되기 직전과 직후에 원하는 코드를 실행할 수 있습니다.
struct Hex {
  var decimal: Int? {
    willSet {
      print("\(self.decimal)에서 \(newValue)로 값이 바뀔 예정입니다.")
    }
    didSet {
      print("\(oldValue)에서 \(self.decimal)로 값이 바뀌었습니다.")
    }
  }
}
```

> 마찬가지로, willSet에서는 새로운 값을 newValue로 얻어올 수 있고, didSet에서는 예전 값을 oldValue라는 예약어를 통해 얻어올 수 있습니다.
willSet과 didSet은 일반적으로 어떤 속성의 값이 바뀌었을 때 UI를 업데이트하거나 특정 메서드를 호출하는 등의 역할을 할 때에 사용됩니다.
