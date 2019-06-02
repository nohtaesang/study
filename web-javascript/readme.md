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