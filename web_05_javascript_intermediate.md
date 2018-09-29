---
title: JavaScript - Intermediate
date: 2018-09-28 18:01:24
tags: 
- programming
- web
- javascript
categories: 
- Programming 공부
- Web 공부
---

# 1. Object(객체)
- python에서 class로 만드는 객체와 같은 의미
- python에서 dict type과도 같은 의미

## 1.1 객체 생성
- 가장 많이 쓰는 방법 (obj를 만들고 나서 값들을 하나씩 넣어줌)  

```javascript
var obj = {};   // 다음과 동일: var obj = new Object();
obj.name = "hyeshin";
    // obj['addr'] = "seoul" 이런식으로도 가능하긴 함(더 좋진 x)
obj.math = 92;
obj.english = 97;
obj.science = 85;
console.log(obj);
console.log(obj.english);
```
	{ name: 'hyeshin', math: 92, english: 97, science: 85 }
	97

- 다른 방법: 객체를 리터럴로 선언한다
	- 리터럴: 변수에 대입해주는 값  

```javascript
var obj2 = {
    name: "Jin",      // key는 ""없어도 자동으로 문자열로 들어감
    addr: "seoul",    // js는 마지막 ',' 쓰면 낮은 ie에서 오류 가능성
    skill: function(){
        console.log("coding");
    }
};   // key값은 문자열만 가능
```

## 1.2 객체 출력
```javascript
for(var key in obj2){
  console.log(key, obj2[key]);
}
```
	name Jin
	addr seoul
	skill function(){
	        console.log("coding");
	    }

## 1.3 객체에 함수 담기
- Object.keys : 객체의 키값 리스트로 가져오기
- toFixed(number) : 반올림해서 number 자리수까지 출력

```javascript
var pointsObj = {
    'points':{'math': 91, 'science': 98, 'english': 86},
    'total': function(){
        var total = 0;
        for(var key in this.points){
            total += this.points[key];
        }
        return total;
    },
    'avg': function(){
            return this.total() / Object.keys(this.points).length;
    }
};

console.log(pointsObj);
console.log(pointsObj.total());
console.log(pointsObj.avg());
console.log(pointsObj.avg().toFixed(2));
```
	{ points: { math: 91, science: 98, english: 86 },	
	  total: [Function: total],
	  avg: [Function: avg] }
	275
	91.66666666666667
	91.67


# 2. function - 함수

## 2.1 선언 및 호출
```javascript
function sum(a, b){
  return a + b;
}
var result = sum(3, 5);
console.log(result);
```
	8

## 2.2 함수를 변수에 담아서 선언
- hoisting: 변수를 선언하면 해당 scope의 최상단으로 올라감  

```javascript
var minus = function(a, b){
  return a - b;
};

var result = minus(3, 5);
console.log(result);
console.log(typeof minus);
```
	-2
	function



# 3. Scope
- python의 scope와 같은 개념
- 함수 안에서 local 변수를 var를 사용해서 선언  

```javascript
var a = 'hello';    // global 변수 선언
function disp(){
  var a = "world";  // local 변수 선언
  console.log(a);
}

disp();
console.log(a);
```
	world
	hello

- var를 안 써주면 global 변수에 접근  

```javascript
var a = 'hello';    // global 변수 선언
function disp(){
  a = "world";      // global 변수에 접근
  console.log(a);
}

disp();
console.log(a);
```
	world
	world


# 4. 즉시실행함수, 익명함수
- 즉시실행함수: 함수를 선언함과 동시에 실행함
- 사용하는 이유
	- javascript는 frontend 언어로 코드가 browser에 공개됨
	- 서비스에 접속한 이용자가 전역 함수를 실행할 수 있음
	- 이로 인해 보안에 문제가 생길 수 있으므로 모든 함수나 변수를 지역 함수/변수로 선언  

```javascript
// 아무 것도 실행되지 않음
(function(){

})
```
```javascript
// 함수를 선언하는 동시에 function 안의 코드를 실행시킴
(function(){
  console.log("data");
})();
```
	data

```jacascript
// disp함수를 즉시실행
// disp는 지역함수가 되어 글로벌 영역에서 맘대로 쓸 수 없게 됨
(function(){
  var name = "hyeshin";
  function disp(){
    console.log(name);
  }
  disp();
})();
```
	hyeshin

![image](web_05_javascript_intermediate/IMG_2911.jpg)


# 5. Module pattern
- 실제로 JavaScript에서 module을 사용하는 방법 중 하나
- JavaScript는 class가 없는데 OOP로 코딩해야 함<br>(캡슐화, 추상화, 은닉화 개념 사용)
- getter, setter 구현

## 5.1 모듈 객체 변수 선언
- Module이라는 변수가 있으면 Module이 Module에 대입, 없으면 빈 객체를 만듦  

```javascript
var Module = Module || {};
```
- 즉시실행함수로 parameter로 module을 던지고 argument로 `_module`을 받음<br> <i>(복습하며 보니 parameter와 argument가 바뀐 듯 한데???) </i>
```javascript
(function(_Module){
  var _name = "hyeshin";   // private이므로 _를 붙임

  _Module.getName = function(){
    return _name;
  };

  _Module.setName = function(name){
    _name = name;
  };

})(Module);

console.log(Module.getName());
console.log(Module._name);    // 접근 불가
```
	hyeshin
	undefined

JavaScript를 더 깊이 공부하고 싶다면(중급 수준)
- closure 클로져, prototype 개념을 추가적으로 공부
- 웹서비스 개발은 jquery를 공부하여 구현 가능할 것


# 6. callback - 콜백함수
- callback은 모든 언어에서 사용되는 용어
- 함수에서 argument로 함수를 받아서 함수 안의 코드가 다 수행된 후에 argument로 받은 함수를 수행
- 여기서 argument로 받은 함수를 콜백함수라고 함

```javascript
function add(a, b, callback){
    var result = a + b;
    callback(result);	//callback으로 받은 함수를 마지막에 실행
}

function disp(result){
    console.log(result);
}

function sq(result){
    console.log(result*result);
}


var result = add(2, 3, disp); 
console.log(result);

var result = add(2, 3, sq);
console.log(result);
```
	5
    undefined
    25
    undefined
    
- 웹에서 비동기 통신을 할때 많이 사용됨  
- api를 주고 받을 때 주로 사용
	- api: request, response → 마지막으로 callback 함수를 수행
	![image](web_05_javascript_intermediate/IMG_2910.jpg)



#### 참고자료
- 패스트캠퍼스, ⟪데이터사이언스스쿨 8기⟫ 수업자료

