---
title: 자바스크립트-5. 
date : 2021-06-10 12:00:00
categories: [Language, Javascript]
tags: [Javascript]
---

# pattern

pattern을 눌러줬을때 동작이되지않아서 검색해본결과
pattern에서 사용하는 input 타입은 form에서 submit을 누를때 동작을하므로 
소스를 수정해주었다.

정규표현식을 사용할때는 submit을 잘 연동해서 사용하자

```html
<form name="form1" action="" method="get">
입력1 : <input id="number1" type="text" size=10 pattern=[0-9] required/><br />
입력2 : <input id="number2" type="text" size=10 /><br />
결과 : <input id="result" type="text" size=10 /><br />
  
<input type="submit" value="+" onclick="calc(1)" />   // 임시적으로 submit으로 바꿔줬다.
<input type="button" value="-" onclick="calc(2)" />
<input type="button" value="*" onclick="calc(3)" />
<input type="button" value="/" onclick="calc(4)" />
</form>
```

# number함수

문자열의 숫자를 number로 바꿔주는 역활

Number( ~.value    ) = 

대괄호안의 값이 없다면 Number는 0을 반환한다.

그렇다는 사실을 알고 

# try - catch문

try문에서 오류가생겼을때 catch문으로 간다

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>try~catch</title>
<script>
    var msg = "";
    function test()
    {
        try 
        {
            allert("hello world"); // 구문안에서 오류가발생했을때 catch문으로감
        }
        catch(error)
        {
            msg = "다음과 같은 오류가 발생 : " + error.message;
            alert(msg);
        }
    }
</script>

</head>
<body>
    <input type="button" value="try-catch테스트" onclick="test()">
</body>
</html>
```

1. 문법적인오류
2. 개발자가 예외로 던진다. 

두가지경우로 사용한다.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var result = 53;
        function test()
        {
            try
            {
                x = document.getElementById("number1").value;
                if(x == "") 
                {
                    throw "입력없음";
                }
                if(isNaN(x)) throw "숫자가 아님";
                if(x > result) throw "너무 큽니다";
                if(x < result) throw "너무 작습니다";
                if(x == result) throw "성공입니다";
            }
            catch(error) //throw값이 error변수에 담긴다
            {
               msg = document.getElementById("message");
               msg.innerHTML = "힌트 : " + error;
            }
        }

    </script>
</head>
<body>
<h1>Number Guess</h1>
<p>1부터 100 사이의 숫자를 입력하세요.</p>
<input type="text" name="number1" id="number1">
<input type="button" value="숫자 추측" onclick="test()">
<p id="message"></p>
</body>
</html>
```

# try ~ catch (throw추가)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>
        var result = 53;

        function test()
        {
            try
            {
                x = document.getElementById("number1").value;
              //  x = document.form1.number1.value.trim();  다큐먼트방식으로 가져오기
                if(x == "") 
                {
                    throw "입력없음";
                }
                if(isNaN(x)) throw "숫자가 아님";
                if(x > result) throw "너무 큽니다";
                if(x < result) throw "너무 작습니다";
                if(x == result) throw "성공입니다";
            }
            catch(error) //throw값이 error변수에 담긴다
            {
               msg = document.getElementById("message");
               msg.innerHTML = "힌트 : " + error;
            }
        }

    </script>
</head>
<form>
<body>
<h1>Number Guess</h1>
<p>1부터 100 사이의 숫자를 입력하세요.</p>
<input type="text" name="number1" id="number1">
<input type="button" value="숫자 추측" onclick="test()">
<p id="message"></p>
</body>
</form>
</html>
```


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script>

        // src값 얻어서 input처리
        // 전역변수로 1번일때 2번일때 
        function get()
        {
            var val = document.getElementById("ex").innerHTML;
            alert(val);
        }

        // function set(msg)
        // {
        //     document.getElementById("ex").innerHTML = msg;
        // }

        // function changeImage()
        // {
        //     document.getElementById("image").src = "../img/img2.jpg";
        // }


        //함수로 사용
        /*
         function changeImage()
         {
            var gab = document.getElementById("image").src;
            var logImg;
                if(gab == "file:///c%3A/sample/0610/img/img1.jpg")
                {
                    logImg =  "../img/img2.jpg";
                }
                else 
                {
                    logImg =  "../img/img1.jpg";
                }
            document.getElementById("image").src = logImg;
         }
         */
        
         // 대입과 ==을 잘 비교하자 
         var checkImg = 1;

         function changeImage()
        { 
            var logImg;
            if(checkImg == 1)
            {
                logImg =  "../img/img2.jpg";
                checkImg = 2;
            }
            else
            {
                logImg =  "../img/img1.jpg";
                checkImg = 1;
            }
            document.getElementById("image").src = logImg;
        }  

    </script>
</head>
<body>
    <div id="ex">여기가 div로 선언되었음.</div>
    <a href="javascript:get()">div요소 내용 출력하기</a>
    <br>
    <a href="#" onclick="set('변경되었습니다.')">div요소 내용 변경</a>

    <br><br>
    <img id="image" src="../img/img1.jpg" width="120" height="100">
    <input type="button" onclick="changeImage()" value="눌러보세요.">
</body>
</html>
```


