# coding-standard
HTML, CSS 작성 가이드.

> [codeguide.co](git@github.com:dalgos/coding-standard.git)의 내용을 바탕으로, 필요한 내용만을 참고하여 작성되었습니다.

html로 직접 작성하는 경우 필요한 규칙입니다. reactJS등의 프레임워크를 통해 생성되는 코드에는 적용되지 않습니다.

# HTML

## Syntax

* 들여쓰기는 `2space`를 사용합니다.(tab은 사용하지 않습니다.)
* 속성은 반드시 큰따옴표("")를 사용합니다.
* 종료 태그를 임의로 누락하지 않도록 주의합니다.

```html
<!doctype html>
<html>
  <head>
    <title>coding-standard</title>
  </head>
  <body>
    <img src="logo.png" alt="logo">
    <div class="title">coding-standard</div>
  </body>
</html>
```

## HTML5 doctype

* doctype 버전은 html5 방식을 사용합니다.

```html
<!doctype html>
<html>
  <head></head>
  <body></body>
</html>
```

## 언어 속성 추가하기

* html 태그에 `lang` 속성을 이용해 언어를 반드시 표기합니다.

```html
<html lang="ko">
  ...
</html>
```

## IE 호환성 모드

* IE 환경에서의 안정적인 렌더링 성능확보를 위해 head에 `<meta>`를 추가합니다.

```html
...
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
...
```

## 문자 인코딩

* 문자 인코딩 타입은 `UTF-8`로 설정합니다.

```html
<meta charset="UTF-8">
```

## CSS, Javascript 사용

* `style`, `script` 태그 사용시 별도의 `type` 속성은 작성하지 않습니다.

```html
<!-- 외부 css 파일 사용하기 -->
<link rel="stylesheet" href="coding-standard.css">

<!-- 문서 내부에 스타일을 직접 작성할 때 -->
<style>
/*...*/
</style>

<!-- Javascript을 사용하기 -->
<script src="coding-standard.js"></script>
```

## 속성 순서

* 코드의 가독성을 위해 아래의 순서로 속성을 작성합니다.
  - class
  - id, name
  - data-*
  - src, for, type, href, value
  - title, alt
  - role, aria-*

```html
<a class="btn btn-small" id="saveButton" data-toggle="modal" href="#">
  저장하기
</a>

<input class="form-control" type="text">

<img src="coding.png" alt="coding">
```

## Boolean 속성

* Boolean 타입의 값을 사용하는 특정 속성의 경우 HTML5의 스펙에 맞추어 그 값을 별도로 입력하지 않습니다.(해당 속성명이 작성된 상태가 `true`)

```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>선택하세요</option>
</select>
```

## 마크업의 수를 최소화합니다.

```html
<!-- 이렇게 작성하기 보다는, -->
<span class="thumb">
  <img src="thumb.png">
</span>

<!-- 이렇게 작성하는 것이 나아 보입니다 -->
<img class="thumb" src="thumb.png">
```

## Javascript를 이용한 마크업 생성

* Javascript를 이용하여 마크업을 생성하는 경우, 추적이 어렵고, 수정 및 변경 내용을 적용하고자 하는 경우 찾기 어려운 경우가 많습니다. 되도록 그 빈도를 줄이는 것이 좋겠습니다.

# CSS

## Syntax

* softtab을 지원하는 IDE를 사용한다면 해당 옵션을 활성화하고, 들여쓰기 공백은 `2space`로 지정합니다.
* 여러개의 selector를 함께 사용하는 경우 한 줄씩 분리하여 작성하도록 합니다.
* 중괄호를 시작하기전 `1space`의 공백을 추가하여, 가독성을 높입니다.
* 종료용 중괄호를 작성할때는 줄바꿈 합니다.
* 속성을 작성시 `:`뒤에 `1space`의 공백을 추가합니다.
* 속성 선언시 `;`를 붙여 선언이 종료됨을 표시합니다.
* `,`로 분리된 속성값을 작성하는 경우 `,`뒤로 `1space`의 공백을 추가합니다.
  * 컬러값을 식별하는데 유용하도록 `rgb()`, `rgba()`, `hsl()`, `hsla()`, `rect()` 등의 속성의 값의 `,`뒤에는 공백을 추가하지 않습니다.
* 1 이하의 수를 표시할때 `0`은 생략하여 작성합니다.(0.5 대신 `.5`, -0.5px 대신 `-.5px`)
* hex 컬러값 작성시 `#fff`와 같이 모두 소문자로 표기합니다.
* 가능하다면 shorthand를 활용합니다.(`#ffffff`대신 `#fff`)
* 선택자 내부의 속성의 값을 표기하는 경우 큰따옴표(`""`)를 사용합니다.

```css
/* 잘못된 케이스 */
.selector,.selector-secondary,
.selector[type=text]{
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0);
  box-shadow:0px 1px 2px #CCC,inset 0 1px 0 #FFFFF
}

/* 아래의 형태로 사용합니다. */
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin-bottom: 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```