#### tutorial
```
1. typescript handbook - https://typescript-kr.github.io/
2. ts for jsdev - https://ahnheejong.gitbook.io/ts-for-jsdev/
```

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


#### [제네릭 (generic)]()
```typescript
function identity(arg: number): number {
    return arg;
}

function identity(arg: any): any {
    return arg;
}
any를 사용하는 것은 함수가 arg에 대한 모든 타입을 전달 받을 수 있게되지만 
실제로 함수가 반환할 떄 그 타입이 무엇이었는지에 대한 정보를 잃어버리게 된다.

타입변수(type variable)를 사용하여 어떤 타입이 반환될 것인지를 나타낼 수 있다. 
function identity<T>(arg: T): T {
    return arg;
}
identity 함수에 타입변수 T를 추가한 모습이다.
이 T는 함수 사용자가 제공한 타입을 캡처하여 나중에 해당 정보를 사용할 수 있도록 한다.
이를 제네릭 함수라고 한다.

제네릭함수를 호출하는 방법은 두가지가 있다.
1. 타입 인수를 포함한 모든 인수를 함수에 전달하는 것
let output = identity<string>("myString");  // 반환 타입은 'string' 입니다.
T를 string으로 명시했으며 인수에 () 대신 <>를 사용했다.

2. 타입 인수 추론(type argument inference)을 사용한다(더 일반적인 방법)
let output = identity("myString");  // 반환 타입은 'string' 입니다.
<> 안에 명시적으로 타입을 전달할 필요가 없다.
컴파일러는 그저 "myString" 의 값을 보고 T를 그 타입으로 설정한다.
컴파일러가 타입을 추론하지 못하면 1번의 예제처럼 타입 인수를 명시적으로 전달해야 할 수도 있다.


제네릭 함수에서 약간의 문제가 있다.
function loggingIdentity<T>(arg: T): T {
    console.log(arg.length);  // 오류 : T는 .length 메소드를 가지고 있지 않습니다.
    return arg;
}
컴파일러는 arg의 .length 멤버를 사용하고 있다는 오류를 주지만 arg 모듈에는 이 멤버가 없다고 할 수는 없다.
실제로 이 함수가 T 대신 T 배열을 처리한다고 가정한다면 아래와 같이 해결할 수 있다.

function loggingIdentity<T>(arg: T[]): T[] {
    console.log(arg.length);  // Array는 .length 멤버가 있습니다. 오류 없음.
    return arg;
}

아래처럼 해결도 가능하다.
interface Lengthwise {
    length: number;
}

function loggingIdentity<T extends Lengthwise>(arg: T): T {
    console.log(arg.length);  // 이제 .length 프로퍼티가 있으므로 더이상 오류가 없습니다.
    return arg;
}

대신 모든 필수 프로퍼티가 있는 타입의 값을 전달해야 한다.
loggingIdentity({length: 10, value: 3});
```


#### [제네릭 제약조건에서 타입 매개변수 사용 - using type parameters in generi constaraints]
```typescript
다른 타입 매개 변수에 의해 제한되는 타입 매개 변수를 선언할 수 있다.
예를 뜰어 여기서는 일므을 가진 객체의 프로퍼티를 가져오려고 한다.
실수로 obj에 존재하지 않는 프로퍼티를 잡아내지 않도록 하고자 한다.
그래서 두가지 타입 사이에 제약조건을 적용한 것이 아래의 코드다.
function getProperty<T, K extends keyof T>(obj: T, key: K) {
    return obj[key];
}

let x = { a: 1, b: 2, c: 3, d: 4 };

getProperty(x, "a"); // 오류 없음
getProperty(x, "m"); // 오류 : 타입 'm'의 인수를 'a' | 'b' | 'c' | 'd' 에 할당 할 수 없습니다.
```


#### [열거형](https://typescript-kr.github.io/pages/Enums.html)
```typescript
열거형을 사용하면 이름이 있는 상수들을 정의할 수 있다.
열거형의 사용은 문서의 의도나 명확한 사례들을 쉽게 만들 수 있다.

1.숫자 열거형
enum Direction {
    Up = 1,
    Down,
    Left,
    Right,
}
Down 부터 2, 3, 4가 적용된다.

2. 문자 열거형
문자 열거형에서 각 멤버는 모두 초기화가 되어야 한다.
enum Direction {
    Up = "UP",
    Down = "DOWN",
    Left = "LEFT",
    Right = "RIGHT",
}
문자 열거형은 자동 증가 동작을 하지 않지만 직렬화 하는 이점이 있다.
문자 열거형을 사용하면 열거형 멤버 자체의 이름과 독립적으로 코드가 실행될 때 의미있고 읽기 쉬운 값을 제공한다.
ㅁㄴ
```


