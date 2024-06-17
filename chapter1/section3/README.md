# 인터페이스

- 인터페이스는 다음과 같은 범주에 대해 약속을 정의할 수 있다.
  1. 객체의 스펙(속성과 속성의 타입)
  2. 함수의 파라미터
  3. 함수의 스펙(파라미터, 반환 타입 등)
  4. 배열과 객체를 접근하는 방식
  5. 클래스
- 인터페이스를 인자로 받아 사용할 때 항상 인터페이스의 속성 갯수와 인자로 받는 객체의 속성 갯수를 일치시키지 않아도 된다.

##### 옵션 속성

- 속성의 끝에 `?`를 붙인다.
- 사용 하지 않아도 되는 속성을 옵션 속성이라 한다

```typescript
interface 인터페이스_이름 {
  속성?: 타입;
}
```

##### 옵션 속성의 장점

- 속성을 선택적으로 적용할 수 있다.
- 인터페이스에 정의되어 있지 않은 속성에 대해서 인지시켜줄 수 있다.

##### 읽기 전용 속성

- 인터페이스로 객체를 처음 생성할 때만 값을 할당하고 그 이후에는 변경할 수 없는 속성을 의미한다.
- `readonly`속성을 앞에 붙인다.

```typescript
interface CraftBeer {
  readonly brand: string;
}
```

##### 읽기 전용 배열

- `ReadonlyArray<T>` 타입을 사용하면 읽기 전용 배열을 생성할 수 있다.

```typescript
let arr: ReadonlyArray<number> = [1, 2, 3];
```

##### 객체 선언과 관련된 타입 체킹

- `myBeer` 객체에는 `brandon`이 선언되어 있어 오탈자 점검을 요하는 오류가 난다. 이런 타입 추론을 무시하고 싶다면 아래와 같이 선언한다.

```typescript
interface CraftBeer {
  brand?: string;
}
function brewBeer(beer: CraftBeer) {
  //..
}
let myBeer = { brandon: "what" };
brewBeer(myBeer as CraftBeer);
```

- 인터페이스 정의하지 않은 속성들을 추가로 사용하고 싶을 때는 아래와 같은 방법을 사용한다.

```typescript
interface CraftBeer {
  brand?: string;
  [propNmae: string]: any;
}
```

##### 함수 타입

- 인터페이스는 함수의 타입을 정의할 때에도 사용할 수 있다.

```typescript
interface login {
  (username: string, password: string): boolean;
}
```

- 함수의 인자의 타입과 반환 값의 타입을 정합니다.

```typescript
let loginUser: login;
loginUser = function (id: string, pw: string) {
  return true;
};
```

##### 클래스 타입

- C#이나 자바처럼 클래스가 일정 조건을 만족하도록 타입 규칙을 정할 수 있다.

```typescript
interface CraftBeer {
  beerName: string;
  nameBeer(beer: string): void;
}

class myBeer implements CraftBeer {
  beerName: string = "Baby Guinness";
  nameBeer(b: string) {
    this.beerName = b;
  }
  constructor() {}
}
```

##### 인터페이스 확장

- 클래스와 마찬가지로 인터페이스도 인터페이스 간 확장이 가능하다.

```typescript
interface Person {
  name: string;
}
interface Drinker {
  drink: string;
}
interface Developer extends Person, Drinker {
  skill: string;
}
let fe = {} as Developer;
fe.name = "josh";
fe.skill = "TypeScript";
fe.drink = "Beer";
```

##### 하이브리드 타입

- 자바스크립트의 유연하고 동적인 타입 특성에 따라 인터페이스 역시 여러 가지 타입을 조합하여 만들 수 있다.

```typescript
interface CraftBeer {
  (beer: string): string;
  brand: string;
  brew(): void;
}

function myBeer(): CraftBeer {
  let my = function (beer: string) {} as CraftBeer;
  my.brand = "Beer Kitchen";
  my.brew = function () {};
  return my;
}

let brewedBeer = myBeer();
brewedBeer("My First Beer");
brewedBeer.brand = "Pangyo Craft";
brewedBeer.brew();
```
