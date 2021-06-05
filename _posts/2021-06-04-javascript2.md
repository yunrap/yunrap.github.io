---
title: 자바스크립트-3. DOM 탐색하기
date: 2021-06-04 11:33:00
categories: [Language, Javascript]
tags: [Javascript]
---

자바스크립트를 공부하던중 dom 접근을 제대로 하지못해서
테이블을 만들지 못했던 경험이있다.

그래서 dom 접근방식에대해 포스팅할려고한다.


# DOM 탐색하기

## <body> = document.body
 
  - document.body는 <body> 를 표현하는말로, 자주 쓰이는 노드 중하나입니다.
  
  
```html
<html>

<head>
  <script>
    alert( "HEAD: " + document.body ); // null, 아직 <body>에 해당하는 노드가 생성되지 않았음
  </script>
</head>

<body>
  <script>
    alert( "BODY: " + document.body ); // HTMLBodyElement, 지금은 노드가 존재하므로 읽을 수 있음
  </script>
</body>
</html>
```
  
## childNodes, firstChild, lastChild
  
  ### 자식노드 탐색하기
  
  자식노드는 바로 아래의 자식 요소를 나타냅니다. 
