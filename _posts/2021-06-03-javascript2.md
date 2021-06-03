---
title: 자바스크립트-2. 타입과 변수
date: 2021-06-03 11:33:00
categories: [Language, Javascript]
tags: [Javascript]
---

# 타입변환

var num = 20;
num = "이십"; 
var num; //한변수에 여러번 대입할수는 있지만, 변수의 재선언은 할 수 없습니다. 즉 재선언문은 무시됩니다.

# 묵시적 타입 변환

자바스크립트는 특정 타입의 값을 기대하는곳에 다른 타입값이 오면 자동으로 타입을 변환하여 사용
즉, 문자열이 와야할 곳에 숫자가 오더라도 알아서 숫자를 문자열로 변환

10 + "문자열";  //문자열 연결을 위해 숫자 10이 문자열로 변환됨
"3" * "5"; // 곱셈 연산을 위해 두문자열이 모두 숫자로 변환됨
1 - "문자열" // NAN : 정의되지않은 값이나 표현할수 없는 값

```html
<!DOCTYPE html>
<html lang="en">
    <script src="javascript-1.js"></script>
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>묵시적타입변환</h1>
    <p id="result"></p>
    
    <script>
    var result = 10 + "문자열";
    document.getElementById("result").innerHTML = 
        result + "<br>";
    result = "3" * "5";
    document.getElementById("result").innerHTML += 
        result + "<br>";
    result = 1 - "문자열";
    document.getElementById("result").innerHTML +=
        result;
    </script>
    
</body>
</html>
```


# 명시적 타입 변환

명시적 타입 변환을 위해 자바 스크립트가 제공하는 전역함수

Number("10") // 숫자 10
String(true) // 문자열 "true"
Boolean(0); // 불리언 false
Object(3); // 숫자 3

# 변수의 선언과 초기화
var month;  //변수의 선언 , undefined
date = 35;

선언된 변수는 나중에 초기화할수있고, 선언과 동시에 초기화 할수도 있다.
var month;          //변수의 선언
var date = 25;    // 변수의 선언과 동시에 초기화
month = 12;       //변수의 초기화

쉼표연산자를 이용하여 여러변수를 동시에 선언하거나 초기화 할 수 있다.
var month, date;                //여러 변수를 한번에 선언
var hours = 7, minutes = 15;    //여러 변수를 선언과 동시에 초기화
month = 10, date = 5;           //여러 변수를 한번에 초기화


