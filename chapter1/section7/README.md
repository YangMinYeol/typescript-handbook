# 제네릭(Generics)

- 제네릭은 C#, Java등의 언어에서 재사용성이 높은 컴포넌트를 만들 때 자주 활용되는 특징이다.
- 한가지 타입보다 여러가지 타입에서 동작하는 컴포넌트를 생성하는데 사용된다.

##### 제네릭의 한 줄 정의와 예시

- 제네릭이란 타입을 마치 함수의 파라미터처럼 사용하는 것을 의미한다.

```typescript
function getText<T>(text: T): T {
  return text;
}
getText<string>("hi");
getText<number>(10);
getText<boolean>(true);
```

##### 제네릭을 사용하는 이유

- any를 사용 할 경우 함수의 인자로 어떤 타입이 들어갔고 어떤 값이 반환되는지는 알 수가 없다.
  > 이러한 문제를 해결할 수 있는 것이 제네릭이다.

##### 제네릭 클래스

- 제네릭 클래스를 선언할 때 클래스 이름 오른쪽에 `<T>`를 붙여준다. 그리고 해당 클래스로 인스턴스를 생성할 때 타입에 어떤 값이 들어갈 지 지정하면 된다.

```typescript
class GenericMath<T> {
  pi: T;
  sum: (x: T, y: T) => T;
}

let math = new GenericMath<number>();
```

##### 객체의 속성을 제약하는 방법

- 두 객체를 비교할때 제네릭 제약 조건을 사용할 수 있다.

```typescript
function getProperty<T, O extends keyof T>(obj: T, key: O) {
  return obj[key];
}
let obj = { a: 1, b: 2, c: 3 };

getProperty(obj, "a"); // okay
getProperty(obj, "z"); // error: "z"는 "a", "b", "c" 속성에 해당하지 않습니다.
```
