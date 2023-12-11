# Swift

## 클래스와 객체

- 클래스(Class) : 같은 종류(또는 문제 해결을 위한)의 집단에 속하는 속성과 행위를 정의한 것
- 객체(Object) : 클래스의 인스턴스(실제로 메모리에 할당되어 동작하는 모양을 갖춘 것, instance)
- 매서드(Method) or 메세지(message) : 객체가 클래스에 정의된 행위를 실질적으로 하는 함수

## 명령형 VS 함수형 프로그래밍

|   | 명령형 프로그래밍 | 함수형 프로그래밍 |
| :------------: | :-----------: | :-------------------: |
| 프로그래머가 초점을 두는 곳 | 작업 수행 알고리즘, 상태의 변경 추적 | 원하는 정보, 필요한 변환 |
| 상태 변경 | 중요 | 없음 |
| 실행 순서 | 중요 | 낮은 중요도 |
| 주요 흐름 제어 | 제어 구문(반복문, 조건문 등), 함수(매서드) 호출 | 순환(재귀)함수 호출 등의 함수 호출로 제어 |
| 주요 조작 단위 | 클래스나 구조체의 인스턴스 | 함수 |


# 문법

## 명명규칙
- 소문자 Camel Case : 함수, 메서드, 변수, 상수
- 대문자 Camel Case : 클래스, 구조체, enum, extension … etc (type)
- 대소문자구분함
- Swift API 디자인 가이드라인

## 콘솔로그
- print : 단순문자열 출력
- dump : 객체에 자세한 설명까지 출력
```swift
class Inswave {
	var product: String = ""
}

let company: Inswave = Inswave()
company.product = "웹스퀘어"
dump(company)

/* 출력결과
__lldb_expr_11.Inswave #0
  - product: "웹스퀘어"
*/
```

## 문자열보간법
- 문자열내에 변수와 상수에 값을 출력하기 위해서 사용함
- \ (변수나상수)
```swift
let name: String = "Inswave systems"
print("회사이름은 \(name) 입니다.")
```

## 퀵헬프 마크업
```swift

/// 오류타입의 열거형
/// - noAppID : hybrdApp id가 서버 Config에 없는 경우
/// - unavailableServer : 하이브리드앱 서버를 사용할 수 없음
/// - unknown : 알수없는 오류

enum hybridAppError : Error {
	case noAppID
	case unavailableServer
	case unknown
}
```

## 상수
- let 키워드를 사용하여 상수생성
- let [상수명] : [데이터타입] = [값]
- 데이터타입 생략가능
```swift
let cname: String = "inswave systems"
let myname = "changok"
let age: Int = 30
```

## 변수
- var 키워드를 사용하여 변수생성
- var [변수명] : [데이터타입] = [값]
- 데이터타입 생략가능
```swift
var job: String = "iOS Programmer"
var height = 180.0
height = 160.0
```

## 기본 데이터 타입 1
- Int : +,- 부호를 포함한 정수
- UInt : 0을 포함한 양의 정수
- Bool : 참(true),거짓(false)만 값으로 가짐. 0,1은 타입에러
- Float : 32비트 부동소수 표현 (소수점 6자리)
- Double : 64비트 부동소수 표현 (소수점 15자리)(권장)
- nil : 없음. 값이들어있지않고 비어있음을 나타내는 키워드

## 기본 데이터 타입 2
- Character : 한문자 (swift는 유니코드문자를 사용, 모든언어 및 특수문자 사용가능)
- String : 문자열, 유니코드를 사용하여 문자열앞뒤에 큰따옴표를 사용하여 표현
- 특수문자/제어문자 : 문자열내에 일정기능을하는 특수문자 ( \n, \ , * , \t ,\0 )
- Any : 모든 데이터 타입
- AnyObject : 제한적인 Any, 클래스에 인스턴스만 할당가능

## 타입추론
- 변수나 상수 선언시 특정타입을 명시하지않아도 컴파일러가 할당된값을 기준으로 타입을 결정
```swift
// name은 타입어노테이션이 있어 추론할 필요가없음. age의 경우 입력값 19를 보고 타입을 Int로 추론한다.
var name: String = "tester"
var age = 19

// 변수나 상수에 선언과 초기화를 분리시에는 선언부에 타입어노테이션을 넣어야 된다.
var number
number = 2  // error발생
```

