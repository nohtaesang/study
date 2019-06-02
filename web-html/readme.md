#### [contentEditable 으로 인라인 편집기(inline editor) 제작하기](https://code.tutsplus.com/ko/tutorials/create-an-inline-text-editor-with-the-contenteditable-attribute--cms-25655)
```html
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
#### [designMode 로 문서 전체 편집가능하게 하기](https://www.w3schools.com/jsref/prop_document_designmode.asp)
```javascript
document.designMode = "on";
```