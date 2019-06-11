#### [combineReducers](https://deminoth.github.io/redux/recipes/reducers/UsingCombineReducers.html)
```javascript
import { combineReducers } from 'redux';
import { noticeReducer } from './notice';

const rootReducer = combineReducers({ noticeReducer });

export default rootReducer;
```
#### [컴포넌트 내부 변수와 redux 전역변수, 언제 어떻게 쓰는게 좋을까?](https://huns.me/development/1953)
```javascript
실제 제품을 개발할 때는 이것을 전역 상태로 둘지, 지역 상태로 둘지 결정하기 모호한 경우를 꽤 자주 만난다. 특히나 요구 사항이 완전치 않은 개발 초기에 이런 상황을 자주 접한다. 이럴 때는 우선 지역 상태로 분류하는 게 좋다. 전역 상태를 처리하는 과정이 지역 상태를 처리하는 과정 보다 번거롭고, 지역 상태가 전역 상태보다 외부와의 접점이 적기 때문에 나중에 상태의 성격을 변경할 때 수정 비용이 더 적게 들어간다. 그리고 지역 상태를 중심으로 자율성을 갖는 컴포넌트가 더 유연하다. 물론 유연하다는 것은 구현에 그만큼의 비용이 더 들어간다는 뜻이기도 하다. 따라서 상황에 따라 적절히 판단해야 하며 이는 개발자의 몫이다.

```
#### [reselector 모듈 - 이전 상태를 캐시하고 있다가 새로운 상태가 들어오면 변경 여부를 확인하여 변경이 있을때만 하위 컴포넌트로 상태를 전파하는 문지기 역할](https://github.com/reduxjs/reselect)


#### [redux 분석하기](https://meetup.toast.com/posts/111)

#### [redux 와 hooks](https://react-redux.js.org/next/api/hooks)