## 난수 만들기
```swift
Int.random(in: -100...100)
UInt.random(in: 1...30 )
Double.random(in: 1.5...4.3)
Float.random(in: -0.5...1.5)
```

## 문자열
- 문자열 합성
```swift
var introduce = "저의 이름은 : "
introduce.append("PBH")

introduce = introduce + " 입니다."
```
- 문자열 카운트
```swift
var Hi = "hello Swift!"
print("글자수 확인 : \(Hi.count)")
print("비어있는 변수 확인 " \(Hi.isEmpty)")
```
- 문자열 비교
```swift
var check : Bool = false
var hello = "hello"
check = hello == "hello"
// True
check = hello == "Hello"
//false
```
- 접두어, 접미어 확인
```swift
// 접두어
var hello = "hello"
hello.hasPrefix("he")
// 접미어
hello.hasSuffix("llo")
```
- 대소문자 변경
```swift
var hello = "hello"
hello.uppercased()  // HELLO
hello.lowercased()  // hello
```

## 특수문자
- \n : 줄바꿈 문자
- \\ : 문자열 내에서 백슬래시 표현
- \" : 문자열 내에서 큰따움표 표현
- \t : 탭 문자
- \0 : NUll 문자

## Any
- 어떤 종류의 데이터 타입으로도 할당 할 수 있는 타입
```swift
var some : Any = "hello world"
some = 100
some = 1.22
```

## 컬렉션 1
- 튜플 : 지정된 데이터의 묶음. 파이선의 튜플과 유사, 타입이름은 따로없고 일정타입의 나열생성됨
```swift
 var cat: (name:String, age:Int, size:String) = ("name",2,"big")
 cat.name = "dog"   // 요소의 이름을 통해 접근
 cat.2 = 4  // 요소의 인덱스를 통해 접근
```
- 배열 : 같은 타입의 데이터를 일렬로 순서대로 저장하는 형태의 컬렉션
```swift
 var names: Array<String> = ["inswave","rnd1","rnd2"]
 var names: [String] = ["inswave","rnd1","rnd2"]

 var emptyArray : [Any] = [Any]()   // Any 데이터를 요소로 갖는 빈 배열 생성
 var emptyArray : [Any] = Array<Any>()   // Any 데이터를 요소로 갖는 빈 배열 생성
 var emptyArray : [Any] = []   // Any 데이터를 요소로 갖는 빈 배열 생성
```
```swift
// 배열의 사용
var names : [Any] = ["hi", "hello", "swift"]
names[2] = "world"
names.append("python")
names.append(contentsOf:["js", "html"])
names.insert("happy", at:2)
names.removeFirst()
names.removeLasr()
names.remove(at:2)
print(names[1...3])
```

## 컬렉션 2
- 딕셔너리 : 순서없이 키(unikey)와 값의 쌍으로 구성되는 컬렉션
```swift
 var codeForName: Dictionary<String, Int> = Dictionary<String,Int>()
 var codeForName:[String,Int] = [String:Int]()
 var codeForName:[String,Int] = [:]

 var names : [Any, Any] = ["a" : 1, "b" : 2, "c" : 3]
 names["a"] // 1
 names["b"] = 4
 names.removeValue(forKey: "c")
 names["c", defult:0]
```

## 컬렉션 3
- 세트 : 같은타입의 데이터를 순서없이 하나의 묶음으로 저장, 중복없음
- 내부의 값이 모두 유일하기 때문에 집합관계를 표현할 때 유용하다
```swift
// 타입(Set)을 지정해주지 않으면 Array로 인식
 var codes: Set<String> = Set<String>()
 let 새: Set<String> = ["비둘기","닭","꿩","매"]
```
```swift
// Set의 활용
let englishClass : Set<String> = ["jon", "Kim", "haha"]
let koreaClass : Set<String> = ["jon", "Nana", "Ou"]

// 교집합
let intersectSet : Set<String> = englishClass.intersection(koreaClass)

// 여집합
let intersectSet : Set<String> = englishClass.symmetricDiffernce(koreaClass)

// 합집합
let intersectSet : Set<String> = englishClass.union(koreaClass)

// 차집합
let intersectSet : Set<String> = englishClass.subtracting(koreaClass)

// 정렬
koreaClass.sorted()

// 서로 배타적(다른)인가 true
새.isDisjoint(with : 포유류)

// 새가 동물의 부분 집합인가 true
새.isSubset(of: 동물)

// 동물은 포유류의 전체집합인가 true
동물.isSuperset(of : 포유류)
```

