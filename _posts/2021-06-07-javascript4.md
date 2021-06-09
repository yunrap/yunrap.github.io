---
title: 자바스크립트-4. 
date : 2021-06-07 12:00:00
categories: [Language, Javascript]
tags: [Javascript]
---

# do~while문 프린트하기

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
   <!-- do~while 문 사용
    출력에 ) 카운터 : 0
            ...
            카운터 : 9-->
        <script>
            var i = 0;
            do
            {
                document.write("카운터 : " + i +"<p>"); 
                i++;
            }while(i<10)
        </script>
</body>
</html>
```

# label 문

label문을 사용하면 break 문과 continue문의 동작이 프로그램의 흐름을 특정영역으로 이동한다.

continue 라벨이름;
break 라벨이름;

# 배열

var arrList = [1, true, "javascript"];
var arrObj = Array[1, true, "javascript"];
var arrNewObj = new Array(1, true, "javascript");

이렇게 세개의 방식으로 사용한다.

함수내부에서 var 키워드를 사용하지 않고 변수를 선언하면, 해당 변수는 전역변수로 선언됨

전역변수와 같은 이름의 지역변수 선언시 함수내에서는 지역 변수만을 호출 할 수 있음

함수내에 전역변수에 접근할려면 window.전역변수면 가능하다



## 연관배열

```javascript
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
  <body>
  <script>
  //연관배열
  var fruits = new Array();
  fruits['a'] = '사과';
  fruits['b'] = '포도';
  fruits['c'] = '오렌지';

  document.write(fruits['a'] + "<br />");
  document.write(fruits['b'] + "<br />");
  document.write(fruits['c'] + "<br />");
  </script>
  </body>
</html>
```

# input박스 접근하기

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>

<script>
function init()
{
	for(var i = 0; i < 3; i++)
	{
		document.form1["a" +i].value = i;
	}
}
</script>

</head>
<body>
  <form name="form1">
    필드1<input type="text" name="a0" /><br />
    필드2<input type="text" name="a1" /><br />
    필드3<input type="text" name="a2" /><br />
    <input type="button" value="초기화" onclick="init();" />
  </form>

  <br /><br />
  <input type="button" value="눌러보세요!" onclick="greeting('홍길동', '사원');" />
  <br /><br />
</body>
</html>
```


# 전역변수, 지역변수

전역변수, 지역볁수가있으면 일반적으로 지역변수를 먼저 선정한다.
하지만 전역변수로 접근하고 싶을땐 window.변수명 으로 접근한다.

```javascript
var num = 10;

function globalNum()
{
var num = 20;
document.write("함수 내부에 num: " + num + "<br />");    //20 (지역변수호출)
document.write("전역변수 값은 " + window.num + "<br />");   //10 (전역변수호출)
}

globalNum();
document.write("함수 밖에서 num: " + num);
```

# 매개변수 (맞지않는 매개변수 개수)

- 타입의따로 명시하지않고, 
- 매개변수보다 적은인수가 전달되더라도 오류발생x


```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<script>
    function addNum(x, y, z)
    {
        return x + y + z;
    }
</script>
<body>
    <script>
        document.write(addNum(1,2,3));
        document.write("<br>");
        document.write(addNum(1,2));
        document.write("<br>");
        document.write(addNum(1))
    </script>
</body>
</html>
```

```console
6
NaN
NaN
```

만약 매개변수가 (1,2) 두개를 던져준다면 (x, y, z) 중 
z변수는 undefined가되어서 document.write를찍어주면 NaN 값이된다.

# 매개변수 (맞지않는 매개변수 개수) ,수정

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>매개변수</title>
</head>
<script>
    function addNum(x, y, z)
    {
       
        if(x === undefined) // === 데이터타입도 같고 값도같아야한다
        {
            x = 0;
        }
        if(y === undefined)
        {
            y = 0;
        }
        if(z === undefined)
        {
            z = 0;
        }
        return x + y + z;
        
    }
</script>
<body>
    <script>
        document.write(addNum(1,2,3));
        document.write("<br>");
        document.write(addNum(1,2));
        document.write("<br>");
        document.write(addNum(1))
        document.write("<br>");
        document.write(addNum())
    </script>
