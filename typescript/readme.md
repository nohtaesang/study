#### [5분안에 보는 타입스크립트](https://typescript-kr.github.io/pages/tutorials/TypeScript%20in%205%20minutes.html)
```typescript
Type annotations
- 함수 또는 변수의 의도된 계약을 적는 것인다.
- 잘못된 형태로 함수 또는 변수를 사용하면 오류가 표시된다.
- 하지만 컴파일은 정상적으로 된다.

Interface와 Class를 사용할 수 있다.
class Student {
	fullName: string;
	constructor(public firstName: string, public middleInitial: string, public lastName: string) {
		this.fullName = firstName + ' ' + middleInitial + ' ' + lastName;
	}
}

interface Person {
	firstName: string;
	lastName: string;
}

function greeter(person: Person) {
	return 'Hello, ' + person.firstName + ' ' + person.lastName;
}

let user = new Student('Noh', 'Kirin', 'TaeSang');
document.body.innerHTML = greeter(user);
```
#### [리엑트 + 웹팩 설정](https://typescript-kr.github.io/pages/tutorials/React%20&%20Webpack.html)
```
1.webpack 글로벌 설치
npm install -g webpack

2. react, react-dom 의존성 추가
npm install --save react react-dom @types/react @types/react-dom
- @types/ 접두사는 react와 react-dom을 위한 선언 파일을 가져온다는 것을 의미한다.

3. awesome-typescript-loader 와 source-map-loader에 development-time 의존성 추가
npm install --save-dev typescript awesome-typescript-loader source-map-loader

- awesome-typescript-loader는 webpack이 tsconfig.json을 사용하여 typescript 코드를 컴파일 하는데 도움이 된다. 
(ts-loader를 사용할 수도 있다.)

- source-map-loader는 typescript의 모든 소스 맵 출력을 사용하여 자체소스 맵을 생성 할 때 webpack에 알린다.
이렇게하면 원래 typescript 소스 코드를 디버깅 하듯이 최종 출력 파일을 디버깅할 수 있다.

4. typescript 설정 파일 추가
{
    "compilerOptions": {
        "outDir": "./dist/",
        "sourceMap": true,
        "noImplicitAny": true,
        "module": "commonjs",
        "target": "es5",
        "jsx": "react"
    },
    "include": [
        "./src/**/*"
    ]
}

```

#### --strictNullChecks 를 사용하면, null 과 undefined는 void 와 그 각각의 타입에만 할당할 수 있다.
```
strickNullChecks 검사를 사용하도록 권장한다.

string 또는 null 또는 undefined중 하나를 전달하고자 하는 경우
string | null | undefined (Union 타입) 을 사용할 수도 있다.
```

#### [type assertion 예시](https://hyunseob.github.io/2017/12/12/typescript-type-inteference-and-type-assertion/)
```typescript
class Character {
  hp: number;
  runAway() {
    /* ... */
  }
  isWizard() {
    /* ... */
  }
  isWarrior() {
    /* ... */
  }
}

class Wizard extends Character {
  fireBall() {
    /* ... */
  }
}

class Warrior extends Character {
  attack() {
    /* ... */
  }
}


위의 코드가 있을 때,

function battle(character: Character) {
  if (character.isWizard()) {
    character.fireBall(); // Property 'fireBall' does not exist on type 'Character'.
  } else if (character.isWarrior()) {
    character.attack(); // Property 'attack' does not exist on type 'Character'.
  } else {
    character.runAway();
  }
}
이 코드는 에러가 난다.
character에 fireBall() 메소드가 없기 때문이다.
하지만 우리는 character.isWizard() 가 true 이면 fireBall() 메소드가 확실히 있을것을 알고 있다.
이 경우에 아래와 같이 타입 단언(as)을 사용하면 된다.

function battle(character: Character) {
  if (character.isWizard()) {
    (character as Wizard).fireBall(); // Pass
  } else if (character.isWarrior()) {
    (character as Warrior).attack(); // Pass
  } else {
    character.runAway();
  }
}

이 문제는 타입 가드(Type Guard)를 통해 해결 가능하다.
class Character {
  isWizard(): this is Wizard {
    return this instanceof Wizard;
  }
  isWarrior(): this is Warrior {
    return this instanceof Warrior;
  }
}
타입 가드는 런타임에서의 타입 체크를 컴파일러에게 알려주는 기능이다.

타입스크립트를 사용하기로 마음 먹었다면 as와 any는 가능한 적게 사용하는 것이 좋다.
물론 아예 사용하지 않기는 어렵다.

타입 단언은 타입 캐스팅이 아니다.
타입 단언은 타입을 변경한다는 사실 때문에 타입 캐스팅과 비슷하게 느껴질 
수 있다.
타입 단언이 타입 캐스팅이라 불리지 않는 이유는 런타임에 영향을 미치지 않기 때문이다.
타입 캐스팅은 컴파일 타임과 런타임에서 모두 타입을 변경시키지만
타입 단언은 오직 컴파일 타임에서만 타입을 변경시킨다.


```

