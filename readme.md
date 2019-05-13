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
            * [styled-component](#styled-component)
        * [react-native](#react-native)
        * [nodejs](#nodejs)
* [Github](#github)
* [Markdown](#markdown)
* [Edu](#edu)
* [Util](#util)





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





## css
* [inline formatting context에 대한 이해 (lineheight, vertical-align) - wit ](https://wit.nts-corp.com/2017/09/25/4903)
* [flex 참고하기 가장 좋은 사이트](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* [user-select - 사용자로부터 컨텐츠 선택을 제어하는 방법 - blog](https://webisfree.com/2018-10-31/css-%ED%85%8D%EC%8A%A4%ED%8A%B8-%EC%84%A0%ED%83%9D-%EB%93%9C%EB%9E%98%EA%B7%B8-%EC%84%A4%EC%A0%95-user-select-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
* [transform:scale(0.5) - img 태그 비율 조절하기](https://codeday.me/ko/qa/20190310/34589.html)
* background로 이미지를 가져왔을 때는 background-size:로 사이즈를 조절할 수 있다.
```
background: url('https://static.bitnaru.com/v3_web/images/icon_next.png') 0 0 no-repeat;
background-size: 15px;
```
* [before, after를 이용하여 쉽게 부가적인 컨텐츠를 추가할 수 있다 - TODO]
* i tag의 색상과 크기는 font-size, color로 설정할 수 있다.



## sass






## javascript





## es6





## dom
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
* classList.add(className)      
    * element의 class 속성에 값을 추가한다.
    * 이미 존재할 경우 추가하지 않는다.

* after(content) 
    * element와 같은 레벨로 element 다음에 오도록 한다.
    * 값 복사가 아닌 참조로 실제 값을 이동시킨다.

* [append((Node or DOMString)[, ...nodes]) vs appendChild(node)](https://rpubs.com/raulUbiqum/append)
    * appendChild는 Node를 인자로 넣어야 한다. (string일 경우 error 발생)
    * append는 Node, string 모두 인자로 넣을 수 있다.


## webpack
* [JavaScript 모듈화 도구 webpack - D2](https://d2.naver.com/helloworld/0239818)
* [webpack, bable 적용 따라하기 - poiemaweb](https://poiemaweb.com/es6-babel-webpack-1)







## babel







## reactjs
* [성능 최적화 - 문서](https://reactjs-kr.firebaseapp.com/docs/optimizing-performance.html)
* [성능 최적화 21가지 방법 - 블로그](https://www.codementor.io/blog/react-optimization-5wiwjnf9hj)
* [크롬으로 성능 확인하기 - medium](https://building.calibreapp.com/debugging-react-performance-with-react-16-and-chrome-devtools-c90698a522ad)
* [react-device-detect - react에서 사용자가 모바일인지 확인하는 라이브러리 ](https://github.com/duskload/react-device-detect#readme)
* [css 속성을 변경하여 image slider 구현하기 ](https://nohtaesang.tistory.com/17)
* [렌더링 시 스크롤 중앙으로 위치시키기](https://nohtaesang.tistory.com/18)






## nextjs
* [커스텀 라우팅을 위한 방법 - 공식 문서](https://nextjs.org/docs/#custom-app)
* [커스텀 라우팅을 위한 방법 - github](https://github.com/zeit/next.js/#with-link)
* [커스텀 라우팅을 위한 방법 - 블로그](http://webframeworks.kr/tutorials/nextjs/nextjs-004/)
* [router.push()로 페이지 이동시 스크롤 최상단으로 이동시키기 - stackoverflow](https://github.com/zeit/next.js/issues/3249)
* [Link 가 작동하지 않는 문제](https://github.com/zeit/next.js/issues/5598)
  * [HMR] bundle rebuilding 이 출력되면서 페이지 이동이 일어나지 않음
  * 결론부터 말하면, 로컬에서만 발생하는 문제
  * https://next-router-issue-wjnmzzmmft.now.sh/ 배포된 곳에서 테스트하면 문제가 생기지 않지만
  * https://github.com/malimccalla/next-routing-issue 로컬로 받아와서 테스트하면 1~2분 뒤 문제가 발생함









## redux












## styled-component
* [바벨 설정하기 - 문서](https://www.styled-components.com/docs/tooling#babel-plugin)
* [media query 사용하기]
```
@media (max-width: 1024px) {
	width: 100%;
}
```










## react-native










## nodejs








# github









# markdown
* [내부 링크 - blog](https://a1010100z.tistory.com/entry/Markdown-%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4-%EB%AC%B8%EC%84%9C-%EB%82%B4%EB%B6%80-%EB%A7%81%ED%81%AC-%EC%9D%B4%EB%8F%99)
```
[Title](#taesang)
# taesang
```











# edu
* [전반적인 코딩 관련 학습 자료. 요약이 잘 되어있음 - tcpschool ](http://tcpschool.com/)


# util
* [xe icon](https://xpressengine.github.io/XEIcon/library-2.3.3.html)