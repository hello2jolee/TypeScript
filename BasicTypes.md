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