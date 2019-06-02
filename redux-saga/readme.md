#### [왜 redux-saga인가 - 한글 정리 깔끔](https://gracefullight.dev/2017/12/06/Why-redux-saga/)
#### [redux-saga 사이드 이펙트 관리](https://meetup.toast.com/posts/136)
```javascript
사이드 이펙트는, 코드가 외부 세계에 영향을 주거나 받는 것이다.
```
#### [redux-saga와 generator](https://meetup.toast.com/posts/140)
```javascript
제너레이터는 제너레이터 함수의 반환이다.

function* myGeneratorFunction() {
  yield 1;
  yield 2;
  yield 3;
}

const generator = myGeneratorFunction();

console.log(generator.next().value); // 1
console.log(generator.next().value); // 2
console.log(generator.next().value); // 3


제너레이터는 이터레이터 프로토콜과 이터러블 프로토콜을 따른다.

이터러블 프로토콜은 단순히 obj[Symbol.iterator]: Function => Iterator로 표현할 수 있다.
객체는 이터레이터 심볼 키값에 이터레이터를 반환하는 메서드를 가지고 있다면 이터러블이다.

이터레이터 프로토콜도 단순하다. 
객체가 next라는 메서드를 가지고 있고, 그 결과로 IteratorResult 라는 객체를 반환하면 된다.
반환되는 IteratorResult는 {done: boolean, value: any} 형태의 단순한 객체다.

제너레이터는 이터러블이면서 이터레이터이다.
이터러블에서 반환하는 이터레이터가 바로 자기 자신이다.
generator === generator[Symbol.iterator](); // true
```
#### 이펙트만을 Yield 하는 Saga를 작성하는 것이 좋다.
#### [redux-saga channel](https://meetup.toast.com/posts/145)
```javascript
WebSocket과 같은 외부 이벤트들은 일반적으로 리스너를 등록하는 on(type, listener) 형태의 push 기반 로직을 작성한다. 하지만 reudx-saga는 take(pattern) 형태의 액션을 끌어오는 pull 기반 로직을 작성한다.

push와 pull
push기반 동작은 휴대폰을 만지지 않아도 알림창에 데이터가 계속 오는 것이다.
pull기반 동작은 웹에서와 같이 데이터를 요청하면 받는 것이다.

channel은 push동작을 pull 동작으로 바꾸는 것을 일반화 한 방법이다.
프로세스: 동시적으로 수행되는 독립적인 작업이다. 각 코드는 순차적으로 처리된다.
체널: FIFO의 큐다. 각 프로세스는 체널을 통해 데이터를 주고받으며 통신한다. 체널에 put연산으로 데이터를 추가하고, take 연산으로 데이터를 가져온다.
```
#### [react redux-saga example app ](https://medium.com/@lavitr01051977/make-your-first-call-to-api-using-redux-saga-15aa995df5b6)
#### [yield all() - promise.all() 처럼 동시에 수행하기](https://github.com/redux-saga/redux-saga/blob/master/docs/advanced/RunningTasksInParallel.md)
