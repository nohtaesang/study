##### [두 배열을 비교하여 추가된 것, 삭제된 것, 변하지 않은것 찾기]
```javascript
const compareBase = (markets, copyMarkets) => {
	let added = [],
		deleted = [],
		unChanged = [];

	const before = markets.reduce((acc, market) => acc.concat(market.base), []);
	const after = copyMarkets.reduce((acc, market) => acc.concat(market.base), []);
	before.map((b, i) => {
		const idx = after.findIndex((a) => a === b);
		if (idx !== -1) {
			unChanged.push(after.splice(idx, 1)[0]);
		} else {
			deleted.push(b);
		}
	});
	added = after.slice();
	console.log(added, deleted, unChanged);
};
```

#### object에 특정 속성만 교체하고 싶을 때
```javascript
const obj ={a:1, b:2, c:3}
const newObj = {...obj, c:4} // newObj: a:1, b:2, c:4

const temp = {b:1, c:1}
const newObj2 = {...obj, ...temp} // newObj2: a:1, b:1, c:1
```

#### [new Date(date) 에서 date가 문자열이면 안된다.]()
```javascript
new Date('1558421237881') // Invalid Date
```
#### [object로 array의 map 사용하기 - Object.entries() 를 사용하여](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)
```javascript
{Object.entries(tokenList).map((token, i) => <Item key={i} type="tokenList" token={token[1]} />)}
```
#### [object 복사하기] (https://velog.io/@ddalpange/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EA%B0%9D%EC%B2%B4-%EB%B3%B5%EC%82%AC%ED%95%98%EA%B8%B0)
```javascript
1. Object.assign() (얕은복사)
2. JSON.PARSE(JSON.stringify()) (깊은복사) 느리다
3. 재귀 사용 (깊은복사)
4. Immutable.js 사용 (깊은복사)
5. Spread 문법 사용 (얕은복사)

immutable js 를 왜 사용하려는지 알겠다.
```

#### [이벤트 버블링, 이벤트 캡처 그리고 이벤트 위임까지](https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/)

#### [엔진, 런타임, 콜스택 개관](https://engineering.huiseoul.com/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%9E%91%EB%8F%99%ED%95%98%EB%8A%94%EA%B0%80-%EC%97%94%EC%A7%84-%EB%9F%B0%ED%83%80%EC%9E%84-%EC%BD%9C%EC%8A%A4%ED%83%9D-%EA%B0%9C%EA%B4%80-ea47917c8442)

#### [v8 엔진 내부](https://engineering.huiseoul.com/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%9E%91%EB%8F%99%ED%95%98%EB%8A%94%EA%B0%80-v8-%EC%97%94%EC%A7%84%EC%9D%98-%EB%82%B4%EB%B6%80-%EC%B5%9C%EC%A0%81%ED%99%94%EB%90%9C-%EC%BD%94%EB%93%9C%EB%A5%BC-%EC%9E%91%EC%84%B1%EC%9D%84-%EC%9C%84%ED%95%9C-%EB%8B%A4%EC%84%AF-%EA%B0%80%EC%A7%80-%ED%8C%81-6c6f9832c1d9)


#### [메모리 누수 대처법](https://engineering.huiseoul.com/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%9E%91%EB%8F%99%ED%95%98%EB%8A%94%EA%B0%80-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EA%B4%80%EB%A6%AC-4%EA%B0%80%EC%A7%80-%ED%9D%94%ED%95%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EB%88%84%EC%88%98-%EB%8C%80%EC%B2%98%EB%B2%95-5b0d217d788d)


#### [sync await 과 이벤트 루프](https://engineering.huiseoul.com/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%9E%91%EB%8F%99%ED%95%98%EB%8A%94%EA%B0%80-%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EB%A3%A8%ED%94%84%EC%99%80-%EB%B9%84%EB%8F%99%EA%B8%B0-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%EC%9D%98-%EB%B6%80%EC%83%81-async-await%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EC%BD%94%EB%94%A9-%ED%8C%81-%EB%8B%A4%EC%84%AF-%EA%B0%80%EC%A7%80-df65ffb4e7e)


