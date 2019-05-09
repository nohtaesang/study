* [DOM에 대한 간략한 정리 - wit 블로그](https://wit.nts-corp.com/2019/02/14/5522)
* [새 창으로 링크 열기 - blog](https://rocabilly.tistory.com/84)
  * window.open()
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
