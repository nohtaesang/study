####  [커스텀 라우팅을 위한 방법 - 공식 문서](https://nextjs.org/docs/#custom-app)
####  [커스텀 라우팅을 위한 방법 - github](https://github.com/zeit/next.js/#with-link)
####  [커스텀 라우팅을 위한 방법 - 블로그](http://webframeworks.kr/tutorials/nextjs/nextjs-004/)
####  [router.push()로 페이지 이동시 스크롤 최상단으로 이동시키기 - stackoverflow](https://github.com/zeit/next.js/issues/3249)
#### [Link 가 작동하지 않는 문제](https://github.com/zeit/next.js/issues/5598)
```javascript
[HMR] bundle rebuilding 이 출력되면서 페이지 이동이 일어나지 않음
결론부터 말하면, 로컬에서만 발생하는 문제
https://next-router-issue-wjnmzzmmft.now.sh/ 배포된 곳에서 테스트하면 문제가 생기지 않지만
https://github.com/malimccalla/next-routing-issue 로컬로 받아와서 테스트하면 1~2분 뒤 문제가 발생함
```


#### [plugin 여러개 동시에 사용하기](https://github.com/zeit/next-plugins/issues/34)
```javascript
module.exports = withCSS(withTypescript(withSass({
 cssModules: true,
 webpack: (config) => {
    return config
 }
})))
```

#### [nextjs 에서 css 파일 사용하기](https://github.com/zeit/next-plugins/tree/master/packages/next-css)
```javascript
yarn add @zeit/next-css

// next.config.js
const withCSS = require('@zeit/next-css')
module.exports = withCSS({
  /* config options here */
})
```


#### [styled-components 사용시 Warning: Prop `className` did not match. 오류가 나올 경우](https://github.com/zeit/next.js/issues/4068)
```javascript
babel을 수정해준다.

module.exports = {
	presets: [ 'next/babel', '@zeit/next-typescript/babel' ],
	plugins: [
		[
			'styled-components',
			{
				ssr: true,
				displayName: true
			}
		]
	]
};

```