#### [화살표함수와 this (arrow function and this)](https://poiemaweb.com/es6-arrow-function)
```javascript
let deck = {
    suits: ["hearts", "spades", "clubs", "diamonds"],
    cards: Array(52),
    createCardPicker: function() {
        return function() {
            let pickedCard = Math.floor(Math.random() * 52);
            let pickedSuit = Math.floor(pickedCard / 13);

            return {suit: this.suits[pickedSuit], card: pickedCard % 13}; // this ===window
        }
    }
}

let cardPicker = deck.createCardPicker();
let pickedCard = cardPicker();

alert("card: " + pickedCard.card + " of " + pickedCard.suit);


아래처럼 화살표 함수를 사용하면 this를 캡처할 수 있다.
let deck = {
    suits: ["hearts", "spades", "clubs", "diamonds"],
    cards: Array(52),
    createCardPicker: function() {
        // 주의: 아래 줄은 이제 화살표 함수입니다. 여기에서 'this'를 캡처할 수 있습니다.
        return () => {
            let pickedCard = Math.floor(Math.random() * 52);
            let pickedSuit = Math.floor(pickedCard / 13);

            return {suit: this.suits[pickedSuit], card: pickedCard % 13};
        }
    }
}

let cardPicker = deck.createCardPicker();
let pickedCard = cardPicker();

alert("card: " + pickedCard.card + " of " + pickedCard.suit);
```


#### [화살표 함수를 사용하면 안되는 경우](https://poiemaweb.com/es6-arrow-function#4-%ED%99%94%EC%82%B4%ED%91%9C-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%B4%EC%84%9C%EB%8A%94-%EC%95%88%EB%90%98%EB%8A%94-%EA%B2%BD%EC%9A%B0)
```javascript
1. 메소드는 축약 메소드 표현으로
// Bad
const person = {
  name: 'Lee',
  sayHi: () => console.log(`Hi ${this.name}`)
};

person.sayHi(); // Hi undefined

// Good
const person = {
  name: 'Lee',
  sayHi() { // === sayHi: function() {
    console.log(`Hi ${this.name}`);
  }
};

person.sayHi(); // Hi Lee

2. prototype에 메소드를 할당할 경우 사용하면 안된다.
// Bad
const person = {
  name: 'Lee',
};

Object.prototype.sayHi = () => console.log(`Hi ${this.name}`);

person.sayHi(); // Hi undefined

// Good
const person = {
  name: 'Lee',
};

Object.prototype.sayHi = function() {
  console.log(`Hi ${this.name}`);
};

person.sayHi(); // Hi Lee

3. addEventListener 함수의 콜백함수
// Bad
var button = document.getElementById('myButton');

button.addEventListener('click', () => {
  console.log(this === window); // => true
  this.innerHTML = 'Clicked button';
});

// Good
var button = document.getElementById('myButton');

button.addEventListener('click', function() {
  console.log(this === button); // => true
  this.innerHTML = 'Clicked button';
});
```

#### [내부함수의 this가 window를 가리키는 것을 회피하는 방법](https://poiemaweb.com/js-this)
```javascript
1. 내부함수에서 that을 이용하여 this를 캡처한다.

var value = 1;

var obj = {
  value: 100,
  foo: function() {
    var that = this;  // Workaround : this === obj

    console.log("foo's this: ",  this);  // obj
    console.log("foo's this.value: ",  this.value); // 100
    function bar() {
      console.log("bar's this: ",  this); // window
      console.log("bar's this.value: ", this.value); // 1

      console.log("bar's that: ",  that); // obj
      console.log("bar's that.value: ", that.value); // 100
    }
    bar();
  }
};

obj.foo();


```


#### [화살표함수가 일반함수와 다른 점 - this에 대하여](https://egghead.io/lessons/javascript-capture-this-with-an-arrow-function)
```
Arrow functions are not only syntactically different from other JavaScript functions.
but they also have special this behavior
An arrow function doesn't have its own this. 
Instead, it uses the this value from its enclosing execution context.
화살표 함수는 자바스크립트의 함수와 다르지 않다.
그러나 this에 대한 작용은 다르다.
화살표함수는 자신의 this를 가지고 있지 않는다.!!!
대신에 실행 컨텍스트에서의 this를 사용한다.

When an arrow function is created, it permanently captures the surrounding this value. 
Neither call() nor apply() can change the this value later. 
Additionally, arrow functions cannot be used as constructors.
화살표 함수가 생성될 때, this 를 영구히 캡쳐한다.
call이나 apply로도 그 값을 변경할 수 없다.
추가적으로 화살표함수는 생성자 함수로 쓰일 수 없다.
```

