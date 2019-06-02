#### [ socket 과 같이 구독(?) 서비스로 이벤트 제어하기 - toastify.js 를 참고](https://github.com/fkhadra/react-toastify) 
```javascript
const eventManager = {
	list: new Map(),

	on(event, callback) {
		this.list.has(event) || this.list.set(event, []);
		this.list.get(event).push(callback);
		return this;
	},
	off(event) {
		this.list.delete(event);
		return this;
	},
	emit(event, ...args) {
		this.list.has(event) &&
			this.list.get(event).forEach((callback) =>
				setTimeout(() => {
					callback(...args);
				}, 0)
			);
	}
};

export default eventManager;

```
#### DB사용을 최소한으로
```javascript
현재 Market을 수정하는 작업을 하고 있다.
(base 마켓 등록, base 마켓간의 순서 조정, base 마켓마다 trade 마켓들 등록 및 순서 수정)
마켓을 등록하는 query, 마켓 순서를 바꾸는 query, 마켓마다 trade 배열을 수정하는 query가 있다.
사용자가 할 수 있는 행동으로는
1. base 등록
2. base 삭제
3. base 순서 변경
4. trade 등록
이 행동들이 일어날 때 마다 query를 날리는 방법으로 코드를 짰었다.
생각할수록 비효율적이라고 생각이 들었다.

결론만 말하자면, 원본 market을 DB에서 가져와 copy본을 만들었다.
그 후 프론트에서는 copy만 조작한다.
save 버튼을 누르면 원본과 copy본을 비교하여 query를 날린다.

앞으로도 원본과 copy본을 나누어 DB 사용을 최소화하는 방법으로 설계를 할 것 같다.


* 결론
1. 원본을 COPY 하여 COPY를 조작한 후 한번에 변경 사항을 적용하는 방법이 있다.
2. CRUD를 효율적으로 사용할 수 있도록 설계하자

```

#### 배열을 원하는 객체로 변환하여 map 자료구조처럼 사용하기
```javascript
tokenList는 배열로서 prCode 프로퍼티를 가지고 있다.
tokenList의 순서와 prCode 는 무관한 상태이다.
원하는 prCode의 token을 가져오기 위해서는 tokenList를 순회해서 prCode를 찾아야 하는 상황.
이 문제를 해결하기 위해서 아래와 같은 방법을 사용했다.


const res = yield initWeb3();
const { tokenList } = res;
const nextTokenList = {};
tokenList.forEach((token) => {
	nextTokenList[token.prCode] = token;
});

key: prCode, value: token 인 객체 만들기

이러면 생기는 문제점은, array 에서 object가 되므로 map, filter와 같은 배열 함수를 사용할 수 없다.

이를 해결하기 위해 tokenList.values() 를 사용하여 순회 가능한 배열을 얻어 사용하였다.

{Object.values(tokenList).map((token, i) => <Item key={i} type="tokenList" token={token} />)}
```
#### setTimeout으로 toast 구현
```javascript
toast를 구현하고 싶었다.
queue를 사용하면 간단하게 해결할 수 있을 것 같았다.
그러나 문제가 생겼다.
setTimeout 을 통해 toast의 제한 시간을 걸어두었는데, 
걸어두는 시점에서의 queue의 상태와
제한 시간 이후의 시점에서의 queue의 상태가 다르다는 것이다.

그 이유는 setTimeout으로 특정 함수를 실행시키면, closure가 형성되어 그 시점의
정보를 기억하기 때문이다.

const timer = setTimeout(() => {
	popToastExcuteQueue(id);
}, 2000);

const popToastExcuteQueue = (id) => {
	const nextToastExcuteQueue = Object.assign({}, toastExcuteQueue);
	delete nextToastExcuteQueue[id];
	setToastExcuteQueue(nextToastExcuteQueue);
};

예를 들어 2초가 지나기 전에 3번의 toast를 호출했다고 치자.
처음 2초가 지나면 Object.assign({}, toastExcuteQueue) 가 실행될 때의
toastExcuteQueue 는 처음 실행한 toast만 가지고 있다.


const popToastExcuteQueue = (id) => {
		setTargetId(id);
};

useEffect(
	() => {
		if (targetId === null) return;
		const nextToastExcuteQueue = Object.assign({}, toastExcuteQueue);
		delete nextToastExcuteQueue[targetId];
		setToastExcuteQueue(nextToastExcuteQueue);
	},
	[ targetId ]
);
이렇게 직접 스코프에 속하지 않도록 코드를 구성했다.



```