## randomElement(), shuffle(), shuffled()
- randomElement : 임의의 요소 추출
- shuffle : 컬렉션 섞기
- shuffled : 기존의 컬렉션을 이용하여 섞인 새로운 컬렉션 생성

## 열거형 
- 연관된 항목들을 묶어서 표현, enum키워드를 사용하여 생성
```swift
 enum School { case primary, elementary, middle, high }

 print(School.allCases)
```

## 비교 연산자
- A === B : 같은 인스턴스를 가르키는지 결과값 Bool 반환
- A !== B : 참조가 같지 않다
- A ~= B : A와 B의 패턴이 매치되는지 확인

## 범위 연산자
- 폐쇠 범위 연산자 : A...B
- 반폐쇠 범위 연산자 : A.. < B
- 단방향 범위 연산자 : A... or ...A or .. < A

## 조건문
- if문 : 정수,실수 등 0이 아닌 모든 값을 참으로 취급하여 조건 값이 될 수 있었던 다른언어와 달리 스위프트는 조건값이 꼭 Bool 타입이어야한다.
- switch문 : 다른언어에 비해 많이 다르다. switch구문에 ()를 생략가능, break문은 선택사항.
    - case문 내부코드 실행후 자동 break됨.

### switch문 예
```swift
switch 입력값 {
case 비교값1:
	실행구문
case 비교값2:
	실행구문
	fallthrough // 이번케이스를 마치고 switch문이 끝나지않음. 다음으로 진행
case 비교값3, 비교값4, 비교값5 : //여러개비교 가능
	실행구문
	break //break문을 통한 종료는 선택사항
default: // 한정된 범위가 명확하지않으면 default케이스는 필수
	실행구문
}
```

## 반복문
- 스위프트의 반복문은 기존언어의 반복문과 크게 다르지않음.
- C스타일에 for문 삭제됨.
- 조건에 괄호 생략가능.
- do-while문은 repeat-while문으로 구현

### 반복문 예

```swift
//for-in 반복문
for 임시 상수 in 시퀀스 아이템 {
	실행코드
}

// while
var items = ["ins1","ins2","ins3"]
while items.isEmpty == false {
	print("hello \(items.removeFirest())")
}

// repeat-while
var items = ["ins1","ins2","ins3"]
repeat {
	print("hello \(items.removeFirest())")
} while items.isEmpty == false

```

## 함수
- 스위프트의 함수는 재정의(오버라이드)와 중복정의(오버로드)를 모두지원
- 함수정의 키워드 func
- 반환타입은 ->를 사용하여 명시
- 매개변수이름,전달인자레이블
- 매개변수이름을 사용하지않을때는 와일드카드 식별자사용
- 종료되지않는 함수( 비반환함수, 비반환메서드 ) : 반환타입을 Never로 명시

### 함수 예

```swift
//함수정의
func 함수이름 (매개변수...) -> 반환타입 {
	실행구문
	return 반환값
}

//매개변수이름, 전달인자레이블
func 함수이름 (매개변수이름 전달인자레이블:매개변수타입, 매개변수이름 전달인자레이블:매개변수타입) -> 반환타입 {
	실행구문
	return 반환값
}

//와일드카드 사용예
func sayHelo(_ name:String) -> String {
	print("Helo \(name)!")
}

//종료되지않는 함수
func crashAndReport() -> Never {
	fatalError("something crash")
}
```

## 옵셔널
- 옵셔널은 단어 뜻대로 ‘선택적인’
- 값이 있을 수도, 없을 수도 있음
- 즉 이 변수는 꼭 값이 있다는 것을 보장못함. nil일수도있음.
- nil은 옵셔널로 선언된 곳에서만 사용가능. 옵셔널변수 또는 상수는 데이터타입 뒤에 물음표를 붙여서 사용

### 옵셔널 예
```swift
// 옵셔널변수 선언과 nil할당
var vname: String? = "changok"
print(vname)
vname = nil
print(vname)

//옵셔널강제추출
var myName: String? = "changok"
if myName != nil {
    print("my name is \(myName!)")
} else {
    print("my name is nil")
}

//옵셔널바인딩
var yourname: String? = "changok"
if let name = yourname {
    print("your name is \(name)")
} else {
    print("your name is nil")
}
```