</body>
</html>
```

이렇게 예외처리를 해준다면 값이 비어있지않아 제대로된값을 호출할수있다.


# Arguments 객체

위의처럼 매개변수를 직접정의하지않아도 arguments객체를 사용하면
가변적으로 사용이가능하다


```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<script>
    function nihao()
    {
        var sum = 0;
        for(var i = 0; i< arguments.length; i++)
        {
            sum += arguments[i];
        }
        return sum;
    }
</script>
<body>
    <script>
        document.write(nihao(3,4) + "<br>");
        document.write(nihao(3,4,4,5) + "<br>");
        document.write(nihao(0));
    </script>
</body>
</html>
```


# String 메서드

특정문자나 문자열이 처음으로 등장하는 위치, 마지막등장위치를 반환함

indexOf()
lastIndexOf()
전달 문자열을 찻을 수 없을때는 -1을 반환함


```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<script>
    function nihao()
    {
        var sum = 0;
        for(var i = 0; i< arguments.length; i++)
        {
            sum += arguments[i];
           
        }
         return sum;
    }
</script>
<body>
    <script>
        var str = "abcDEFabc";

        document.write(str.indexOf('abc') + "<br>");
        document.write(str.indexOf('abcd') + "<br>");
        document.write(str.indexOf('abc', 3) + "<br>");
        document.write(str.lastIndexOf('abc') + "<br>");
        document.write(str.lastIndexOf('d') + "<br>");
        document.write(str.lastIndexOf('c') + "<br>");

    </script>
</body>
</html>
```

```console
```


# charAt() , charCodeAt(), charPointAt()

 String 인스턴스에서 전달받은 위치한 문자나 문자코드반환
 이소스는 그냥넘어가도록한다
 
 
# slice() , substring(), substr()

 slice(2,6) : 인덴스2부터 인덱스 5까지의 문자열을 추출함
 slice(-4,-2) : 문자열의 뒤에서부터 추출함
 slice(2) : 문자열의 마지막까지 추출함
 substring(2,6) : 2번째부터 6번째 자리수까지 가져와
 substr(2,4) : 2번째부터 4개가져와
 
 ```javascript
 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        var str = "abcDEFabc";
        document.write("문자열 추출<br />");
        document.write(str.slice(2,6) + "<br>");
        document.write(str.slice(-4,-2) + "<br>");
        document.write(str.slice(2) + "<br>");
        document.write(str.substring(2,6) + "<br>"); //2번째부터 5번째까지 가져와라
        document.write(str.substr(2,4) + "<br>"); // 2번째자리에서 4개를 가져와라

        var str2 = "        java script         ";
        document.write(str2.trim() + "<br>"); // 맨앞과 맨뒤의 공백제거
    </script>
</body>
</html>
 ```
 
 ```console
문자열 추출
cDEF
Fa
cDEFabc
cDEF
cDEF
java script
 ```
 
 많이쓰이므로 이내용은 꼭 숙지하고 넘어가야한다.
 
 
 # Split() 메서드
 
 
 공백, !, 으로 문자열을 쪼개는것이다.
 
 ```javascript
  var str3 = "Java! Script!";
  document.write(str3.split() + "<br>");
  document.write(str3.split("") + "<br>");
  document.write(str3.split(" ") + "<br>");
  document.write(str3.split("!") + "<br>");
 ```
 
```console
Script!
J,a,v,a,!, ,S,c,r,i,p,t,!
Java!,Script!
Java, Script,
```
 
 
 # for of 와 for in문의 차이점


# 유사배열

 배열과 유사한 객체를 유사배열이라 한다.
 
 조건
 1. 숫자 형태 index가 있어햐한다.
 2. length 프로퍼티가있다.
 3. 배열의 기본 메소드를 사용할 수 없다
 4. Array.isArray(유사배열) == false
 5. 
 유사배열은 배열과 비슷하지만 배열이 아니기 때문에 false를 리턴한다
 
 
# 이터레이터
컬렉션을 반복할 수 있게 하는 객체



 
 
 
