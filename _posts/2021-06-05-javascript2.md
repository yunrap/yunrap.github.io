---
title: 자바스크립트-3. 타입과 변수
date: 2021-06-05 11:33:00
categories: [Language, Javascript]
tags: [Javascript]
---

# 타입변환

var num = 20; <br>
num = "이십"; <br>
var num; //한변수에 여러번 대입할수는 있지만, 변수의 재선언은 할 수 없습니다. 즉 재선언문은 무시됩니다.

# 묵시적 타입 변환

자바스크립트는 특정 타입의 값을 기대하는곳에 다른 타입값이 오면 자동으로 타입을 변환하여 사용
즉, 문자열이 와야할 곳에 숫자가 오더라도 알아서 숫자를 문자열로 변환

10 + "문자열";  //문자열 연결을 위해 숫자 10이 문자열로 변환됨 <br>
"3" * "5"; // 곱셈 연산을 위해 두문자열이 모두 숫자로 변환됨 <br>
1 - "문자열" // NAN : 정의되지않은 값이나 표현할수 없는 값 <br>

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
    document.getElementById("result").innerHTML +=  //여기서의 +=은 body안의 내용의 누적을 상징한다.
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

Number("10") // 숫자 10 <br>
String(true) // 문자열 "true" <br>
Boolean(0); // 불리언 false <br>
Object(3); // 숫자 3 <br>


# 변수의 선언과 초기화
var month;  //변수의 선언 , undefined <br>
date = 35; <br>

선언된 변수는 나중에 초기화할수있고, 선언과 동시에 초기화 할수도 있다.
var month;          //변수의 선언 <br>
var date = 25;    // 변수의 선언과 동시에 초기화 <br>
month = 12;       //변수의 초기화 <br>

쉼표연산자를 이용하여 여러변수를 동시에 선언하거나 초기화 할 수 있다.
var month, date;                //여러 변수를 한번에 선언 <br>
var hours = 7, minutes = 15;    //여러 변수를 선언과 동시에 초기화 <br>
month = 10, date = 5;           //여러 변수를 한번에 초기화 <br>



# instanceof

피연산자의 객체가 특정 객체의 인스턴스인지 아닌지를 확인함
var str = new String("이것은 문자열입니다.");
str instanceof Object;   // true <br>
str instanceof String;  // true <br>
str instanceof Array; // false <br>
str instanceof Number; //false <br>


# void

어떤 타입의 값이 오던지 언제나 undefined 값만을 반환

<a href="javascript:void(0)"> 이링크는 동장하지 않습니다</a>


```html
<a href="javascript:void(0)"> 이 링크는 동작 않함.</a>
<br>
<a href="javascript:void(document.body.style.backgroundColor='yellow')">
    이링크도 동작하지 않지만, 배경식을 바꿔줌.
</a>
```

이렇게 쓰면 나중에 동작안할때를 처리해줄때 사용하면 좋다.


# 문제1 > getHours() 사용

```java
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!--현재 시간 new Date().getHours()
    	현재시간이 12시 이전이면 "Good Morning"
    	오후 6시이전이면 "Good Afternoon"
    	그렇지 않으면 "Good evening" alert창으로 출력
    -->
    <p id="hello"> dd</p>

    <script>

         var msg = "";
         var time = new Date().getHours();
         console.log(time);

         if(time < 12)
         {
             msg = "Good Morning";
         }
         else if(time < 18)
         {
             msg = "Good Afternoon";
         }
         else
         {
            msg = "Good evening";
         }

         alert(msg);
    </script>


</body>
</html>
```
  - 이렇게 time 변수에 getHours메소드를 사용하여 현재시간을 가져와 넘겨준다음

  - if문으로 처리하여 alert창을 띄어주는 문제를 만들어보았다.


# 숫자 맞추기 게임

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>숫자 맞추기</title>
<script>
    var computerNumber = 44;
    var gNumber = 0;

    function test1()
    {
        var number = parseInt(document.form1.user.value);
        gNumber++;
        alert(1);
        alert(number);

        if(number == computerNumber)
            {
                result= "성공입니다.";
            }
            else if(number < computerNumber)
            {
                result = "입력값이 작습니다.";
            }
            else
            {
                result = "입력값이 높습니다.";
            }

            document.form1.result.value = result;
            document.form1.guesses.value = gNumber;
    }



</script>
</head>
<body>
    <form name="form1">
    <h1>숫자 맞추기 게임</h1>
    이 게임은 컴퓨터가 생성한 숫자를 맞추는 게임입니다. 숫자는 1부터 100사이에 있습니다.
    <br>
    숫자:
    <input type="text" id="user" name="user" size="5">
    <input type="button" value="확인" onclick="test1();">
    <br>
    추측횟수: 
    <input type="text" id="guesses" name="guesses" size="5">
    힌트:
    <input type="text" id="result" name="result" size="16">
</body>
</form>
</html>
```

처음에 dom구조를 이해 못해서 숫자값을 이해하지 못했다.
dom구조를 더 공부해서 자유롭게 쓸수 있도록 해야겠다.

# document.write 사용 <while>
```html
<!DOCTYPE html>
<html>
    <head>
    <meta charset="UTF-8">
    <title>Insert title here</title>
    </head>
    <body>  

        <script>
            var i = 0;
            
            while(i<10)
            {
                document.write("카운트 : " , i , "<br>");
                i++;
            }

            /* 실행결과 
            	카운드 : 0
            	카운트 : 1
            	...
            	카운트 : 9
            */
        </script>
        
    </body>
</html>
```



# document.write 사용 <do ~while>
  
```html
<!DOCTYPE html>
<html>
    <head>
    <meta charset="UTF-8">
    <title>Insert title here</title>
    </head>
    <body>  

        <script>
            var i = 0;

            do
            {
                document.write("카운트 : " , i , "<br>");
                i++;
            }
            while(i<10);
          
            /* 실행결과 
            	카운드 : 0
            	카운트 : 1
            	...
            	카운트 : 9
            */
        </script>
        
    </body>
</html>
```

  
pattern 사용법 알아두자
  
# 표그리기 문제

  ```html
 <!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>구구단표</title>
</head>
<body>
<h1>구구단표</h1>
<table border="2" width="50%">

    <script>
        for(var i=1; i<=9; i++)
        {
            document.write("<tr>");
            document.write("<td>" + i + "</td>" );
            for(var j=2; j<9; j++)
            {
                document.write("<td>"+ i * j + "</td>");
            }
            document.write("</tr>");
        }
    </script>
</table>
</body>
</html>
```
  
innerHtml 로 할수있는법도 찾아보자 
