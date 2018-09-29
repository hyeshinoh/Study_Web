---
title: HTML Layout
date: 2018-09-26 17:16:09
tags: 
- programming
- web
- html

categories: 
- Programming 공부
- Web 공부
---

## 1. div
- 레이아웃을 잡아줄 때 사용, 가장 많이 쓰이는 element
```html
<!--emmet: div{div$}*3 -->
<div style="width:500px; height:200px; background-color: grey;">div1
	<p>div1</p>
</div>
<div>div2</div>
<div>div3</div>
```
적용시 아래와 같이 나타납니다.
><div style="width:500px; height:200px; background-color: grey;">div1
>	<p>div1</p>
></div>
><div>div2</div>
><div>div3</div>


 
## 2. table
- row & column이 있는 table 모양을 나타낼 때 사용하는 element
- 사용하는 태그
	- table: 표 생성
	- caption: 표 제목 생성
    - tr: row 생성
	- th: column 이름이 들어가는 셀 생성
	- td: 내용이 들어가는 셀 생성
	- 각 열의 의미에 따라 thead, tbody, tfoot 태그로 구분
	- colspan 속성: 가로로 셀을 합칠 때 사용 (e.g.`colspan="2"`)
	- rowspan 속성: 세로로 셀을 합칠 때 사용 (e.g.`rowspan="2"`)
	
- emmet 문법
	- `+`: 동일한 레벨로 element 생성
    - `>`: 하위 레벨에 생성
    - `^`: 상위 depth로 한 단계 올라감
    - `@`: $ 쓸 때 초기값 설정
   
```html
table>caption{table title}+thead>tr>th{col$}*4^^tbody>tr>td{value$@3}*4 -->
```
```html
<table>
  <caption>table title</caption>
  <thead>
    <tr>
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
      <th>col4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>value3</td>
      <td>value4</td>
      <td>value5</td>
      <td>value6</td>
    </tr>
  </tbody>
</table>
```
적용시 아래와 같이 나타납니다.
<table>
  <caption>table title</caption>
  <thead>
    <tr>
      <th>col1</th>
      <th>col2</th>
      <th>col3</th>
      <th>col4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>value3</td>
      <td>value4</td>
      <td>value5</td>
      <td>value6</td>
    </tr>
  </tbody>
</table>


## 3. ul, li
- list element
- 크롤링할 때 많이 보게 될 태그
- emmet 문법: `ul>li{ul_li_$}*3`
```html
<ul>
	<li>ul_li_1</li>
	<li>ul_li_2</li>
	<li>ul_li_3</li>
</ul>
```
적용시 아래와 같이 나타납니다.
<ul>
	<li>ul_li_1</li>
	<li>ul_li_2</li>
	<li>ul_li_3</li>
</ul>

## 4. a
- link element
- href 속성에 url을 넣습니다
- link도 크롤링의 대상으로 많이 사용됨
- 상대경로도 사용 가능
	- e.g. `<a href="01_html_basic.html">html_basic</a><br>`
 
- `target="_blank"` 속성을 넣어주면 새 탭을 띄워서 이동

```html
<a href="http://google.com">Google</a><br>
<a href="http://naver.com" target="_blank">Naver</a><br>
```
적용시 아래와 같이 나타납니다.
<a href="http://google.com">Google</a>
<a href="http://naver.com" target="_blank">Naver</a>



## 5. image
- src 속성: url을 넣음
- style 속성: size를 지정해줄 수 있음 (e.g. `style="width:200px;"`)
- alt 속성: 이미지가 없을 경우 뜨는 문자 (어떤 이미지인지 알려줄 수 있음) (alt 속성은 꼭 넣어야 함)

```html
<img style="width:200px;" src="http://cdn.www.fastcampus.co.kr/wp-content/uploads/2017/11/fastcampus_logo_positive-1.png" alt="패스트캠퍼스">
```
적용시 아래와 같이 나타납니다.
<img style="width:200px;" src="http://cdn.www.fastcampus.co.kr/wp-content/uploads/2017/11/fastcampus_logo_positive-1.png" alt="패스트캠퍼스">


## 6. iframe
- 외부 url 링크 페이지를 보여주기 위한 element
- 중고나라 네이버 카페 등에서 크롤링할 경우 필요
	- iframe 안으로 들어가서 element를 선택해서 데이터를 가져와야 함
