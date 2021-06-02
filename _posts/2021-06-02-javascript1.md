---
title: 자바스크립트-1. 
date: 2021-06-02 11:33:00
categories: [Language, Javascript]
tags: [Javascript]
---

# 자바스크립트 문법
var javascript = 10;
var Javascript = 10; 

대소문자가 다르면 서로다른 변수로 인식한다.

# 자바와 자바스크립트 특징

자바언어 : 변수의 타입을 반드시 선언해야함
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
