#### [s3 로 이미지 업로드하기](https://ideveloper2.tistory.com/117)
#### [절대경로로 수정하기](https://engineering.huiseoul.com/%EB%A6%AC%EC%95%A1%ED%8A%B8-%EC%83%81%EB%8C%80%EA%B2%BD%EB%A1%9C-%EC%A0%88%EB%8C%80%EA%B2%BD%EB%A1%9C-%EB%B3%80%EA%B2%BD-1485babb5198)
#### [절대 경로 수정 후 jsconfig.json 으로 vscode에서 경로잡기](https://itnext.io/create-react-app-with-vs-code-1913321b48d)
#### [map을 사용하여 Object를 렌더링하기]()
```javascript
{Object.values(toastExcuteQueue).map((value, i) => (
	const {type, msg, clearTimer} = value
	<Toast key={i} type={type}>
		<div className="h4">{msg}</div>
		<div onClick={() => clearTimer()}>button</div>
	</Toast>
))}
```
#### [데이터 변화에 따라 렌더링할 떄 깜빡이는 현상(데이터 간의 조작 시간차이) 없애기]
```
A라는 데이터를 이용하여 B라는 데이터를 만든다고 하자.
A와 B를 모두 렌더링하고 있다면, A가 렌더링 되고 난 후 B가 렌더링 될 것이다.
이럴 경우, 깜빡이는 현상, 혹은 시간 차 렌더링이 될 수 있다.
그럴 경우 A라는 데이터를 이용하여 B를 만들면서 A와 똑같은 C를 동시에 만들어 C와 B를
마치 A와 B처럼 렌더링하면 문제는 해결된다.

```
####  [성능 최적화 - 문서](https://reactjs-kr.firebaseapp.com/docs/optimizing-performance.html)
####  [성능 최적화 21가지 방법 - 블로그](https://www.codementor.io/blog/react-optimization-5wiwjnf9hj)
####  [크롬으로 성능 확인하기 - medium](https://building.calibreapp.com/debugging-react-performance-with-react-16-and-chrome-devtools-c90698a522ad)
####  [react-device-detect - react에서 사용자가 모바일인지 확인하는 라이브러리 ](https://github.com/duskload/react-device-detect#readme)
####  [css 속성을 변경하여 image slider 구현하기 ](https://nohtaesang.tistory.com/17)
####  [렌더링 시 스크롤 중앙으로 위치시키기](https://nohtaesang.tistory.com/18)
####  [팝업창 띄울 때 스크롤 막기 - prevent scroll ](https://davidwells.io/snippets/disable-scrolling-with-javascript/)
```javascript

componentWillReceiveProps(nextProps) {
    const { Core } = nextProps;
    const { popupState } = Core;
    const { scrollX, scrollY } = window;

    if (popupState) {
        this.setState({
            scrollX,
            scrollY
        });
        window.addEventListener('scroll', this.noScroll);
    } else {
        window.removeEventListener('scroll', this.noScroll);
    }
}

noScroll = () => {
    const { scrollX, scrollY } = this.state;
    window.scrollTo(scrollX, scrollY);
};
문제점: 스크롤을 빠르게 할 경우 화면이 흔들리는 경우가 보임
```
####  [vanilla javascript 로 스크롤 막기 - prevent scroll](https://codepen.io/wesleypimentel/pen/KpgXJW)
####  [react life cycle](https://velopert.com/1130)
```javascript
1. constructor: 컴포넌트가 처음 만들어질 때 실행된다.
2. componentWillMount: 컴포넌트가 DOM 위에 만들어지기 전에 실행된다.
3. render: 컴포넌트 렌더링을 담당한다.
4. componentDidMount: 컴포넌트가 만들어지고 첫 렌더링을 다 마친 후 실행되는 메소드다.
5. componentWillReceieveProps: 컴포넌트가 prop을 받았을 때 실행된다.
* 여기서 this.setState()를 해도 추가적으로 렌더링하지 않는다.
6. shouldComponentUpdate: prop, state가 변경 되었을 때 리렌더링을 할지 말지 정하는 메소드다.
7. componentWillUpdate: 컴포넌트가 업데이트 되기 전에 실행된다.
* this.setState() 사용 금지
8. render
9. componentDidUpdate: 컴포넌트가 리렌더링을 마친 후 실행된다.
10. componentWillUnmount: 컴포넌트가 DOM에서 사라진 후 실행되는 메소드다.
```
#### [react 상대경로 설정하기](https://engineering.huiseoul.com/%EB%A6%AC%EC%95%A1%ED%8A%B8-%EC%83%81%EB%8C%80%EA%B2%BD%EB%A1%9C-%EC%A0%88%EB%8C%80%EA%B2%BD%EB%A1%9C-%EB%B3%80%EA%B2%BD-1485babb5198)
```javascript
.env 파일에 
NODE_PATH=src/
추가
```
#### [간단하게 Pagination 구현]()
```javascript
블로그에 업로드
```
#### [map과 setTimout을 함께 쓰면 생기는 문제]()
```javascript
map으로 queue에 있는 항목을 렌더링하고 싶다.
각 항목들은 일정 시간이 지나면 사라진다.
queue에 삽입되는 순간 map에서 항목을 그리고,
항목은 setTimeout에 의해 실행된다.
여기서 일정 시간이 지나 어떤 항목이 사라지게 된다.
여기서 queue는 수정이 된다.
이때 발생하는 문제는 map이 전체 queue를 다시 rendering하게 된다.
따라서 setTimeout은 또 걸리게 된다.


export const renderAlertBox = (queue, spliceAlertBox) => {
	return <AlertBox>{queue.map((alert, i) => renderAlert(alert, i, spliceAlertBox, 5000))}</AlertBox>;
};


const renderAlert = (obj, index, spliceAlertBox, sec) => {
	const dequeue = () => {
		spliceAlertBox(obj);
	};

	const timer = setTimeout(dequeue, sec);

	const onClickClose = () => {};

	return (
		<Alert key={index}>
			<i className="xi-bell-o" />
			<div>{obj.msg}</div>
			<div>{obj.state}</div>
			<i className="xi-close-min" onClick={onClickClose} />
		</Alert>
	);
};
```
#### [react outside click - airbnb](https://github.com/airbnb/react-outside-click-handler)
```javascript
바깥 클릭 검출을 쉽게 도와주는 라이브러리
```

#### [react-infinite-scroller](https://github.com/CassetteRocks/react-infinite-scroller/blob/master/src/InfiniteScroll.js)