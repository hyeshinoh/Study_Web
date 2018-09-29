---
title: CSS Selector
date: 2018-09-27 19:01:10
tags: 
- programming
- web
- CSS
categories: 
- Programming 공부
- Web 공부
---

## 1. CSS

### 1.1 CSS란
- CSS는 Cascading Style Sheets의 약자로, HTML, XHTML, XML 같은 문서의 스타일을 꾸밀 때 사용하는 스타일 시트 언어
- 글꼴이나 배경색, 너비와 높이, 위치 등을 지정할 수 있음
- 웹브라우저, 스크린 크기, 장치에 따라서 화면을 다르게 표시될 수 있도록 지정할 수 있음
- 문서의 내용과 표현을 분리하며 CSS 파일만 수정하면 스타일에 해당하는 HTML 문서가 한 번에 수정되는 장점이 있음

### 1.2 CSS 작성법
- html 문서의 `<head><style>` `</style></head>` 안에 작성 
- `선택자 {속성:속성값; 속성:속성값;}`
- web crawling을 위해서는 CSS selector(선택자)를 이해해야 함

### 1.3 Selector
- `#id`, `.class`, `tag-name` 세 가지를 주로 이용해서 select, 속성값으로도 select 가능
- css 속성을 추가하기 위해 특정 element를 선택할 때 사용
- div element를 select하기
```html
div{

}
```
- p element의 ds1 클래스를 select하기
```html
p.ds1{

}
```
- 한칸 띄우면 하위 element, 붙여쓰면 둘다 해당 element
```html
p.ds1.ds{

}
```

## 2. id Selector
- id를 select하기 위해서 `#아이디이름`을 사용
- id로 ds1, ds2를 select하여 style 적용하기
```html
<head>
  <style>
    #ds1{
    font-size: 32px;
    }
    #ds1, #ds2{
    color: red;
    }
  </style>
</head>
<body>
  <!-- emmet: p#ds${ds$}*2 -->
  <p id="ds1">ds1</p>
  <p id="ds2">ds2</p>
</body>
```

## 3. Class Selector
- class select 위해 `.클래스이름`을 사용
- `.class`로 select하여 style 적용하기
```html
<head>
  <style>
    .ds{
    font-size: 15px;
    }
    .ds3, .ds4{
    font-weight: bold;
    }
    .science{
    color: blue;
    }
  </style>
</head>
<body>
  <!-- span.ds.ds${a$}*5 -->
  <span class="ds ds1">a1</span>
  <span class="ds ds2">a2</span>
  <span class="ds ds3">a3</span>
  <span class="ds ds4">a4</span>
  <span class="ds ds5">a5</span><br> 
  <span class="ds ds1 data">b1</span>
  <span class="ds ds2 data">b2</span>
  <span class="ds ds3 science">b3</span>
  <span class="ds ds4 science">b4</span>
  <span class="ds ds5 science">b5</span>
</body>
```

## 4. not
- 특정 element를 빼고 싶을 때 사용
```html
<head>
  <style>
    .d:not(.ds2){
    background-color: yellow;
    }
  </style>
</head>
<body>
  <!-- span.ds.ds${a$}*5 -->
  <span class="d ds1">a1</span>
  <span class="d ds2">a2</span>
  <span class="d ds3">a3</span>
  <span class="d ds4">a4</span>
  <span class="d ds5">a5</span><br>
  <span class="d ds1 data">b1</span>
  <span class="d ds2 data">b2</span>
  <span class="d ds3 science">b3</span>
  <span class="d ds4 science">b4</span>
  <span class="d ds5 science">b5</span>
</body>
```

## 5. first-child, last-child, nth-child
- body, div, p 등등의 element로 감싸져있는 element의 n번째 element가 설정한 css selector와 맞으면 css가 적용
- 아래의 본문에 스타일을 적용한다고 가정
```html
<body>

  <p class="sc" id="ds1">class: sc | id: ds1</p>
  <p class="sc" id="ds2">class: sc | id: ds2</p>

  <div class="dsc">
    <p class="ds ds1">ds1</p>
    <p class="ds ds2">ds2</p>
    <p class="ds ds3">ds3</p>
    <p class="ds ds4">ds4</p>
    <p class="ds ds5">ds5</p>
  </div>

  <div class="contents">
    <h1>inner1</h1>
    <div class="txt">
      <h1>inner2</h1>
      <h1>inner3</h1>
    </div>
  </div>

  <div>
    <h1>inner4</h1>
  </div>

  <p class="ts"><span>Span1</span><span>Span2</span></p>

</body>
```

### 5.1 first-child
- 가장 앞에 있는 element를 선택할 때 사용
#### example 1 
```html
.ds:first-child {
color: blue;
}
```
- body의 first element는 `.sc` 이기 때문에 `.ds`와 같지 않으므로 css가 적용되지 않음
- ds 클래스 element를 div로 묶어준 부분은 div의 첫번째 엘리먼트가 `.ds`가 맞으므로 css가 적용됨

#### example 2
```html
.sc:first-child {
color: green;
}
```
- body의 first elememt로 `.sc`가 있으므로 green이 적용

#### example 3
```html
h1:first-child {
color: brown;
}
```
- div의 first element로 tag가 h1인 엘리먼트가 inner1, inner2, inner4이므로 3개의 element에 css가 적용

#### example 4
```html
span:first-child{
color: purple;
font-weight: bold;
}
```
- p안에 first element로 span element가 있으므로 css 적용

### 5.2 last-child
- 가장 마지막에 있는 element를 선택할 때 사용

#### example
```html
.ds:last-child {
color: red;
}
```
- body의 last element로 `.ds`가 없고, div의 last element로 `.ds`가 없으므로 css가 적용되지 않음
- div의 last element에는 `.ds`가 있으므로 css가 적용


### 5.3 nth-child
- n번째에 있는 element를 선택할 때 사용

#### example
```html
.ds:nth-child(3), .ds:nth-child(4){
color: red;
}
```
- div의 3rd, 4th element로 `.ds`가 있으므로 "ds3", "ds4"에 css가 적용

## 6. depth
- element의 level, 깊이를 선택
- 공백문자: 하위 element를 모두 select
- `>`: 바로 아래 depth에 대한 element만 select
- tagname은 아무것도 붙이지 않고 쓰면 select할 수 있음

```html
<head>
  <style>
    .contents h1{
    color: red;
    }

    .contents > h1{
    font-size: 16px;
    }

    /*body > div > h1{
    color: yellow;
    }*/
  </style>
</head>
<body>
  <div class="contents">
    <h1>inner1</h1>
  <div class="txt">
    <h1>inner2</h1>
  </div>
  </div>
</body>
```

#### 참고자료
- 패스트캠퍼스, ⟪데이터사이언스스쿨 8기⟫ 수업자료
