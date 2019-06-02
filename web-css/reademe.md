
#### [transition과 animation의 차이](https://ahribori.com/article/5a0c49926c9eef13d882e3ea)
```
animation이 할 수 있는게 더 많다.
시작, 정지, 반복 까지 제어 가능
```
#### [onTransitionEnd - transtion이 끝남을 감지하는 이벤트](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/transitionend_event)
```javascript
const transition = document.querySelector('.transition');

transition.addEventListener('transitionend', () => {
  console.log('Transition ended');
});
```
#### [direction:rtl 과 ltr 로 문자 정렬하기](http://www.homejjang.com/07/text_direction.php)
```html
<p style="direction: ltr">direction 속성값을 ltr로 지정한 문단</p>
<p style="direction: rtl">direction 속성값을 rtl로 지정한 문단</p>
ltr은 left to right(왼쪽에 붙음)
rtl은 right to left(오른쪽에 붙음)
```
#### [text-overflow 시 ellipse 나오게 하기 ](https://webdir.tistory.com/483)
```css
.notice-title {
	display: inline-block;
	max-width: 300px;
	white-space: nowrap;
	overflow: hidden;
	text-overflow: ellipsis;
}
```
#### [ css를 이용하여 hover 시 다른 element에 css 적용하기](https://codepen.io/mvaneijgen/pen/oEhgk)
```css
&:hover .item-token-name {
	font-weight: bold;
}
hover이벤트가 일어나면 .item-token-name이 bold 처리된다.
```
#### [inline formatting context에 대한 이해 (lineheight, vertical-align) - wit ](https://wit.nts-corp.com/2017/09/25/4903)
#### [flex 참고하기 가장 좋은 사이트](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
####  [user-select - 사용자로부터 컨텐츠 선택을 제어하는 방법 - blog](https://webisfree.com/2018-10-31/css-%ED%85%8D%EC%8A%A4%ED%8A%B8-%EC%84%A0%ED%83%9D-%EB%93%9C%EB%9E%98%EA%B7%B8-%EC%84%A4%EC%A0%95-user-select-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
####  [transform:scale(0.5) - <img> 태그 비율 조절하기](https://codeday.me/ko/qa/20190310/34589.html)
####  background로 이미지를 가져왔을 때는 background-size:로 사이즈를 조절할 수 있다.
```css
background: url('https://static.bitnaru.com/v3_web/images/icon_next.png') 0 0 no-repeat;
background-size: 15px;
```
####  [before, after를 이용하여 쉽게 부가적인 컨텐츠를 추가할 수 있다 - TODO]
####  i tag의 색상과 크기는 font-size, color로 설정할 수 있다.
####  [transition - 특정 속성 제외하고 적용하기](https://hashnode.com/post/applying-transition-to-everything-except-one-property-cilsya6zj00ewag531amxwp8n)
```css
transition: all 0.5s, z-index 0s;
z-index도 trasition에 영향을 받는다.
이것 때문에 뷰에서 문제가 생긴다.
```
#### [css로 삼각형 만들기](http://uxuiz.cafe24.com/wp/archives/4619)
```css
.triangle {
    width: 0px;
    height: 0px;
    border-top: 5px solid none;
    border-bottom: 5px solid #4385a7;
    border-right: 5px solid transparent;
    border-left: 5px solid transparent;
}
```
#### [scale을 이용하여 드롭다운 구현하기](https://stackoverflow.com/a/17260048)
```css
transform-origin: top;
&.visible {
	transform: scaleY(1);
}

&.hidden {
	transform: scaleY(0);
}

문제는 자식의 크기도 함께 축소된다는 것이다.
```
####[ 스크롤 영향 안받기 - overflow:overay ]()
```
scroll의 영향을 안받도록 설정한다.
(scroll 까지 width로 계산함)
```