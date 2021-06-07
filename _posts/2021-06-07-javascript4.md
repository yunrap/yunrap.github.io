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

# for in 문



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







