---
title: 자바스크립트-1. 
date: 2021-06-02 11:33:00
categories: [Language, Javascript]
tags: [Javascript]
---

# 자바스크립트 문법
  - var javascript = 10;
  - var Javascript = 10; 

대소문자가 다르면 서로다른 변수로 인식한다.

# 자바와 자바스크립트 특징

자바언어 : 변수의 타입을  반드시 선언해야함
자바스크립트 : 변수의 타입을 선언하지 않아도 사용가능

# 식별자 작성 방식

Camel Case 방식

: 첫번째 단어는 모두 소문자로, 그 다음단어부터는 첫문자만 대문자로 작성하는 방식


underscore case 방식
: 단어들을 언더바로 사용하는 방식


# 자바스크립트 출력

1. window.alert() 메서드
2. document.write() 메서드
3. console.log() 메서드


# html dom 요소를 이용한 innerHTML 프로퍼티

 getElementByID() 나 getElementsByTagName() 등의 메서드를 사용하여 HTML 요소를 선택함
 
 ```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>JAva Script</title>
</head>
<body>
	<h1>HTML DOM요소를 이용한 innerHTML</h1>
	
	<p id="text">현재 문장을 바꿀 것입니다.</p>
	
	<script>
		var str = document.getElementById("text");
		str.innerHTML = "이 문장으로 바뀌었습니다.";
		
		
		var now = new Date();
		document.write(now);
	</script>
	
	<input type="button" onClick="alert('반갑습니다.')" value="버튼 누르세요." />
</body>
</html>
```
인라인 자바스크립트 방식으로
1. button을 눌르면 onClick 메소드를 이용해서 alert창을 나타내게하는 방식


3.  getElementByID()로 id가 text를 찾아서 innerHTML로 그안에있는 내용을 바꾸게하는 방식을 사용하였다. 

# 객체 기본

자바스크립트의 실체 객체에 대해서 알아보자

처음으로 script 태그에
  
  var person = {} 

이렇게 초기화해주면 

  [object Object] 

라고 결과가 뜹니다.

그렇다면 이 오브젝트를 다음과 같이 고쳐봅시다.


```html
var person = {
  name: ['Bob', 'Smith'],
  age: 32,
  gender: 'male',
  interests: ['music', 'skiing'],
  bio: function() {
    alert(this.name[0] + ' ' + this.name[1] + ' is ' + this.age + ' years old. He likes ' + this.interests[0] + ' and ' + this.interests[1] + '.');
  },
  greeting: function() {
    alert('Hi! I\'m ' + this.name[0] + '.');
  }
};
```

```console
person.name
person.name[0]
person.age
person.interests[1]
person.bio()
person.greeting()
```

이렇게 객체에 포함된 데이터와 함수를 나타낼수있다.
문법의 형식은 이름과 값은 :
한쌍의 표현은 , 로 나타낸다

우리가 만든
  name: ['Bob', 'Smith'],
  age: 32,
  gender: 'male',
  interests: ['music', 'skiing'],
 이런요소들을 객체 리터럴이라고 불린다.


자바스크립트 undefined???? 중요하다


# === , !== 연산자, 삼항연산자
```html
	/*
	=== : 값과 타입이 모두 같으면 참
	!== : 값이나 타입이 다르면 참
	*/
	
	var x = 10;
	var y = 20;
	
	document.write("<br>");
	document.write((x === y) + "<br>");
	document.write((x !==y) + "<br>");

  var max_value = ( x > y ) ? x : y ; /*삼항연산자*/
	document.write("<br>" + max_value);
```

false
true
20

# prompt 함수

```html
//prompt() 함수 : 사용자한테 정보를 알려 입력을 받을때 사용
	var age = prompt("나이를 입력하세요.", "만나이로 입력.");  
```

visual code 플러그인
Bracket Pair Colorizer
Browser Preview
ESLint
indent-rainbow
JavaScript (ES6) code snippets
Live Server
Prettier - Code formatter
Quokka.js

# 덧셈 계산기
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Java script 연습</title>
    <script>
        function calc()
        {
            // id 값으로 사용
            // var x = document.getElementById("x").value;
            // var y = document.getElementById("y").value;
            
            //name으로 사용
            var x = document.form1.in_1.value;
            var y = document.form1.in_2.value;
            var sum;

            sum = parseInt(x) + parseInt(y);
            //document.getElementById("sum").value = sum;
            document.form1.sum.value = sum;
        }
    </script>
</head>
<body>
    <h1>덧셈 계산기</h1>
    <form name="form1" action="js_ex2.html" method="POST">
        첫번째 정수 : <input type="text" id="x" name="in_1"><br>
        두번째 정수 : <input type="text" id="y" name="in_2"><br>
        합계 :        <input type="text" id="sum" name="sum"><br>
        <input type="button" value="계산하기" onclick="calc();">
    </form>
</body>
</html>
```

getElementById("x") 할때 id값을 ""안에 넣어준다. 이문법을 잘기억해둔다

 