#### 배열 비구조화로 타입 지정이 가능하다
```typescript
function f([first, second]:[number, number]){
   
}
```

#### 객체 비구조화
```typescript
1. 프로터티의 이름을 바꿔서 불러올 수 있다.
const o ={
    a: 1,
    b: 'hello'
}

let {a: newName1, b:newName2} = o;

2. 위에서의 콜론은 타입을 나타내는 것이 아니다.
형식을 지정하는 경우 전체 형식이 비구조화된 후에도 형식을 작성해야 한다.

let {a, b} : {a: number, b: string} = o;

```

#### 기본값을 사용하여 프로퍼티가 정의되지 않은 경우 기본값 지정하기
```typescript
function f(obj: {a: number, b?: string}){
    let {a, b = 1001} = obj
}
```

#### interface를 사용하는 간단한 예제
```typescript
function printLabel(labelledObj: { label: string }) {
  console.log(labelledObj.label);
}

printLabel을 호출하기 위해서는 단일 매개변수가 필요하다.
이는 문자열 타입 label 프로퍼티를 가진다.
위의 코드를 인터페이스를 사용하여 아래처럼 바꿀 수 있다.

interface LabelledValue {
  label: string;
}

function printLabel(labelledObj: LabelledValue) {
  console.log(labelledObj.label);
}

인터페이스 labelledValue는 이전 코드의 요구사항을 설명하는 데 사용할 수 있는 이름이다.
```



#### [함수와 인터페이스](https://poiemaweb.com/typescript-interface)
```typescript
인터페이스는 함수의 타입으로 사용할 수 있다.
이때 함수의 인터페이스에는 타입이 선언된 파라미터 리스트와 리턴 타입을 정의한다.

interface SquareFunc {
  (num: number): number;
}

// 함수 인테페이스를 구현하는 함수는 인터페이스를 준수하여야 한다.
const squareFunc: SquareFunc = function (num: number) {
  return num * num;
}
```


#### 선택적 프로퍼티
```typescript

인터페이스의 프로퍼티는 반드시 구현되어야 한다.
하지만 선택적 프로퍼티를 사용하면 생략하여도 에러가 발생하지 않는다.

interface UserInfo {
  username: string;
  password: string;
  age?    : number;
  address?: string;
}

const userInfo: UserInfo = {
  username: 'ungmo2@gmail.com',
  password: '123456'
}

console.log(userInfo);

선택적 프로퍼티를 가진 인터페이스는 선언된 프로퍼티 이름 끝에 ? 로 표시된다.
선택적 프로퍼티의 장점은 사용 가능한 프로퍼티를 설명하는 동시에 인터페이스에
포함되지 않은 프로퍼티의 사용을 방지할 수 있다는 것이다.
```


#### [덕 타이핑 (duck typing) 또는 구조적 타이핑 (structural typing)](https://poiemaweb.com/typescript-interface)
```typescript
Typescript는 해당 인터페이스에서 정의한 프로퍼티나 메소드를 가지고 있다면 그 인터페이스를 구현한 것으로 인정한다.
함수와 변수 모두 해당된다.

interface IPerson {
  name: string;
}

function sayHello(person: IPerson): void {
  console.log(`Hello ${person.name}`);
}

const me = { name: 'Lee', age: 18 };
sayHello(me); // Hello Lee

```


#### readonly와 const
```
변수는 const를 사용하고 프로퍼티는 readonly를 사용한다.
```


