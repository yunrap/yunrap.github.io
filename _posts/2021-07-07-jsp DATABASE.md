
---
title: jsp DATABASE
date : 2021-07-07 12:00:00
categories: [Language, jsp]
tags: [jsp]
---



# jsp 표현식 

변수나 메소드일때는 세미콜론을 사용하지않는다.

```
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
	<body>
<%
	int i = 0;
	while(true)
	{
		out.println(i + "번째 줄");
		i++;
%>

<br/>
================================================================
<br/>

<%
	if(i > 5)
		break;
	}
%>
	</body>
</html>
```

# JDBC 오라클 연동

1. JDBC 드라이버 로딩
2. DB 연결
3. PreparedStatement 객체생성



1. tomcat밑에 lib 폴더에 ojdbc5를 넣어줬다.



# index_jdbc.jsp파일

jsp파일을 만들어서

<포트포워딩>
String url = "jdbc:oracle:thin:@집 포트포워딩:1523:xe";


드라이버연결할때 oracle/product/11.2.0/server/jdbc/lib/ojdbc5를 복사한다.

```
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page import="java.sql.Connection" %>
<%@ page import="java.sql.DriverManager" %>

<%
boolean connection = false;
Connection conn = null;

String driver = "oracle.jdbc.driver.OracleDriver";
String url = "jdbc:oracle:thin:@localhost:1521:xe";

try
{
	Class.forName(driver);
	conn = DriverManager.getConnection(url, "iciauser", "1234");

	if(conn == null)
	{
		connection = false;
		System.out.println("DB연결 실패했습니다.");
	}
	else
	{
		connection = true;
		System.out.println("DB연결 성공했습니다.");
	}

}
catch(Exception e)
{
	connection = false;
	System.out.println("DB연결 실패.....");
	e.printStackTrace();  
}

%>

<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>JDBC TEST</title>
</head>
<body>
<%
	if(connection == true)
	{
%>
	<h1>연결되었습니다.</h1>
<%
	}
	else
	{
%>	
	<h1>연결실패입니다.</h1>
<%
	}
%>

</body>
</html>
```


# DATABASE
```
drop table bonus;
drop table dept;
drop table emp;
drop table salgrade;
drop table salgrade1;

--회원테이블
CREATE TABLE TBL_USER
(
    USER_ID VARCHAR2(20) NOT NULL,
    USER_PWD VARCHAR(20) NULL,
    USER_NAME VARCHAR2(30) NULL,
    USER_EMAIL VARCHAR2(50) NULL,
    STATUS CHAR(1) NULL,
    REG_DATE DATE NULL
);


COMMENT ON COLUMN TBL_USER.USER_ID IS '사용자 아이디';
COMMENT ON COLUMN TBL_USER.USER_PWD IS '비밀번호';
COMMENT ON COLUMN TBL_USER.USER_NAME IS '사용자 명';
COMMENT ON COLUMN TBL_USER.USER_EMAIL IS '사용자 이메일';
COMMENT ON COLUMN TBL_USER.STATUS IS '사용여부(Y:사용, N:정지)';
COMMENT ON COLUMN TBL_USER.REG_DATE IS '등록일';

CREATE UNIQUE INDEX PK_USER ON TBL_USER(USER_ID ASC); 
ALTER TABLE TBL_USER ADD CONSTRAINT PK_USER PRIMARY KEY(USER_ID);
-- PK_USER를 UNIQUE INDEX로 잡아준다.

-- ROWNUM , ROWID 알려달라고하기


--게시판 BBS_SEQ 시퀀스
CREATE SEQUENCE SEQ_BOARD 
INCREMENT BY 1
MAXVALUE 999999999999
MINVALUE 1
NOCACHE;

--게시판 생성
CREATE TABLE TBL_BOARD
(
    BBS_SEQ NUMBER(12) NOT NULL,
    USER_ID VARCHAR2(20) NULL,
    BBS_NAME VARCHAR2(50) NULL,
    BBS_EMAIL VARCHAR2(50) NULL,
    BBS_PWD VARCHAR2(10) NULL,
    BBS_TITLE VARCHAR2(150) NULL,
    BBS_CONTENT CLOB NULL,
    BBS_READ_CNT NUMBER(10) NULL,
    REG_DATE DATE NULL
);

COMMENT ON COLUMN TBL_BOARD.BBS_SEQ IS '게시물번호(시퀀스SEQ_BOARD)';
COMMENT ON COLUMN TBL_BOARD.USER_ID IS '사용자 아이디';
COMMENT ON COLUMN TBL_BOARD.BBS_NAME IS '게시자 이름';
COMMENT ON COLUMN TBL_BOARD.BBS_EMAIL IS '게시자 이메일';
COMMENT ON COLUMN TBL_BOARD.BBS_PWD IS '게시물 비밀번호';
COMMENT ON COLUMN TBL_BOARD.BBS_TITLE IS '게시물 제목';
COMMENT ON COLUMN TBL_BOARD.BBS_CONTENT IS '게시물 내용';
COMMENT ON COLUMN TBL_BOARD.BBS_READ_CNT IS '게시물 조회수';
COMMENT ON COLUMN TBL_BOARD.REG_DATE IS '게시물 등록일';

CREATE UNIQUE INDEX PK_BOARD ON TBL_BOARD(BBS_SEQ ASC);
ALTER TABLE TBL_BOARD ADD CONSTRAINT PK_BOARD PRIMARY KEY(BBS_SEQ);


```