## 구조체
- 데이터타입들을 묶어서 사용할 때 필요함.
- swift의 구조체는 메서드를 가질 수 있음.
- struct 키워드로 정의
```swift
struct 구조체이름 {
	프로퍼티
	메서드
	...
}
```

### 구조체 예
```swift
struct base{
	var name: String
	var age: Int
}
var base1: base = base(name:"inswave",age:16)
base1.name = "websquare" //변경가능
base1.age = 10

let base2: base = base(name:"proworks",age:14)
base2.age = 15  // 변경불가
```

## 클래스
- swift 클래스는 부모클래스없이 단독으로 정의 가능
- class 키워드를 사용하여 정의

```swift
class 클래스이름: 부모클래스이름 {
	프로퍼티
	메서드
}

//deinit
class Person {
	var height: Double = 0.0
	var weight: Double = 0.0
	deinit {
		print("person is died")
	}
}

var tester: Person? = Person()
tester = nil // print 'persion is died'
```

## 구조체와 클래스의 차이
- 구조체는 상속없음
- 타입캐스팅은 클래스의 인스턴스에만 허용
- 디이니셜라이저는 클래스이 인스턴스만 활용가능
- 참조횟수계산은 클래스의 인스턴스에만 적용
- 구조체는 값타입이고 클래스는 참조타입이다.

### 값타입과 참조타입 차이
```swift
struct Info {
	var name :String
}
var myInfo: Info = Info(name: "changok")
var friendInfo: Info = myInfo
friendInfo.name = "tom"

print("my name is \(myInfo.name)")
print("my friend name is \(friendInfo.name)")
// friendInfo는 myInfo으 값을 복사해서 서로 별개의 값을 가짐.

class Person {
	var name: String = "changok"
	var age: Int = 30
}
var myObj: Person = Person()
var myFriend: Person = myObj
print("my age is \(myObj.age)") // 30
print("my friend age is \(myFriend.age)") // 30

myFriend.age = 29
print("my age is \(myObj.age)") // 29
print("my friend age is \(myFriend.age)") // 29

```

## 클래스
- 프로퍼티
    - 저장 프로퍼티 : 인스터스의 변수 나 상수
    - 연산 프로퍼티 : 특정연산을 수행한 결과값을 가짐
    - 타입 프로퍼티 : 인스턴스가 아닌 타입자체에 속한 프로퍼티
    - 프로퍼티 감시자 : 프로퍼티값이 변경이되면 호출되는 메서드 (willSet,didSet)
- 메서드
    - 인스턴스 메서드 : 특정타입에 인스턴스에 속한 메서드 (일반적인)
    - 타입 메서드 : 타입자체에서 호출이 가능한 메서드
- 접근제어 : 코드끼리 상호작용할 때 파일 간 또는 모듈간에 접근을 제한 할 수 있는 기능, 접근제어를 통해 구현은 숨기고 허용된 기능만 노출할 수 있음.

