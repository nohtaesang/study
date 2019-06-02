####  [DOM에 대한 간략한 정리 - wit 블로그](https://wit.nts-corp.com/2019/02/14/5522)
####  [새 창으로 링크 열기 - blog](https://rocabilly.tistory.com/84)
```javascript
window.open()
```
####  [html 태그로 이루어진 문자열을 DOM element로 바꾸기 - stackoverflow](https://stackoverflow.com/a/3104251)
```javascript
const convertStringToElement = (str) => {
	const wrapper = document.createElement('div');
	wrapper.innerHTML = str;
	return wrapper.firstChild;
};
```
####  [NodeList 객체인지 확인하기 - stackoverflow](https://stackoverflow.com/a/36857902)
```javascript
NodeList.prototype.isPrototypeOf(nodes)
```
####  classList.add(className)      
```javascript
element의 class 속성에 값을 추가한다.
이미 존재할 경우 추가하지 않는다.
```
####  after(content)
```javascript
element와 같은 레벨로 element 다음에 오도록 한다.
값 복사가 아닌 참조로 실제 값을 이동시킨다.
```
####  before(content)
```javascript
element와 같은 레벨로 element 이전에 오도록 한다.
값 복사가 아닌 참조로 실제 값을 이동시킨다.
```

####  [append((Node or DOMString)[, ...nodes]) vs appendChild(node)](https://rpubs.com/raulUbiqum/append)
```javascript
appendChild는 Node를 인자로 넣어야 한다. (string일 경우 error 발생)
append는 Node, string 모두 인자로 넣을 수 있다.
```
####  [attribute 와 property의 차이](https://medium.com/hexlant/attribute-%EC%99%80-property-%EC%9D%98-%EC%B0%A8%EC%9D%B4-c6f1c91ba91)
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
#### [How to get CSS values in Javascript - inline styles과 computed style의 차이](https://zellwk.com/blog/css-values-in-js/)
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
#### [How to set CSS values in Javascript]()
```javascript
attribute 
node.style.setProperty(propertyName, value)
node.style[propertyName] = valeu

property
CSSStyleDeclaration 는 read-only여서 수정할 수가 없다.
```

####  [transition 완료 감지하기](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions#%ED%8A%B8%EB%9E%9C%EC%A7%80%EC%85%98_%EC%99%84%EB%A3%8C_%EA%B0%90%EC%A7%80%ED%95%98%EA%B8%B0)
```javascript
element.addEventListener('transitioned', ...)
```

#### [.cloneNode()]
```javascript
node.cloneNode(true) // 깊은 복사
```

#### .parentNode
```javascript
node.parentNode // node의 부모 노드를 반환한다.
```

#### [.removeChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/removeChild)
```javascript
node.removeChild(child) // node의 자식중 child를 삭제한다
return 값은 삭제된 노드이다.

모든 자식을 지우는 방법
let element = document.getElementById("top");
while (element.firstChild) {
  element.removeChild(element.firstChild);
}
```
#### [.classList](https://developer.mozilla.org/ko/docs/Web/API/Element/classList)
```javascript
add(string)

remove(string)

item
```
#### 단위(ex. 100px)를 pre(100), post(px) 로 나누기
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