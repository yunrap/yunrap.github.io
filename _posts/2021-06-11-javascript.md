# window 객체

모든 객체, 전역함수, 전역변수들은 자동으로 window 객체의 프로퍼티가 됨.
window 객체 메서드는 전역함수이며, window 객체의 프로퍼티는 전역 변수가 됨


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
    <form>
        <input type="button" value="구글 열기" onclick=
        "window.open('http://www.google.com', '_blank', width=300, height=300, true)" />
    </form>
</body>
</html>
```

# 매개변수의 다형성