## Foundation Framework
```swift
import Combine
import CoreFoundation
import CoreGraphics
import Darwin
import Darwin.uuid
import Dispatch
import Foundation.FoundationErrors
import Foundation.FoundationLegacySwiftCompatibility
import Foundation.NSArray
import Foundation.NSAttributedString
import Foundation.NSAutoreleasePool
import Foundation.NSBundle
import Foundation.NSByteCountFormatter
import Foundation.NSByteOrder
import Foundation.NSCache
import Foundation.NSCalendar
import Foundation.NSCharacterSet
import Foundation.NSCoder
import Foundation.NSComparisonPredicate
import Foundation.NSCompoundPredicate
import Foundation.NSData
import Foundation.NSDate
import Foundation.NSDateComponentsFormatter
import Foundation.NSDateFormatter
import Foundation.NSDateInterval
import Foundation.NSDateIntervalFormatter
import Foundation.NSDecimal
import Foundation.NSDecimalNumber
import Foundation.NSDictionary
import Foundation.NSEnergyFormatter
import Foundation.NSEnumerator
import Foundation.NSError
import Foundation.NSException
import Foundation.NSExpression
import Foundation.NSExtensionContext
import Foundation.NSExtensionItem
import Foundation.NSExtensionRequestHandling
import Foundation.NSFileCoordinator
import Foundation.NSFileHandle
import Foundation.NSFileManager
import Foundation.NSFilePresenter
import Foundation.NSFileVersion
import Foundation.NSFileWrapper
import Foundation.NSFormatter
import Foundation.NSHTTPCookie
import Foundation.NSHTTPCookieStorage
import Foundation.NSHashTable
import Foundation.NSISO8601DateFormatter
import Foundation.NSIndexPath
import Foundation.NSIndexSet
import Foundation.NSInvocation
import Foundation.NSItemProvider
import Foundation.NSJSONSerialization
import Foundation.NSKeyValueCoding
import Foundation.NSKeyValueObserving
import Foundation.NSKeyedArchiver
import Foundation.NSLengthFormatter
import Foundation.NSLinguisticTagger
import Foundation.NSListFormatter
import Foundation.NSLocale
import Foundation.NSLock
import Foundation.NSMapTable
import Foundation.NSMassFormatter
import Foundation.NSMeasurement
import Foundation.NSMeasurementFormatter
import Foundation.NSMetadata
import Foundation.NSMetadataAttributes
import Foundation.NSMethodSignature
import Foundation.NSNetServices
import Foundation.NSNotification
import Foundation.NSNotificationQueue
import Foundation.NSNull
import Foundation.NSNumberFormatter
import Foundation.NSObjCRuntime
import Foundation.NSObject
import Foundation.NSOperation
import Foundation.NSOrderedCollectionChange
import Foundation.NSOrderedCollectionDifference
import Foundation.NSOrderedSet
import Foundation.NSOrthography
import Foundation.NSPathUtilities
import Foundation.NSPersonNameComponents
import Foundation.NSPersonNameComponentsFormatter
import Foundation.NSPointerArray
import Foundation.NSPointerFunctions
import Foundation.NSPort
import Foundation.NSPredicate
import Foundation.NSProcessInfo
import Foundation.NSProgress
import Foundation.NSPropertyList
import Foundation.NSProxy
import Foundation.NSRange
import Foundation.NSRegularExpression
import Foundation.NSRelativeDateTimeFormatter
import Foundation.NSRunLoop
import Foundation.NSScanner
import Foundation.NSSet
import Foundation.NSSortDescriptor
import Foundation.NSStream
import Foundation.NSString
import Foundation.NSTextCheckingResult
import Foundation.NSThread
import Foundation.NSTimeZone
import Foundation.NSTimer
import Foundation.NSURL
import Foundation.NSURLAuthenticationChallenge
import Foundation.NSURLCache
import Foundation.NSURLConnection
import Foundation.NSURLError
import Foundation.NSURLProtectionSpace
import Foundation.NSURLProtocol
import Foundation.NSURLRequest
import Foundation.NSURLResponse
import Foundation.NSURLSession
import Foundation.NSUUID
import Foundation.NSUbiquitousKeyValueStore
import Foundation.NSUndoManager
import Foundation.NSUnit
import Foundation.NSUserActivity
import Foundation.NSUserDefaults
import Foundation.NSValueTransformer
import Foundation.NSXMLParser
import Foundation.NSXPCConnection
import Foundation.NSZone
import Foundation
import Foundation.NSURLCredential
import Foundation.NSURLCredentialStorage
import Foundation.NSValue
import ObjectiveC
```

### Fundamentals
- Numbers, Data, and Basic Value : Int, Double 비롯한 기본적인 변수 사용
- String and Text : String에 관련된 처리들
- Collections : Array, Dictionary, Set등 list와 관련된 처리
- Dates and Times : 날짜와 시간 처리
- Units and Measurement
- Data Formatting
- Filters and Sorting : 배열의 검사 및 정렬에 관련된 처리

### App Support
- Task Management
- Resources : 리소스와 관련된 처리
- Notifications : Notification Center 등에 관련된 처리
- App Extension Support 
- Errors and Exceptions
- Scripting Support

### Files and Data Persistence
- File System
- Archives and Serialization
- Preferences
- Spotlight
- iCloud

### Networking
- URL Loading System : URLSession등 네트워킹과 관련된 처리
- Bonjour

### Low-Level Utilities
- XPC
- Object Runtime
- Processes and Threads
- Streams, Sockets, and Ports

