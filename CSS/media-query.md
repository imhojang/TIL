## Media Query란?

Media query는 CSS3에서 소개된 CSS 테크닉이다.

`@media` 룰을 사용하여 어떤 특정 조건에서만 CSS 블록 안의 내용을 유효하게 하는 것이다.

### Example

만약 브라우저 윈도우가 600 px 보다 작거나 같을 경우, background-color는 lightblue여야한다면?

```css
body {
  background-color: lightgreen;
}
@media only screen and (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```