#### [색인 가능 타입 (indexable type)](https://ahnheejong.gitbook.io/ts-for-jsdev/04-interface-and-class/indexable-types)
```typescript
색인에 접근할 때 사용하는 기호인 대괄호를 이용해 객체의 색인 시그니쳐를 적어줘야 한다.

interface NameHeightMap {
  [userName: string]: number | undefined;
}

위는 이렇게 해석될 수 있다.
NameHeightMap 타입의 값을
임의의 string 타입 값 userName으로 색인한 값
즉 nameHeightMap[userName] 은 number 또는 undefined 타입의 값이다.

색인의 타입으로는 문자열 또는 숫자만 사용 가능하다.

```


#### class inheritance (상속)
```typescript
class Animal {
    name: string;
    constructor(theName: string) { this.name = theName; }
    move(distanceInMeters: number = 0) {
        console.log(`${this.name} moved ${distanceInMeters}m.`);
    }
}

class Snake extends Animal {
    constructor(name: string) { super(name); }
    move(distanceInMeters = 5) {
        console.log("Slithering...");
        super.move(distanceInMeters);
    }
}

파생 클래스가 기본 클래스의 생성자를 실행할 super()를 호출해야 한다.
게다가 생성자 내에서 this에 있는 프로퍼티에 접근하기 전에 항상 super() 를 호출해야 한다.
이것은 typescript가 적용할 중요한 규칙이다.


```

#### 접근자 (accessors)
```typescript
typescript는 객체의 멤버에 대한 접근을 인터셉트하는 방법으로 getters/setters를 지원한다.

let passcode = "secret passcode";

class Employee {
    private _fullName: string;

    get fullName(): string {
        return this._fullName;
    }

    set fullName(newName: string) {
        if (passcode && passcode == "secret passcode") {
            this._fullName = newName;
        }
        else {
            console.log("오류 : employee의 무단 업데이트!");
        }
    }
}

let employee = new Employee();
employee.fullName = "Bob Smith";
if (employee.fullName) {
    console.log(employee.fullName);
}

passcode 를 사용하여 set에 대한 권한을 설정할 수 있다.
이는 무단으로 값을 수정하는 것을 방지하는 방법이다.

```

#### 추상 클래스 (abstract classes)
```typescript
추상 클래스는 다른 클래스가 파생될 수 있는 기본 클래스이다.
추상 클래스는 직접적으로 인스턴스화할 수 없다.
인터페이스와 달리 추상 클래스는 클래스의 멤버에 대한 구현 세부 정보를 포함할 수 있다.


abstract 키워드는 추상 클래스뿐만 아니라 추상 클래스 내의 추상 메서드를 정의하는데 사용할 수 있다.
이는 파생된 클래스에서 구현해야 한다.
abstract class Animal {
    abstract makeSound(): void;
    move(): void {
        console.log("roaming the earth...");
    }
}


예시
abstract class Department {

    constructor(public name: string) {
    }

    printName(): void {
        console.log("Department name: " + this.name);
    }

    abstract printMeeting(): void; // 파생된 클래스에서 구현해야 합니다.
}

class AccountingDepartment extends Department {

    constructor() {
        super("Accounting and Auditing"); // 파생된 클래스의 생성자는 super()를 호출해야합니다.
    }

    printMeeting(): void {
        console.log("The Accounting Department meets each Monday at 10am.");
    }

    generateReports(): void {
        console.log("Generating accounting reports...");
    }
}

let department: Department; // 좋아요: abstract 타입에 대한 참조를 만듭니다.
department = new Department(); // 오류: 추상 클래스의 인스턴스를 생성할 수 없습니다.
department = new AccountingDepartment(); // 좋아요: 추상적이지 않은 하위 클래스를 생성하고 할당합니다.
department.printName();
department.printMeeting();
department.generateReports(); // 오류: abstract 타입으로 선언된 메서드가 존재하지 않습니다.


```


#### 나머지 매개변수 (rest parameters)
```typescript
function buildName(firstName: string, ...restOfName: string[]) {
    return firstName + " " + restOfName.join(" ");
}

let employeeName = buildName("Joseph", "Samuel", "Lucas", "MacKinzie");
```