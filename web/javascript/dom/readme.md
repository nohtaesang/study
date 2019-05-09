* [DOM에 대한 간략한 정리 - wit 블로그](https://wit.nts-corp.com/2019/02/14/5522)
* [새 창으로 링크 열기](https://rocabilly.tistory.com/84)
  * window.open()
* [html 태그로 이루어진 문자열을 DOM element로 바꾸기](https://stackoverflow.com/a/3104251)
  * const wrapper = document.createElement('div')
  * wrapper.innerHTML = content
    * div로 문자열을 감싼다.
  * wrapper.firstChild 으로 DOM element로 접근할 수 있다.
