---
title: jsp_project-2. 회원가입화면 구현
date: 2021-07-12 11:33:00
categories: [Jsp, jsp_project]
tags: [jsp_project]
---


web.xml 문구 다시보기!!
icia.test링크로 접속하는것.


1. WEB-INF 안에 config파일에 log4j2.xml파일을 만든다.

이때  이것을 수정해야한다
```
<Property name="logPath">C:/project/webapps/localhost/src/main/webapp/WEB-INF/logs</Property>
<Property name="logArchivedPath">C:/project/webapps/localhost/src/main/webapp/WEB-INF/logs/archived</Property>
```
        
그후 logs파일에 archived 파일을 만들어준다.   
 


2. C:\project\webapps\localhost\src\main\webapp\WEB-INF 경로에

```
<!-- log4j2 환경 정보 시작  -->
	<context-param>
        <param-name>log4jConfiguration</param-name>
        <param-value>/WEB-INF/config/log4j2.xml</param-value>   
   </context-param>   
	<!-- log4j2 환경 정보 종료  --> 
```
  
 이문구를 넣어준다.
 PARAM-VALUE부분 경로 수정해줄것!
  

3. localhost/src/main/java/com/icia/web 경로에   filter 폴더이름을 추가해준다.


4. COM.ICIA.WEB.FILTER 부분에 파일 두개를 추가해준다.
HttpEncodingFilter
UrlUserAuthFilter



5. web.xml 부분에
```
   <!-- HTTP Encoding Filter 시작 -->
    <filter>
          <filter-name>httpEncodingFilter</filter-name>
          <filter-class>com.icia.web.filter.HttpEncodingFilter</filter-class>            
           <init-param>
                <param-name>encoding</param-name>
                <param-value>UTF-8</param-value>
           </init-param>
    </filter>
    <!-- HTTP Encoding Filter 종료 -->
    
    <!-- 사용자 인증 체크 Filter 시작 -->
    <filter>
          <filter-name>urlUserAuthFilter</filter-name>
          <filter-class>com.icia.web.filter.UrlUserAuthFilter</filter-class>            
           <init-param>
                <param-name>authUrl</param-name>
                <param-value>/board</param-value> <!-- 콤마(,) 구분으로 여러개 등록가능 ex) /board,/user -->
           </init-param>
    </filter>
    <!-- 사용자 인증 체크 Filter 종료 -->
    
    <!-- HTTP Encoding Filter Mapping 시작 --> 
    <filter-mapping>
        <filter-name>httpEncodingFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
    <!-- HTTP Encoding Filter Mapping 종료 --> 
    
    <!-- 사용자 인증 체크 Filter Mapping 시작 -->
    <filter-mapping>
        <filter-name>urlUserAuthFilter</filter-name>
        <url-pattern>*.jsp</url-pattern> <!-- 모든 jsp 파일  -->
    </filter-mapping>
    <!-- 사용자 인증 체크 Filter Mapping 종료 -->
    
    문구를 추가해준다.
    
```    
 6. 로그아웃구현을위해 logout.jsp 생성
 
 7. 아이디있나 없나 구현을위해 userIdCheckAjax  USER 폴더에생성

8. 회원가입 창 성공을위해 userProc USER 폴더에 생성
