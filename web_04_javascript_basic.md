---
title: JavaScript - Basic
date: 2018-09-28 16:35:20
tags: 
- programming
- web
- javascript
categories: 
- Programming 공부
- Web 공부
---



# 1. JavaScript 
## 1.1 JavaScript란
- JavaScript란 객체 기반의 스크립트 프로그래밍 언어로, 웹 브라우저 내에서 주로 사용
- HTML, CSS와 함께 웹을 지탱하는 계층 구조에서 많은 역할을 차지
	- HTML 은 웹 페이지상에서 문단, 제목, 표, 이미지, 동영상등을 정의하고 그 구조와 의미를 부여하는 마크업 언어
	- CSS 는 배경색, 폰트, 컨텐츠의 레이아웃등을 지정하여, HTML 컨텐츠를 꾸며주는 스타일 규칙 언어
	- JavaScript 는 동적으로 컨텐츠를 바꾸고, 멀티미디어를 다루고, 움직이는 이미지등 웹 페이지를 꾸며주도록 하는 프로그래밍 언어
	- 출처: [MDN web docs](https://developer.mozilla.org/ko/docs/Learn/JavaScript/First_steps/What_is_JavaScript)
- JavaScript는 자유도가 높은 언어로 규칙에 조금 어긋나는 코드도 실행이됨 (error가 생길수는 있음)
- javascript package 관리 매니져(npm)인 nodejs를 설치할 것


# 2. JavaScript Basic Syntax

- JavaScript 주석처리
	- 한줄 주석: `// code`
	- 여러줄 주석: `/* code ... */`

## 2.1 출력

```javascript
console.log("print")
```
	print

- 이 외에도 여러가지 방법이 있음


## 2.2 식별자 규칙 (사용하는 곳마다 차이 존재)
- 상수명: snake_case(대문자)
- 변수명: camelCase 많이 사용
- 모듈: PascalCase
- 많이 쓰이는 convention: google js style, airbnb js style 등
```javascript
var TOTAL_COUNT = 50;
var firstName = "Doojin",
	lastName = "Park";
```

## 2.3 변수 선언

```javascript
var a = 1;
var b =2;
console.log(a + b);
```
	3

## 2.4 연산자
- `+`, `-`, `*`, `/`, `%`, `++`, `--` (제곱이 없음)
- `++` & `--`: 다른 언어에서도 사용되는 연산자

```javascript
var a = 5;
var result = a++;   // a 가 result로 대입되고 1 증가
console.log(a, result);  

var a = 5;
var result = ++a;   // a를 1 증가시키고 result에 대입
console.log(a, result);    
```
	6 5
   	6 6
    
   
## 2.5 데이터 타입
- 동적타이핑: 변수를 선언할 때 값에 따라 데이터 타입이 나중에 설정

```javascript
var a = 1,           // number
b = 1.9,             // number
c = "data",          // string
d = [1,2,3],         // object
e = {"a":1, "b":2},  // object
f = true,            // boolean
g = false;           // boolean
console.log(typeof a, typeof b, typeof c, typeof d,
    typeof e , typeof f, typeof g);
```
	number number string object object boolean boolean
    
    
## 2.6 null, undefined, NaN
- null: 변수에 값이 없음을 정의
- undefined: 값이 지정되지 않음
- NaN: 존재하지 않는 데이터

```javascript
var a = null;
console.log(a); // 값이 없음을 지정
var b;
console.log(b); // 값이 지정되지 않음
var c = 0/0;
console.log(c); // 존재하지 않는 데이터 형태
```
	null
	undefined
	NaN
    
## 2.7 비교 연산자: <, >, >=, <=, ==, !=, ===, !==
### 1) `==` & `===`: 값을 비교
- `==`와 `===`의 차이: `===`는 데이터타입까지 비교
- `===` 사용 권장

```javascript
console.log(1==1); // true
console.log(1=='1'); // true
console.log(1===1); // true
console.log(1==='1'); // false
```
	true
	true
	true
	false


### 2) `!=`, `<`, `>`, `<=`, `>=`: 값을 비교
- `'==` 사용시 데이터타입까지 비교

```javascript
console.log(1!=1); // false
console.log(1!='1'); // false
console.log(1!==1); // false
console.log(1!=='1'); // true
console.log(1>2); // fasle
console.log(1<2); // true
console.log(1>=1); // true
console.log(1<=2); // true
```
	false
    false
    false
    true
    false
    true
    true
    true

### 3) NaN은 비교연산으로 사용되지 않음
- 비교연산에서 어느 한쪽이 NaN이면 무조건 false

```javascript
console.log(NaN===NaN);
console.log(NaN==NaN);
```
    false
    false


## 2.8 할당 연산자

```javascript
var a = 1;
a += 2;
console.log(a);	// 3
a -= 1;
console.log(a);	// 2
a *= 6;
console.log(a);	// 12
a /= 2;
console.log(a);	// 6
a %= 5;
console.log(a);	// 1
```
    3
    2
    12
    6
    1

## 2.9 논리 연산자
- `&&` : 모두 참일때 참 (and)

```javascript
console.log(true && true); // true
console.log(true && false); // false
console.log(false && false); // false
```
    true
    false
    false

- `||` : 하나라도 참이면 참 (or)

```javascript
console.log(true || true); // true
console.log(true || false); // true
console.log(false || false); // false
```
    true
    true
    false


# 3. Condition - 조건문

## 3.1 if, else if, else
- 문법: `if(조건){code} else if(조건){code} else{code}`

```javascript
if(true){
  console.log("hello javascript");
}

if(false){
  console.log("hello javascript");
} else {
  console.log("hello datascience");
}

if(false){
  console.log("hello javascript");
} else if(true){
  console.log("hello html");
} else {
  console.log("hello datascience");
}
```
	hello javascript
	hello datascience
	hello html

## 3.2 false로 간주되는 데이터형

```javascript
if(null || undefined || NaN || 0 || ""){
console.log("hello true");
} else{
console.log("hello false")
}
```
	hello false
    
## 3.3 true로 간주되는 데이터형
- `[]`, `{}` (비어있는 object) - 객체이기 때문
	- python에서는 False였음

```javascript
if([] && {}){
console.log("hello true");
}
```
	hello true

## Quiz: 점수를 입력하면 학점이 나오는 코드를 작성하시오

```javascript
var point = 76;
var result = "";

if(point >= 90){
  result = 'A';
} else if(point >= 80){
  result = 'B';
} else if(point >= 70){
  result = 'C';
} else if(point >= 60){
  result = 'D';
} else {
  result = 'F';
}

console.log(result); //'C'
```
	C


# 4. Loop - 반복문: while, for, do while(실제로 거의 사용x)

## 4.1 while

```javascript
var a = 0;
while(a < 5){
    a++;
    console.log(a);
}
```
    1
    2
    3
    4
    5

```javascript
var a = 0;
while(true){
    a++;
    if(a === 3){
        continue;   // 3은 console.log가 되지 않음
    } else if (a >= 5){
        break;
    }
console.log(a);
}
```
    1
    2
    4


## 4.2 for
- python: iterable data 갯수만큼 반복
- js: for(초기값; 조건; 증감)
- in: es6에서 추가됨 (es6에 class, 화살표함수(=lambda) 등 추가)
	- es6를 사용할 경우 버전이 낮은 ie에서는 제대로 동작하지 않을 수 있음    

```javascript
for(var i = 0; i < 5; i++){
console.log(i);
}
```
    0
    1
    2
    3
    4


# 5. Array - 배열

## 5.1 배열 선언

```javascript
var arr = ['a','b','c','d','e'];
```

## 5.2 특정 위치 데이터 가져오기

```javascript
console.log(arr[2]);  
```
	c

## 5.3 배열의 크기 (length)

```javascript
console.log(arr.length);
```
	5

## 5.4 배열 추가
- `unshift()`: 맨 앞에 추가 
- `push()`: 맨 뒤에 추가  

```javascript
arr.push('f'); 
console.log(arr);
arr.unshift('z'); 
console.log(arr);
```
	[ 'a', 'b', 'c', 'd', 'e', 'f' ]
	[ 'z', 'a', 'b', 'c', 'd', 'e', 'f' ]

## 5.5 제거
- `shift()`: 첫번째 배열 제거
- `pop()`: 마지막 배열 제거   

```javascript
arr.shift(); 
console.log(arr);
arr.pop();
console.log(arr);
```
	[ 'a', 'b', 'c', 'd', 'e', 'f' ]
	[ 'a', 'b', 'c', 'd', 'e' ]


## 5.6 정렬
- `reverse()`: 역순으로 정렬
- `sort()`: 오름차순으로 정렬  

```javascript
arr.reverse(); 
console.log(arr);
arr.sort(); 
console.log(arr);
```
	[ 'e', 'd', 'c', 'b', 'a' ]
	[ 'a', 'b', 'c', 'd', 'e' ]

## 5.7 배열 자르기

```javascript
var arr2 = arr.splice(2,3); // 2번에서 3개 자름
console.log(arr, arr.length);

delete arr[2]; // 2번이 삭제 하지만 데이터만 삭제, 공간은 남아있음
console.log(arr, arr.length);
```
    [ 'a', 'b' ] 2
    [ 'a', 'b' ] 2

## 5.8 배열 데이터 하나씩 사용하기

```javascript
for(var i = 0; i < arr.length; i++){
console.log(arr[i]);
}
```
    a
    b

#### 참고자료
- 패스트캠퍼스, ⟪데이터사이언스스쿨 8기⟫ 수업자료