#### [유니온 타입](https://ahnheejong.gitbook.io/ts-for-jsdev/03-basic-grammar/union-type)
```typescript
아래의 경우는 인자에 따라 결과 값이 달라진다.
function square(value: number, returnString: boolean = false): ??? {
  const squared = value * value;
  if (returnString) {
    return squared.toString();
  }
  return squared;
}

오버로딩으로 해결할 수 있지만, 이는 바람직하지 않다.
아래와 같이 유니온 타입으로 해결할 수 있다.
function square(value: number, returnString: boolean = false): string | number {
  /* 본문 동일 */
}
const stringOrNumber: string | number = square(randomNumber, randomBoolean);
유니온 타입은 파이프 기호(|)로 이어서 표현한다.

타입 별칭 문법을 사용해 유니온 타입에 이름을 붙일 수 있다.
type SquaredType = string | number;
function square(value: number, returnOnString: boolean = false): SquaredType {
  /* 본문 동일 */
}



```


#### [인터섹션 타입](https://ahnheejong.gitbook.io/ts-for-jsdev/03-basic-grammar/intersection-type)
```typescript
이미 존재하는 여러 타입을 모두 만족하는 타입을 표현하기 위한 수단이다.

type Programmer = { favoriteLanguage: string };
const programmer: Programmer = { favoriteLanguage: 'TypeScript' };

type BeerLover = { favoriteBeer: string };
const beerLover: BeerLover = { favoriteBeer: 'Imperial Stout' };
이렇게 프로그래머와 맥주 선호에 관한 타입이 있다.
이 두개를 함께 나타내기 위해서는

type BeerLovingProgrammer = { favoriteLanguage: string; favoriteBeer: string; };
const AhnHeejong: BeerLovingProgrammer = { 
  favoriteLanguage: 'TypeScript',
  favoriteBeer: 'Imperial Stout',
};
위와 같은 방법이 있을수 있지만, 유지보수 차원에서 좋지 않다.

이럴때 앰퍼샌드(&) 기호를 통해 인터섹션 타입을 사용하면 된다.
type BeerLovingProgrammer = Programmar & BeerLover;

단 모두를 만족해야한다.
```

#### [typescript 와 redux - 쉬운 예제 ](https://velog.io/@yesdoing/TypeScript-with-React-Redux-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-k5jsis62ah)


#### [type과 interface의 차이](https://medium.com/@alexsung/typescript-type%EA%B3%BC-interface-%EC%B0%A8%EC%9D%B4-86666e3e90c)
```
1. interface는 여러곳에서 사용되는 이름을 만든다는 점이 다르다.
type은 새로운 이름을 만들지 않는다.

2. type은 extend되거나 implement 될 수 없다.
소프트웨어의 이상적인 속성이 확장에 용이하다는 것이기 때문에 가능하다면 언제나 type 보다 interface를 이용해야 한다.
```


#### [typescript + redux-saga + immutable + reselect project](https://github.com/nearform/react-redux-typescript-saga-immutable)


#### [typescrit + nextjs](https://medium.com/@miiny/setup-a-server-rendered-reactjs-application-with-next-js-typescript-sass-7cd3e7e79706)

#### [typescrit + nextjs - starter kit](https://github.com/deptno/next.js-typescript-starter-kit)

#### [typescript + nextjs - next-typescript plugin](https://github.com/zeit/next-plugins/tree/master/packages/next-typescript)
```javascript
1. npm install --save @zeit/next-typescript

2. Create a next.config.js in your project
// next.config.js
const withTypescript = require('@zeit/next-typescript')
module.exports = withTypescript({
  /* config options here */
})

3. Create a .babelrc in your project
{
  "presets": [
    "next/babel",
    "@zeit/next-typescript/babel"
  ]
}

4. Create a tsconfig.json in your project
{
    "compilerOptions": {
      "module": "esnext",
      "target": "esnext",
      "jsx": "preserve",
      "sourceMap": false,
      "moduleResolution": "node"
    },
    "exclude": [
      "out",
      ".next"
    ]
}
```


#### 부모 컴포넌트로부터 함수를 props로 받아올 경우
```typescript
type OwnProps = {
	user: UserType | null;
	login(email: string, password: string): LoginType;
	logout(): LogoutType;
};

이런식으로 선언해야한다.
```