# 연산자를 이용한 타입 정의

## 유니온 타입 (Union Type)

- 유니온 타입이란 자바스크립트의 OR 연산자 `||`와 같이 A이거나 B이다 라는 의미의 타입이다.

```typescript
function logText(text: string | number) {}
```

##### 유니온 타입의 장점

- `any`를 사용하면 자바스크립트로 작성한것처럼 동작을 하지만 유니온 타입을 사용할 경우 타입스크립트의 이점을 살리면서 코딩할 수 있다.

##### 유니온 타입을 쓸 때 주의할 점

- `introduce()` 함수 안에서는 별도의 타입 가드를 이용하여 타입의 범위를 좁히지 않는 이상 기본적으로 `Person`과 `Developer` 두 타입에 공통적으로 들어있는 속성인 `name`만 접근할 수 있게 된다.

```typescript
interface Person {
  name: string;
  age: number;
}
interface Developer {
  name: string;
  skill: string;
}
function introduce(someone: Person | Developer) {
  someone.name; // O 정상 동작
  someone.age; // X 타입 오류
  someone.skill; // X 타입 오류
}
```

## 인터섹션 타입 (Intersection Type)

- 인터섹션 타입은 여러 타입을 모두 만족하는 하나의 타입을 의미한다.
- `&`연산자를 이용해 여러 개의 타입 정의를 하나로 합치는 방식을 인터섹션 타입 정의 방식이라고 한다.
