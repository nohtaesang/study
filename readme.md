# STUDY

# Table of content
* [Computer Science](#computer-science)
    * [algorithm](#algorithm)
    * [computer architecture](#computer-architecture)
    * [datastructure](#datastructure)
    * [network](#network)
    * [os](#os)
* [Web](#web)
    * [browser](#browser)
    * [html](#html)
    * [css](#css)
        * [sass](#sass)
    * [javascript](#javascript)
        * [es6](#es6)
        * [dom](#dom)
        * [webpack](#webpack)
        * [babel](#babel)
        * [reactjs](#reactjs)
            * [nextjs](#nextjs)
            * [redux](#redux)
            * [redux-saga](#redux-saga)
            * [styled-component](#styled-component)
        * [react-native](#react-native)
        * [nodejs](#nodejs)
        * [library](#library)
* [Github](#github)
* [Markdown](#markdown)
* [Edu](#edu)
* [Util](#util)
* [개발 방법론](#개발 방법론)




# Computer Science





## algorithm





## computer architecture





## datastructure





## network





## os





# Web
* [웹 프로그래밍 튜토리얼 - poiemaweb](https://poiemaweb.com/)





## browser
* [브라우저는 어떻게 동작하는가 - D2](https://d2.naver.com/helloworld/59361)





## html
### [contentEditable 으로 인라인 편집기(inline editor) 제작하기](https://code.tutsplus.com/ko/tutorials/create-an-inline-text-editor-with-the-contenteditable-attribute--cms-25655)
```javascript
사용법]
<div contentEditable='true'/>

contentEditable 상태 설정하기]
node.contentEditable = 'true' 

컨텐츠 넣기]
node.innerHTML = data

컨텐츠 읽기]
node.innerHTML

css로 접근하기]
[contenteditable="true"]{
    color: green;
}
```
### [designMode 로 문서 전체 편집가능하게 하기](https://www.w3schools.com/jsref/prop_document_designmode.asp)
```javascript
document.designMode = "on";
```



## css
### [inline formatting context에 대한 이해 (lineheight, vertical-align) - wit ](https://wit.nts-corp.com/2017/09/25/4903)
### [flex 참고하기 가장 좋은 사이트](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
###  [user-select - 사용자로부터 컨텐츠 선택을 제어하는 방법 - blog](https://webisfree.com/2018-10-31/css-%ED%85%8D%EC%8A%A4%ED%8A%B8-%EC%84%A0%ED%83%9D-%EB%93%9C%EB%9E%98%EA%B7%B8-%EC%84%A4%EC%A0%95-user-select-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
###  [transform:scale(0.5) - <img> 태그 비율 조절하기](https://codeday.me/ko/qa/20190310/34589.html)
###  background로 이미지를 가져왔을 때는 background-size:로 사이즈를 조절할 수 있다.
```javascript
background: url('https://static.bitnaru.com/v3_web/images/icon_next.png') 0 0 no-repeat;
background-size: 15px;
```
###  [before, after를 이용하여 쉽게 부가적인 컨텐츠를 추가할 수 있다 - TODO]
###  i tag의 색상과 크기는 font-size, color로 설정할 수 있다.
###  [transition - 특정 속성 제외하고 적용하기](https://hashnode.com/post/applying-transition-to-everything-except-one-property-cilsya6zj00ewag531amxwp8n)
```javascript
transition: all 0.5s, z-index 0s;
z-index도 trasition에 영향을 받는다.
이것 때문에 뷰에서 문제가 생긴다.
```
### [css로 삼각형 만들기](http://uxuiz.cafe24.com/wp/archives/4619)
```javascript
.triangle {
    width: 0px;
    height: 0px;
    border-top: 5px solid none;
    border-bottom: 5px solid #4385a7;
    border-right: 5px solid transparent;
    border-left: 5px solid transparent;
}
```
### [scale을 이용하여 드롭다운 구현하기](https://stackoverflow.com/a/17260048)
```javascript
transform-origin: top;
&.visible {
	transform: scaleY(1);
}

&.hidden {
	transform: scaleY(0);
}

문제는 자식의 크기도 함께 축소된다는 것이다.
```


## sass






## javascript
### [object에 특정 속성만 교체하고 싶을 때]
```javascript
const obj ={a:1, b:2, c:3}
const newObj = {...obj, c:4} // newObj: a:1, b:2, c:4

const temp = {b:1, c:1}
const newObj2 = {...obj, ...temp} // newObj2: a:1, b:1, c:1
```

###[new Date(date) 에서 date가 문자열이면 안된다.]()
```javascript
new Date('1558421237881') // Invalid Date
```
### [object로 array의 map 사용하기 - Object.entries() 를 사용하여](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)
```javascript
{Object.entries(tokenList).map((token, i) => <Item key={i} type="tokenList" token={token[1]} />)}
```
### [object 복사하기] (https://velog.io/@ddalpange/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EA%B0%9D%EC%B2%B4-%EB%B3%B5%EC%82%AC%ED%95%98%EA%B8%B0)
```javascript
1. Object.assign() (얕은복사)
2. JSON.PARSE(JSON.stringify()) (깊은복사) 느리다
3. 재귀 사용 (깊은복사)
4. Immutable.js 사용 (깊은복사)
5. Spread 문법 사용 (얕은복사)

immutable js 를 왜 사용하려는지 알겠다.
```


## es6





## dom
###  [DOM에 대한 간략한 정리 - wit 블로그](https://wit.nts-corp.com/2019/02/14/5522)
###  [새 창으로 링크 열기 - blog](https://rocabilly.tistory.com/84)
```javascript
window.open()
```
###  [html 태그로 이루어진 문자열을 DOM element로 바꾸기 - stackoverflow](https://stackoverflow.com/a/3104251)
```javascript
const convertStringToElement = (str) => {
	const wrapper = document.createElement('div');
	wrapper.innerHTML = str;
	return wrapper.firstChild;
};
```
###  [NodeList 객체인지 확인하기 - stackoverflow](https://stackoverflow.com/a/36857902)
```javascript
NodeList.prototype.isPrototypeOf(nodes)
```
###  classList.add(className)      
```javascript
element의 class 속성에 값을 추가한다.
이미 존재할 경우 추가하지 않는다.
```
###  after(content)
```javascript
element와 같은 레벨로 element 다음에 오도록 한다.
값 복사가 아닌 참조로 실제 값을 이동시킨다.
```
###  before(content)
```javascript
element와 같은 레벨로 element 이전에 오도록 한다.
값 복사가 아닌 참조로 실제 값을 이동시킨다.
```

###  [append((Node or DOMString)[, ...nodes]) vs appendChild(node)](https://rpubs.com/raulUbiqum/append)
```javascript
appendChild는 Node를 인자로 넣어야 한다. (string일 경우 error 발생)
append는 Node, string 모두 인자로 넣을 수 있다.
```
###  [attribute 와 property의 차이](https://medium.com/hexlant/attribute-%EC%99%80-property-%EC%9D%98-%EC%B0%A8%EC%9D%B4-c6f1c91ba91)
```javascript
attribute는 
- html document 안에서 존재한다.
- 정적으로 변하지 않는다.
ex) 
<div id='taesang' style='height:200px'><div>
1. document.getElementById('taesang').getAttribute('height') // null
2. document.getElementById('taesang').getAttribute('style') // height:200px

property는
- html DOM tree 안에서 존재한다.
- 동적으로 값이 변할 수 있다.
```
### [How to get CSS values in Javascript - inline styles과 computed style의 차이](https://zellwk.com/blog/css-values-in-js/)
```javascript
inline style은 결국 attribute
property는 computed style

inline style은
node.style.propertyName
node.getAttribute(propertyName)
으로 가져올 수 있다.

computed style은
window.getComputedStyle(node, propertyName)
으로 가져올 수 있다.
```
### [How to set CSS values in Javascript]()
```javascript
attribute 
node.style.setProperty(propertyName, value)
node.style[propertyName] = valeu

property
CSSStyleDeclaration 는 read-only여서 수정할 수가 없다.
```

###  [transition 완료 감지하기](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions#%ED%8A%B8%EB%9E%9C%EC%A7%80%EC%85%98_%EC%99%84%EB%A3%8C_%EA%B0%90%EC%A7%80%ED%95%98%EA%B8%B0)
```javascript
element.addEventListener('transitioned', ...)
```

### [.cloneNode()]
```javascript
node.cloneNode(true) // 깊은 복사
```

### .parentNode
```javascript
node.parentNode // node의 부모 노드를 반환한다.
```

### [.removeChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/removeChild)
```javascript
node.removeChild(child) // node의 자식중 child를 삭제한다
return 값은 삭제된 노드이다.

모든 자식을 지우는 방법
let element = document.getElementById("top");
while (element.firstChild) {
  element.removeChild(element.firstChild);
}
```
### [.classList](https://developer.mozilla.org/ko/docs/Web/API/Element/classList)
```javascript
add(string)

remove(string)

item
```

### 단위(ex. 100px)를 pre(100), post(px) 로 나누기
```javascript
const getStylePreAndPostFix = (prop) => {
	let pre = prop;
	let post = '';
	if (typeof pre === 'string') {
		pre = parseFloat(prop);
		const length = (pre + '').length;
		post = prop.substr(length, prop.length);
	}
	return { pre, post };
};
```


## webpack
###  [JavaScript 모듈화 도구 webpack - D2](https://d2.naver.com/helloworld/0239818)
###  [webpack, bable 적용 따라하기 - poiemaweb](https://poiemaweb.com/es6-babel-webpack-1)





1 2 3 5


## babel






## reactjs
###  [성능 최적화 - 문서](https://reactjs-kr.firebaseapp.com/docs/optimizing-performance.html)
###  [성능 최적화 21가지 방법 - 블로그](https://www.codementor.io/blog/react-optimization-5wiwjnf9hj)
###  [크롬으로 성능 확인하기 - medium](https://building.calibreapp.com/debugging-react-performance-with-react-16-and-chrome-devtools-c90698a522ad)
###  [react-device-detect - react에서 사용자가 모바일인지 확인하는 라이브러리 ](https://github.com/duskload/react-device-detect#readme)
###  [css 속성을 변경하여 image slider 구현하기 ](https://nohtaesang.tistory.com/17)
###  [렌더링 시 스크롤 중앙으로 위치시키기](https://nohtaesang.tistory.com/18)
###  [팝업창 띄울 때 스크롤 막기 - prevent scroll ](https://davidwells.io/snippets/disable-scrolling-with-javascript/)
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
###  [vanilla javascript 로 스크롤 막기 - prevent scroll](https://codepen.io/wesleypimentel/pen/KpgXJW)
###  [react life cycle](https://velopert.com/1130)
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
### [react 상대경로 설정하기](https://engineering.huiseoul.com/%EB%A6%AC%EC%95%A1%ED%8A%B8-%EC%83%81%EB%8C%80%EA%B2%BD%EB%A1%9C-%EC%A0%88%EB%8C%80%EA%B2%BD%EB%A1%9C-%EB%B3%80%EA%B2%BD-1485babb5198)
```javascript
.env 파일에 
NODE_PATH=src/
추가
```

### [간단하게 Pagination 구현]()
```javascript
블로그에 업로드
```
### [map과 setTimout을 함께 쓰면 생기는 문제]()
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
### [react outside click - airbnb](https://github.com/airbnb/react-outside-click-handler)
```javascript
바깥 클릭 검출을 쉽게 도와주는 라이브러리
```


## nextjs
###  [커스텀 라우팅을 위한 방법 - 공식 문서](https://nextjs.org/docs/#custom-app)
###  [커스텀 라우팅을 위한 방법 - github](https://github.com/zeit/next.js/#with-link)
###  [커스텀 라우팅을 위한 방법 - 블로그](http://webframeworks.kr/tutorials/nextjs/nextjs-004/)
###  [router.push()로 페이지 이동시 스크롤 최상단으로 이동시키기 - stackoverflow](https://github.com/zeit/next.js/issues/3249)
###  [Link 가 작동하지 않는 문제](https://github.com/zeit/next.js/issues/5598)
```javascript
[HMR] bundle rebuilding 이 출력되면서 페이지 이동이 일어나지 않음
결론부터 말하면, 로컬에서만 발생하는 문제
https://next-router-issue-wjnmzzmmft.now.sh/ 배포된 곳에서 테스트하면 문제가 생기지 않지만
https://github.com/malimccalla/next-routing-issue 로컬로 받아와서 테스트하면 1~2분 뒤 문제가 발생함
```








## redux
### [combineReducers](https://deminoth.github.io/redux/recipes/reducers/UsingCombineReducers.html)
```javascript
import { combineReducers } from 'redux';
import { noticeReducer } from './notice';

const rootReducer = combineReducers({ noticeReducer });

export default rootReducer;
```
### [컴포넌트 내부 변수와 redux 전역변수, 언제 어떻게 쓰는게 좋을까?](https://huns.me/development/1953)
```javascript
실제 제품을 개발할 때는 이것을 전역 상태로 둘지, 지역 상태로 둘지 결정하기 모호한 경우를 꽤 자주 만난다. 특히나 요구 사항이 완전치 않은 개발 초기에 이런 상황을 자주 접한다. 이럴 때는 우선 지역 상태로 분류하는 게 좋다. 전역 상태를 처리하는 과정이 지역 상태를 처리하는 과정 보다 번거롭고, 지역 상태가 전역 상태보다 외부와의 접점이 적기 때문에 나중에 상태의 성격을 변경할 때 수정 비용이 더 적게 들어간다. 그리고 지역 상태를 중심으로 자율성을 갖는 컴포넌트가 더 유연하다. 물론 유연하다는 것은 구현에 그만큼의 비용이 더 들어간다는 뜻이기도 하다. 따라서 상황에 따라 적절히 판단해야 하며 이는 개발자의 몫이다.

```
### [reselector 모듈 - 이전 상태를 캐시하고 있다가 새로운 상태가 들어오면 변경 여부를 확인하여 변경이 있을때만 하위 컴포넌트로 상태를 전파하는 문지기 역할](https://github.com/reduxjs/reselect)



## redux-saga
### [redux-saga 사이드 이펙트 관리](https://meetup.toast.com/posts/136)
```javascript
사이드 이펙트는, 코드가 외부 세계에 영향을 주거나 받는 것이다.
```
### [redux-saga와 generator](https://meetup.toast.com/posts/140)
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
### 이펙트만을 Yield 하는 Saga를 작성하는 것이 좋다.
### [redux-saga channel](https://meetup.toast.com/posts/145)
```javascript
WebSocket과 같은 외부 이벤트들은 일반적으로 리스너를 등록하는 on(type, listener) 형태의 push 기반 로직을 작성한다. 하지만 reudx-saga는 take(pattern) 형태의 액션을 끌어오는 pull 기반 로직을 작성한다.

push와 pull
push기반 동작은 휴대폰을 만지지 않아도 알림창에 데이터가 계속 오는 것이다.
pull기반 동작은 웹에서와 같이 데이터를 요청하면 받는 것이다.

channel은 push동작을 pull 동작으로 바꾸는 것을 일반화 한 방법이다.
프로세스: 동시적으로 수행되는 독립적인 작업이다. 각 코드는 순차적으로 처리된다.
체널: FIFO의 큐다. 각 프로세스는 체널을 통해 데이터를 주고받으며 통신한다. 체널에 put연산으로 데이터를 추가하고, take 연산으로 데이터를 가져온다.
```
### [react redux-saga example app ](https://medium.com/@lavitr01051977/make-your-first-call-to-api-using-redux-saga-15aa995df5b6)






## styled-component
###  [바벨 설정하기 - 문서](https://www.styled-components.com/docs/tooling#babel-plugin)
###  [media query 사용하기]
```javascript
@media (max-width: 1024px) {
	width: 100%;
}
```
### [animation 사용하기](https://medium.com/@shlee1353/%EB%A6%AC%EC%95%A1%ED%8A%B8-styled-components-%EC%95%A0%EB%8B%88%EB%A9%94%EC%9D%B4%EC%85%98-%EA%B5%AC%ED%98%84-fbbb8aa9e722)
```javascript
const Box = styled.div`
	position: absolute;
	transition: 1s;
	transition-delay: 0.5s;
	width: 200px;
	animation: boxMove 1s ease-out;

	@keyframes boxMove {
		0% {
			right: -200px;
		}
		100% {
			right: 0px;
		}
	}
`;
```








## react-native










## nodejs

## library
## axios
### [axios.delete](https://github.com/axios/axios/issues/736)
```javascript
delete의 params은 {data: params} 처럼 data로 지정해야 한다.


function* deleteNotice(action) {
	const { payload } = action;
	const { databaseUrl } = config;
	const url = `${databaseUrl}/notice`;
	const params = { ...payload };
	const headers = { headers: { 'Content-Type': 'application/json' } };
	try {
		const res = yield axios.delete(url, { data: params }, headers);
		const { data } = res;
		console.log(res);
		yield put({ type: 'DELETE_NOTICE_SUCCESS', payload: data });
	} catch (err) {
		console.log(err);
	}
}
```
### ()






# github









# markdown
###  [내부 링크 - blog](https://a1010100z.tistory.com/entry/Markdown-%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4-%EB%AC%B8%EC%84%9C-%EB%82%B4%EB%B6%80-%EB%A7%81%ED%81%AC-%EC%9D%B4%EB%8F%99)
```javascript
[Title](#taesang)
# taesang
```











# edu
###  [전반적인 코딩 관련 학습 자료. 요약이 잘 되어있음 - tcpschool ](http://tcpschool.com/)


# util
###  [hmtl 아이콘 - xe icon](https://xpressengine.github.io/XEIcon/library-2.3.3.html)
### [변수명 짓기](https://www.curioustore.com/)

# 개발 방법론
### DB사용을 최소한으로
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

### 배열을 원하는 객체로 변환하여 map 자료구조처럼 사용하기
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

