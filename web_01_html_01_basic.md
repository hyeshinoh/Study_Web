---
title: HTML Basic
date: 2018-09-26 15:24:14
tags: 
- programming
- web
- html

categories: 
- Programming 공부
- Web 공부
---

## 1. HTML이란

### 1.1 HTML의 개념
- HTML은 Hyper text Markup Language의 약자로, 월드와이드웹 문서를 작성하는 Markup Language
- Markup Language: 시작과 종료태그가 있는 language (대표적 예: XML)
- HTML은 여러 태그들로 구성되어 있으며 각 태그들을 사용하여 원하는 형태의 문서를 만들어갈 수 있음

### 1.2 HTML의 구성요소
(1) elements(요소): 시작태그와 종료태그로 이루어진 코드
(2) Tag(태그): 요소의 일부로 `<div>`, `<p>` 등, 시작태그와 종료태그가 있음
(3) Attribute(속성): 태그 안에 키와 값으로 이루어진 코드



## 2. HTML elements

### 2.1 Head: 타이틀을 표현하기 위한 element
- h1~h6로 여섯단계가 표현 가능
- emmet 문법: `h${$단계 제목}*6`

```html
<h1>1단계 제목</h1>
<h2>2단계 제목</h2>
<h3>3단계 제목</h3>
<h4>4단계 제목</h4>
<h5>5단계 제목</h5>
<h6>6단계 제목</h6>
```
적용시 아래와 같이 나타납니다.

><h1>1단계 제목</h1>
><h2>2단계 제목</h2>
><h3>3단계 제목</h3>
><h4>4단계 제목</h4>
><h5>5단계 제목</h5>
><h6>6단계 제목</h6>

### 2.2 p
- paragraph의 약자로 문단을 분리하기 위한 태그
- emmet 문법: `p{p_tag_$}*3`

```html
<p>p_tag_1</p>
<p>p_tag_2</p>
<p>p_tag_3</p>
```
적용시 아래와 같이 나타납니다.
><p>p_tag_1</p>
><p>p_tag_2</p>
><p>p_tag_3</p>

### 2.3 span 
- 영역을 설정하는 태그로 div 태그처럼 주로 CSS와 함께 쓰임
- div와 달리 줄바꿈이 되지 않고, 문장 단위로 지정(inline 속성)
- emmet 문법: `span{span_tag_$}*3`

```html
<span>span_tag_1</span>
<span>span_tag_2</span>
<span>span_tag_3</span>
```
적용시 아래와 같이 나타납니다.
><span>span_tag_1</span>
><span>span_tag_2</span>
><span>span_tag_3</span>


### 2.4. pre
- preformatted text의 약자로, 입력한 그대로 화면 출력하는 태그
- 줄바꿈이나 띄어쓰기가 그대로 적용되는 element

```html
<p>
    python
    data
</p>
<pre>
    python
    data
</pre>
```
적용시 아래와 같이 나타납니다. 
><p>
>	python
>	data
></p>
><pre>
>    python
>    data
></pre>


### 2.5 글씨체
- b, strong(굵은글씨)
- i,em(이탤릭체)
- sup,sub(윗첨자, 아래첨자)
- small(작은 글씨)
- mark(배경이 노랑색)
- del(삭제문자열 - 가로줄)
- ins(언더라인 문자열)
- code(코드 문자열)

```html
<span>굵은글씨: <b>굵은글씨</b></span>
<span>굵은글씨: <strong>굵은글씨</strong></span>

<span>이탤릭체: <i>이탤릭체</i></span>
<span>이탤릭체: <em>이탤릭체</em></span>

<span>윗첨자: <sup>윗첨자</sup></span>
<span>아래첨자: <sub>아래첨자</sub></span>
<span>작은글씨: <small>작은글씨</small></span>

<span>글자배경이 <mark>노란색</mark> 입니다</span>
<span>문자열 <del>삭제</del>입니다</span>
<span>문자열 <ins>언더라인</ins>입니다</span>

<span>코드: <code>code</code></span>
```
적용시 아래와 같이 나타납니다.

><span>굵은글씨: <b>굵은글씨</b></span>
><span>굵은글씨: <strong>굵은글씨</strong></span>
>
><span>이탤릭체: <i>이탤릭체</i></span>
><span>이탤릭체: <em>이탤릭체</em></span>
>
><span>윗첨자: <sup>윗첨자</sup></span>
><span>아래첨자: <sub>아래첨자</sub></span>
><span>작은글씨: <small>작은글씨</small></span>
>
><span>글자배경이 <mark>노란색</mark> 입니다</span>
><span>문자열 <del>삭제</del>입니다</span>
><span>문자열 <ins>언더라인</ins>입니다</span>
>
><span>코드: <code>code</code></span>


#### 참고자료
- 패스트캠퍼스, ⟪데이터사이언스스쿨 8기⟫ 수업자료
