# 기본 유형  _(Basic Types)_

프로그램들이 유용하기 위해서는, 우리는 가장 간단한 데이터 단위(숫자, String, 구조, Boolean 기타 등등)를 사용할 수 있어야 합니다. 
TypeScript에서는, 이를 위해 열거 형 몇 개는 추가한 것과 더불어, JavaScript에서 예상하는 것과 동일한 유형을 지원합니다.

## Boolean
* 가장 기본적인 데이터 유형은 간단한 참/거짓 값이며, JavaScript와 TypeScript에서 `boolean` 이라고 부릅니다.
``` typescript
let isDone : boolean = false;
```

## Number
* JavaScript에서와 마찬가지로, TypeScript의 모든 숫자는 부동 소수점 값 또는 BigInteger입니다. 부동 소수점 숫자는 `number`, BigInteger는 `bigint`라는 유형을 얻습니다. 추가적으로 16진수와 10진수 리터럴 외에도 TypeScript는 ECMAScript 2015에 도입 된 이진 및 8 진수 리터럴도 지원합니다.
``` typescript
let decimal : number = 6;
let hex : number = 0xf00d;
let binary : number = 0b1010;
let octal : number = 0o744;
let big : bigint = 100n;
```

## String
* 웹 페이지와 서버를 위해 JavaScript로 프로그램을 만드는 또 다른 근본적인 부분은 텍스트 데이터로 작업하는 것입니다. 다른 언어에서와 마찬가지로 이러한 텍스트 데이터 유형을 참조하기 위해 유형 문자열을 사용합니다. JavaScript와 마찬가지로 TypeScript는 큰 따옴표 `(")` 또는 작은 따옴표 `(')`를 사용하여 문자열 데이터를 묶습니다.
``` typescript
let color : string = "blue";
color = 'red;
```
* 여러 줄에 걸쳐 있고 표현식이 포함 된 템플릿 문자열을 사용할 수도 있습니다. 이러한 문자열은 역 따옴표 / 역 따옴표 문자로 둘러싸여 있으며 포함 된 표현식은 `$ {expr}` 형식입니다. 

``` typescript
let fullName : string = `Bob Bobbington`
let age : number = 37;
let sentence : string = `Hello, my name is ${fullName}.

I'll be ${age + 1} years old next month.`;
```
* 이것은 다음과 같이 문장을 선언하는 것과 같습니다:
``` typescript
let sentence : string =
"Hello, my name is " +
fullName +
".\n\n" +
  "I'll be " +
  (age + 1) +
  " years old next month.";
```

## Array
* JavaScript와 마찬가지로 TypeScript를 사용하면 값을 배열에 저장할 수 있습니다. 배열은 두 가지 방법으로 구현할 수 있습니다. 
첫 번째 방법은 요소 유형 다음에 `[]`를 사용하여 해당 요소 유형의 배열을 나타냅니다.
``` typescript
let list : number[] = [1, 2, 3];
``` 

* 두 번째 방법은 일반 배열 유형, `Array <elemType>`을 사용합니다.
``` TypeScript
let list : Array<number> = [1, 2, 3];
```

## Tuple
* 투플을 통해 유형이 알려져 있지만, 동일할 필요 없는 고정된 숫자 요소를 표현 할 수 있다. 예를 들면, `string`, `number`를 한 쌍의 값으로 표현할 수 있습니다.

``` typeScript
// 튜플 유형을 선언하다
let x : [string, number];

// 적절한 초기화하다
x = ["hello", 10] // O
// 부적절한 초기화
x = [10, "hello"] // X
// 'number' 유형에 'string' 변수를 선언할 수 없다
// 'string' 유형에 'number' 변수를 선언할 수 없다
```

* 알려진 인덱스의 요소에 접근할 때, 올바른 유형이 검색됩니다.

``` typeScript
// 가능
console.log(x[0].substring(1));

console.log(x[1].substring(1)); // 'substring'은 'number' 유형에 존재하지 않기 때문에 경고창이 뜹니다.
``` 
* 알려진 인덱스 집합 외부의 요소에 접근하면 오류가 발생하여 실패합니다.

``` typeScript
x[3] = "world"; // 길이가 2인 '[string number]' 튜플 형태에는 인덱스 3에 요소가 없기 때문에 에러가 발생합니다.

console.log(x[5].toString()); // 대상은 아마도 'undefined'일 것입니다. 길이가 2인 '[string number]' 튜플 형태에는 인덱스 5에 요소가 없습니다.
``` 

## Enum(열거형)
* JavaScript 표준 데이터 유형의 유용한 추가 기능은 열거형입니다. C#과 같은 언어에서와 같이 열거 형은 숫자 집합에 더 친숙한 이름을 제공하는 방법입니다.
``` typeScript
enum Color {
    Red,
    Green,
    Blue,
}
let c : Color = Color.Green;
``` 
* 기본적으로, 열거 형은 멤버들을 `0`번 부터 멤버 번호를 매깁니다. 멤버 중 하나의 값을 수동으로 설정하여 번호를 변경할 수 있습니다. 예를 들면, 이전 예시의 번호를 `0` 대신 `1`부터 적용할 수 있습니다.  
``` typeScript
enum Color {
    Red = 1,
    Green,
    Blue,
}
let c : Color = Color.Green;
``` 
* 또는 열거 형의 모든 값을 수동으로 설정할 수 있습니다. 
``` typeScript
enum Color {
    Red = 1,
    Green = 2,
    Blue = 4,
}
let c : Color = Color.Green;
``` 
* 열거 형의 편리한 기능은 숫자 값에서 열거 형의 해당 값 이름으로 이동할 수도 있다는 것입니다. 예를 들어, 값이 `2` 이지만 `Color`열거 형에 매핑 된 값이 확실하지 않은 경우 해당 이름을 조회 할 수 있습니다. 

``` typeScript
enum Color {
    Red = 1,
    Green,
    Blue,
}
let colorName : string = Color[2];

// 'Green'을 출력한다
console.log(colorName);
```
