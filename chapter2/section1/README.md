# Usage

## 모듈

- 모듈은 전역변수와 구분되는 자체 유효 범위를 가지며 `export`, `import`와 같은 키워드를 사용하지 않으면 다른 파일에서 접근할 수 없다.
- `tsconfig.json` 파일에 설정한 컴파일러 모드에 따라 모듈 코드가 각기 다르게 변환된다.

```typescript
// math.ts
export interface Triangle {
  width: number;
  height: number;
}

// index.ts
import { Triangle } from "./math.ts";
```

## 타입스크립트 선언 파일

- 타입스크립트 선언 파일 `d.ts`는 타입스크립트 코드의 타입 추론을 돕는 파일이다.
- ex: 전역변수로 선언한 변수를 특정 파일에서 `import`구문 없이 사용하는 경우 해당 변수를 인식하지 못한다. 그럴때 아래와 같이 해당 변수를 선언해서 에러가 나지 않게 할 수 있다.

```typescript
declare const global = "sth";
```

## 인덱싱

- 타입스크립트에서는 인터페이스를 이용하여 아래와 같이 인덱싱 타입을 정의할 수 있다.

```typescript
interface StringArray {
  [index: number]: string;
}

const arr: StringArray = ["Thor", "Hulk"];
```

## 유틸리티 타입

- 유틸리티 타입은 이미 정의해 놓은 타입을 변환할 때 사용하기 좋은 타입 문법이다.

##### Partial

- 파셜 타입은 특정 타입의 부분 집합을 만족하는 타입을 정의할 수 있다.

```typescript
interface Address {
  email: string;
  address: string;
}

type MayHaveEmail = Partial<Address>;
const me: MayHaveEmail = {}; // 가능
const you: MayHaveEmail = { email: "test@abc.com" }; // 가능
const all: MayHaveEmail = { email: "capt@hero.com", address: "Pangyo" }; // 가능
```

##### Pick

- 픽 타입은 특정 타입에서 몇개의 속성을 선택하여 타입을 정의할 수 있다.

##### Omit

- 오밋 타입은 특정 타입에서 지정된 속성만 제거한 타입을 정의해준다.

```typescript
interface AddressBook {
  name: string;
  phone: number;
  address: string;
  company: string;
}
const phoneBook: Omit<AddressBook, "address"> = {
  name: "재택근무",
  phone: 12342223333,
  company: "내 방",
};
const chingtao: Omit<AddressBook, "address" | "company"> = {
  name: "중국집",
  phone: 44455557777,
};
```

## 맵드 타입

- 맵드 타입이란 기존에 정의되어 있는 타입을 새로운 타입으로 변환해 주는 문법을 의미한다.
- 자바스크립트 `map()` API 함수를 타입에 적용한 것과 같은 효과를 가진다.

##### 맵드 타입의 기본 문법

- `[P in K]`는 마치 자바스크립트의 `for in` 문법과 유사하게 동작한다.

```typescript
{ [ P in K ] : T }
{ [ P in K ]? : T }
{ readonly [ P in K ] : T }
{ readonly [ P in K ]? : T }
```

##### 맵드 타입 기본 예제

```typescript
type HeroProfiles = { [K in Heroes]: number };
const heroInfo: HeroProfiles = {
  Hulk: 54,
  Thor: 1000,
  Capt: 33,
};
```
