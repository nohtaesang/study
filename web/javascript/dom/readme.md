* [DOM에 대한 간략한 정리 - wit 블로그](https://wit.nts-corp.com/2019/02/14/5522)
* [새 창으로 링크 열기 - blog](https://rocabilly.tistory.com/84)
```
window.open()
```
* [html 태그로 이루어진 문자열을 DOM element로 바꾸기 - stackoverflow](https://stackoverflow.com/a/3104251)
```
const convertStringToElement = (str) => {
 const wrapper = document.createElement('div');
 wrapper.innerHTML = str;
 return wrapper.firstChild;
};
```
* [NodeList 객체인지 확인하기 - stackoverflow](https://stackoverflow.com/a/36857902)
```
NodeList.prototype.isPrototypeOf(nodes)
```
* [element인지 확인하기]
```
el.nodeType 이 undfined가 아니면, element이다.
```
* [textContext, innerText, innerHTML 성능 비교 - blog](https://equal-blog.tistory.com/entry/innerHTML-innerText-textContent-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EB%B3%84-%EC%84%B1%EB%8A%A5-%EB%B9%84%EA%B5%90)
```
textContext를 사용하자
```

## DOM API
1. classList
    1. add()
        * element의 class 속성에 값을 추가한다.
        * 이미 존재할 경우 추가하지 않는다.
1. after() 
    * element와 같은 레벨로 element 다음에 오도록 한다.
    * 값 복사가 아닌 참조로 실제 값을 이동시킨다.
    
