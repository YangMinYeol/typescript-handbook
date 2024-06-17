# 기본 타입

- 타입스크립트의 기본 타입에는 12가지가 있다.

1. Boolean
2. Number
3. String
4. Object
5. Array
6. Tuple
7. Enum
8. any
9. void
10. null
11. undefined
12. never

##### String

- 자바스크립트 변수의 타입이 문자열인 경우 아래와 같이 선언

```typescript
let str: string = "hi";
```

##### Number

- 타입이 숫자인 경우 아래와 같이 선언

```typescript
let num: number = 10;
```

##### Boolean

- 타입이 진위 값인 경우 아래와 같이 선언

```typescript
let isBoolean: boolean = false;
```

##### Array

- 타입이 배열인 경우 아래와 같이 선언

```typescript
let arr: number[] = [1, 2, 3];
```

- 제너릭을 사용해 아래와 같이 선언

```typescript
let arr: Array<number> = [1, 2, 3];
```

##### Tuple

- 튜플은 배열의 길이가 고정되고 각 요소의 타입이 지정되어 있는 배열 형식을 의미한다
- 정의하지 않은 타입, 인덱스로 접근할 경우 오류가 난다.

```typescript
let arr: [string, number] = ["hi", 10];
```

##### Enum

- C, Java와 같은 다른 언어에서 흔하게 쓰이는 타입으로 특정 값(상수)들의 집합을 의미한다.
- 인덱스를 사용자 편의로 변경하여 사용할 수 있다.

```typescript
enum Avengers {
  Capt = 2,
  IronMan,
  Thor,
}
let hero: Avengers = Avengers[2]; // Capt
let hero: Avengers = Avengers[4]; // Thor
```

##### any

- 단어 의미 그대로 모든 타입에 대해서 허용한다는 의미를 갖는다.
- 기존에 자바스크립트로 구현되어 있는 웹 서비스 코드에 타입스크립트를 점진적으로 적용할 때 활용하면 좋은 타입이다.

```typescript
let str: any = "hi";
let num: any = 10;
let arr: any = ["a", 2, true];
```

##### void

- 반환 값이 없는 함수의 반환 타입
- `return`이 없거나 `return`이 있더라도 반환하는 값이 없으면 함수의 반환 타입을 `void`로 지정한다.

```typescript
function printSomething(): void {
  console.log("sth");
}

function returnNothing(): void {
  return;
}
```

##### Never

- 함수의 끝에 절대 도달하지 않는다는 의미를 지닌 타입이다.

```typescript
// 이 함수는 절대 함수의 끝까지 실행되지 않는다는 의미
function neverEnd(): never {
  while (true) {}
}
```
