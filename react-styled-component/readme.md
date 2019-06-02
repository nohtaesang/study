####  [바벨 설정하기 - 문서](https://www.styled-components.com/docs/tooling#babel-plugin)
####  [media query 사용하기]
```javascript
@media (max-width: 1024px) {
	width: 100%;
}
```
#### [animation 사용하기](https://medium.com/@shlee1353/%EB%A6%AC%EC%95%A1%ED%8A%B8-styled-components-%EC%95%A0%EB%8B%88%EB%A9%94%EC%9D%B4%EC%85%98-%EA%B5%AC%ED%98%84-fbbb8aa9e722)
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