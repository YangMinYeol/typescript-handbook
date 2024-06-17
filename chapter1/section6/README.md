# 클래스(Class)

##### readonly

- `readonly` 키워드를 사용하면 읽기만 가능하며 쓰기는 불가능하다.

##### Accessor

- name 속성에 제약 사항을 추가하고 싶다면 아래와 같이 get과 set을 활용한다.
- get만 선언하고 set을 선언하지 않는 경우에는 자동으로 `readonly`로 인식된다.

```typescript
class Developer {
  private name: string;

  get name(): string {
    return this.name;
  }

  set name(newValue: string) {
    if (newValue && newValue.length > 5) {
      throw new Error("이름이 너무 깁니다");
    }
    this.name = newValue;
  }
}
const josh = new Developer();
josh.name = "Josh Bolton"; // Error
josh.name = "Josh";
```

###### Abstract Class

- 추상 클래스는 특정 클래스의 상속 대상이 되는 클래스이며 좀 더 상위 레벨에서 속성, 메서드의 모양을 정의한다.

```typescript
abstract class Developer {
  abstract coding(): void; // 'abstract'가 붙으면 상속 받은 클래스에서 무조건 구현해야 함
  drink(): void {
    console.log("drink sth");
  }
}

class FrontEndDeveloper extends Developer {
  coding(): void {
    // Developer 클래스를 상속 받은 클래스에서 무조건 정의해야 하는 메서드
    console.log("develop web");
  }
  design(): void {
    console.log("design web");
  }
}
const dev = new Developer(); // error: cannot create an instance of an abstract class
const josh = new FrontEndDeveloper();
josh.coding(); // develop web
josh.drink(); // drink sth
josh.design(); // design web
```
