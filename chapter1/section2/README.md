# 함수

- 웹 애플리케이션을 구현할 때 자주 사용되는 함수는 타입스크립트로 크게 다음 3가지 타입을 정의할 수 있다.
  1. 함수의 파라미터(매개변수) 타입
  2. 함수의 반환 타입
  3. 함수의 구조 타입

##### 함수의 기본적인 타입 선언

- 함수의 반환 값에 타입을 정하지 않을 때는 `void`라도 사용한다.

```typescript
function sum(a: number, b: number): number {
  return a + b;
}
```

##### 함수의 인자

- 타입스크립트에서는 함수의 인자를 모두 필수 값으로 간주합니다. 따라서 함수의 매개변수를 설정하면 `undefined`나 `null`이라도 인자로 넘겨야 한다.
- 정의된 매개변수 값만 받을 수 있고 추가로 인자를 받을 수 없다.
- 만약 정의된 매개변수의 갯수 만큼 인자를 넘기지 않으려면 `?`를 사용해야한다.

```typescript
function sum(a: number, b?: number): number {
  return a + b;
}
```

##### REST 문법이 적용된 매개변수

```typescript
function sum(a: number, ...nums: number[]): number{
  ...
}
```
