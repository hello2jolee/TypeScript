# 기본 유형  _(Basic Types)_

프로그램이 유용하기 위해서는, 사용자가 가장 간단한 데이터 단위(숫자, String, 구조, Boolean 기타 등등)를 사용할 수 있어야 합니다. 
TypeScript는, JavaScript에서 지원하는 유형들과 더불어 도음이 될만한 열거 형들을 추가로 지원합니다.

## Boolean
* 가장 기본적인 데이터 유형은 간단한 참/거짓 값이며, JavaScript와 TypeScript에서 `boolean` 이라고 부릅니다.
``` typescript
let isDone: boolean = false;
```

## Number
* JavaScript에서와 마찬가지로, TypeScript의 모든 숫자는 부동 소수점 값 또는 BigInteger입니다. 부동 소수점 숫자는 `number`, BigInteger는 `bigint`라는 유형을 가집니다. 추가적으로 16진수와 10진수 리터럴 외에도 TypeScript는 ECMAScript 2015에 도입 된 이진 및 8 진수 리터럴을 지원합니다.
``` typescript
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
let big: bigint = 100n;
```

## String
* 웹 페이지와 서버를 위해 JavaScript로 프로그램을 작성하는 또 다른 근본적인 이유는 텍스트 데이터로 작업하기 위해서입니다. 다른 언어에서와 마찬가지로 이러한 텍스트 데이터 유형을 참조하기 위해 유형 문자열을 사용합니다. JavaScript와 마찬가지로 TypeScript는 큰 따옴표 `(")` 또는 작은 따옴표 `(')`를 사용하여 문자열 데이터를 묶습니다.
``` typescript
let color : string = "blue";
color = 'red;
```
* 여러 줄에 걸쳐 있고 표현식이 포함 된 템플릿 문자열을 사용할 수도 있습니다. 이러한 문자열은 역 따옴표 문자로 둘러싸여 있으며 포함 된 표현식은 `$ {expr}` 형식입니다. 

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
## Unknown(알 수 없음)
* 응용 프로그램을 작성할 때 모르는 변수 유형을 설명해야 할 수도 있습니다. 이러한 값은 동적 콘텐츠(예 : 사용자로부터) 또는 API의 모든 값을 의도적으로 수락하기를 원할 수 있습니다. 이 경우 컴파일러와 미래의 독자에게 이 변수가 무엇이든 될 수 있음을 알려주는 유형을 제공하고 싶으므로 `unknown` 유형을 제공합니다. 

``` typeScript
let notSure : unknown = 4;
notSure = "maybe a string instead";

notSure = false; // 가능, 확실한 boolean
```
* 알 수 없는 유형의 변수가 있는 경우, `typeof` 검사, 비교 검사 또는 이후 장에서 설명 할 고급 유형 보호를 수행하여 보다 구체적인 변수로 좁힐 수 있습니다.
 ``` typeScript
 declare const maybe: unknown;
 // 'maybe'는 string, object, boolean, undefined 또는 다른 유형 일 수 있습니다.
 const aNumber : number = maybe; // 'unknown'은 'number' 유형으로 선언 할 수 없습니다.

 if(maybe === true) {
     // TypeScript는 'maybe'가 boolean 유형이라는 것을 알고 있습니다.
     const aBoolean: boolean = maybe;
     // 그러므로, string 유형이 될 수 없습니다.
     const aString: string = maybe; // 'boolean' 유형은 'string' 유형으로 선언 할 수 없습니다.
 }

 if(typeof maybe === 'string') {
     // TypeScript는 'maybe'가 string 유형이라는 것을 알고 있습니다.
     const aString: string = maybe;
     // 그러므로, boolean 유형이 될 수 없습니다.
     const aBoolean: boolean = maybe; // 'string' 유형은 'boolean' 유형으로 선언 할 수 없습니다.
 }
 ```

 ## Any(어떤)
 * 일부 상황에서는 모든 유형 정보를 사용할 수 없거나 해당 선언에 부적절한 노력이 필요합니다. TypeScript 또는 타사 라이브러리 없이 작성된 코드의 값에 대해 이러한 문제가 발생할 수 있습니다. 이러한 경우 유형 검사를 `opt-out` 할 수 있습니다. 이를 위해 이러한 값에 `any` 유형으로 레이블을 지정합니다.
 ```typeScript
 declare function getValue(key: string): any;
 // OK, 'getValue'의 반환 값이 확인되지 않았습니다.
 const str: string = getValue("myString");
 ```
* `any` 유형은 기존 JavaScript와 함께 작업하는 강력한 방법으로, 컴파일하는 동안 점차적으로 유형 검사를 opt-in 밒 opt-out 할 수 있습니다. `unknown` 유형과 달리 `any` 유형의 변수는 존재하지 않는 속성을 포함하여 임의의 속성에 액세스 할 수 있습니다. 이러한 속성에는 함수가 포함되며 TypeScript 해당 존재 또는 유형을 확인하지 않습니다.