```html
<iframe src="https://hyeshinoh.github.io/" width="600" height="400"></iframe>
```
적용시 아래와 같이 나타납니다.
<iframe src="https://hyeshinoh.github.io/" width="600" height="400"></iframe>



## 7. 입력(input) : text, password, radio, checkbox
- 크롤링할 때, 로그인을 하고 나서 이동한 페이지를 크롤링할 시 이용 가능

### 7.1 text, password
- placeholder 속성: 어떤 정보를 넣는지 알려줌
```html
<input type="text" name="" value="" placeholder="이메일">
<input type="password" name="" value="" placeholder="패스워드">
```
적용시 아래와 같이 나타납니다.
<input type="text" name="" value="" placeholder="이메일">
<input type="password" name="" value="" placeholder="패스워드"><br>

<span><h3>7.2 radio: 여러개 중에 선택하는 박스</h3></span>
<ul>
  <span><li>버튼은 name 속성의 값으로 그룹핑 (그룹핑되면 그 중에 택1하게 만들어짐)</li></span>
  <span><li>요즘에 웹 개발에선 많이 사용되지는 않음</li></span>
</ul>

```html
<input type="radio" name="radio_1" value="b1">버튼1</input>    
<input type="radio" name="radio_1" value="b2">버튼2</input><br>

<input type="radio" name="radio_2" value="b3">버튼3</input>
<input type="radio" name="radio_2" value="b3">버튼4</input>
<input type="radio" name="radio_2" value="b5">버튼5</input>
```
적용시 아래와 같이 나타납니다.
<input type="radio" name="radio_1" value="b1">버튼1</input>    
<input type="radio" name="radio_1" value="b2">버튼2</input><br>

<input type="radio" name="radio_2" value="b3">버튼3</input>
<input type="radio" name="radio_2" value="b3">버튼4</input>
<input type="radio" name="radio_2" value="b5">버튼5</input>

### 7.3 checkbox: 해당사항을 체크하는 박스
```html
<input type="checkbox" name="" value="c1"> 체크박스1</input>  
<input type="checkbox" name="" value="c2"> 체크박스2</input>
```
적용시 아래와 같이 나타납니다.
<input type="checkbox" name="" value="c1"> 체크박스1</input>
<input type="checkbox" name="" value="c2"> 체크박스2</input>


## 8. textarea
- 여러줄을 입력받는 element
- inputtext와 달리 여러줄을 입력할 수 있음
- `style="resize:none;"`을 넣어주면 크기가 고정됨
```html
<textarea name="name" cols="30" rows="10" style="resize:none;"></textarea>
```
적용시 아래와 같이 나타납니다.
<textarea name="name" cols="30" rows="10" style="resize:none;"></textarea>


## 9. select, option
- option 선택할 수 있는 dropdown element
```html
<select>
	<option value="1">option 1</option>
	<option value="2">option 2</option>
	<option value="3">option 3</option>
</select><br>
<!-- select>option[value=$][style=color:red]{option $}*3 -->
<select name="" id="">
	<option value="1" style="color:red">option 1</option>
	<option value="2" style="color:red">option 2</option>
	<option value="3" style="color:red">option 3</option>
</select>
```
적용시 아래와 같이 나타납니다.
<select>
	<option value="1">option 1</option>
	<option value="2">option 2</option>
	<option value="3">option 3</option>
</select><br>
<!-- select>option[value=$][style=color:red]{option $}*3 -->
<select name="" id="">
	<option value="1" style="color:red">option 1</option>
	<option value="2" style="color:red">option 2</option>
	<option value="3" style="color:red">option 3</option>
</select>

## 10. button
- onclick 속성: 클릭했을 때 event. javascript 코드를 넣어줄 수 있음
```html
<button type="button" name="button" onclick="javascript:(alert('alert msg'))">Click</button><br>
<button type="button" name="button" onclick="javascript:(location.href = 'http://naver.com')">네이버로 이동</button>
```
적용시 아래와 같이 나타납니다.
<button type="button" name="button" onclick="javascript:(alert('alert msg'))">Click</button>
<button type="button" name="button" onclick="javascript:(location.href='http://naver.com')">네이버로 이동</button>



#### 참고자료
- 패스트캠퍼스, ⟪데이터사이언스스쿨 8기⟫ 수업자료