```typeScript
let looselyTyped: any = 4;
// OK, ifItExists는 런타임에 존재할 수 있습니다.
looselyTyped.ifItExists();
// OK, toFixed가 존재합니다 (하지만 컴파일러는 확인하지 않습니다)
looselyTyped.toFixed();

let stricklyTyped: unknown = 4;
strictlyTyped.toFixed(); // Object는 'unknown' 유형입니다.
```
* `any`는 계속해서 객체를 통해 전파됩니다:
```typeScript
let looselyTyped: any = {};
let d = looselyTyped.a.b.c.d;
// ^ = let d: any
```
* 결국, `any`의 모든 편의는 유형 안전성을 잃는 대가로 온다는 것을 기억하십시오. 유형 안전성은 TypeScript를 사용하는 주요 동기 중 하나이며 필요하지 않은 경우 `any` 사용을 피해야합니다.

 ## Void (빈)
 * `void`는 `any`의 반대와 비슷합니다 : 어떤 타입도 전혀 가지지 않습니다. 일반적으로 값을 반환하지 않는 함수의 반환 유형으로 볼 수 있습니다.
 ```typeScript
 function warnUser(): void {
     console.log("This is my warning messasge")
 }
 ```
 * `void` 유형의 변수를 선언하는 것은 `null` (`--strictNullChecks`가 지정되지 않은 경우에만 다음 섹션 참조) 또는 `unknown` 변수만 할당할 수 있기 때문에 유용하지 않습니다:
 ```typeScript
 let unusable: void = undefined;
 // `--strictNullChecks`이 주어지지 않아도 괜찮습니다.
 unusable = null;
 ```

 ## Null and Undefined
 * TypeScript에서는 `undefined`와 `null` 둘 다 실제로 각각 `undefined`와 `null`이라는 유형을 가지고 있습니다. `void` 처럼, 그 자체로는 그다지 유용하지 않습니다.
  ```typeScript
  // 이 변수에 할당 할 수 있는 것은 많지 않습니다!
  let u: undefined = undefined;
  let n: null = null;
   ```
* 기본적으로 `null`과 `undefined`는 다른 모든 유형의 하위 유형입니다. 즉, `number`와 같은 것에 `null`과 `undefined`를 할당 할 수 있습니다.
* 그러나 `--strictNullChecks` 플래그를 사용할 때 `null`과 `undefined`는 `unknown`, `any` 및 해당 유형에만 할당 할 수 있습니다(한 가지 예외는 `undefined`는 `void`에도 할당 할 수 있다는 점입니다). 이렇게 하면 많은 일반적인 오류를 방지할 수 있습니다. `string`, `null` 또는 `undefined`를 전달하려는 경우 `string | null | undefined` 공용체 유형을 사용할 수 있습니다.
* 공용체 유형은 이후 장에서 다룰 고급 주제입니다.
    * 참고: 가능하면 `--strictNullChecks`를 사용하는 것을 권장하지만, 핸드북의 목을 위해 이 기능이 꺼져있다고 가정합니다.

## Number
* `never` 유형은 발생하지 않는 값 유형을 나타냅니다. 예를 들어, `never`는 항상 예외를 발생시키는 함수 표현식 또는 화살표 함수 표현식 또는 반환하지 않는 표현식의 반환 유형입니다. 변수는 참일 수 없는 유형 가드에 의해 좁혀지면 유형 `never`도 획득합니다.
* `never` 유형은 모든 유형의 하위 유형이며 모든 유형에 할당 할 수 있습니다. 그러나 어떤 유형도 `never`의 하위 유형이 아니거나 `never`에 할당 할 수 없습니다(`never` 자체 제외). `any` 조차도 `never`에게 할당 할 수 없습니다.
* `never`를 반환하는 함수의 몇 가지 예 :

```typeScript
// never를 반환하는 함수에는 도달 가능한 끝 점이 없어야 합니다.
function error(message: string): never {
    throw new Error(message);
}

// 유추 된 반환 유형은 never 입니다.
function fail() {
    return error("Something failed");
}

// never를 반환하는 함수에는 도달 가능한 끝 점이 없어야 합니다.
function infiniteLoop(): never {
    while(true) {}
}
```

## Object
* `object`는 기본이 아닌 유형을 나타내는 유형입니다. 즉, `number`, `string`, `boolean`, `bigint`, `symbol`, `null` 또는 `undefined`가 아닌 것입니다.
* `object` 유형을 통해, `Object.create`와 같은 API들이 더 잘 표현 될 수 있습니다. 예를 들면 : 

``` typeScript
declare function create(o: object | null): void;

// OK
create({prop: 0}),
create(null);

create(42); // '42' 유형의 값은 'object | null' 파라미터에 할당 할 수 없습니다.
create("string") // '"string"' 유형의 값은 'object | null' 파라미터에 할당 할 수 없습니다.
create(false) // 'false' 유형의 값은 'object | null' 파라미터에 할당 할 수 없습니다.
create(undefined) // 'undefined' 유형의 값은 'object | null' 파라미터에 할당 할 수 없습니다.
```
* 일반적으로는, 이것을 사용할 필요가 없습니다.