---
title: spring_project-2. 
date: 2021-07-22 11:33:00
categories: [Project, spring_project]
tags: [spring_project]
---

# 회원가입 화면만들기

```
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ include file="/WEB-INF/views/include/taglib.jsp" %>
<!DOCTYPE html>
<html>
<head>
<%@ include file="/WEB-INF/views/include/head.jsp" %>
<script type="text/javascript">
$(document).ready(function() {
    
	$("#userId").focus();
	
	$("#btnReg").on("click", function() {
		
		// 모든 공백 체크 정규식
		var emptCheck = /\s/g;
		// 영문 대소문자, 숫자로만 이루어진 4~12자리 정규식
		var idPwCheck = /^[a-zA-Z0-9]{4,12}$/;
				
		if($.trim($("#userId").val()).length <= 0)
		{
			alert("사용자 아이디를 입력하세요.");
			$("#userId").val("");
			$("#userId").focus();
			return;
		}
		
		if (emptCheck.test($("#userId").val())) 
		{
			alert("사용자 아이디는 공백을 포함할 수 없습니다.");
			$("#userId").focus();
			return;
		}
		
		if (!idPwCheck.test($("#userId").val())) 
		{
			alert("사용자 아이디는 4~12자의 영문 대소문자와 숫자로만 입력하세요");
			$("#userId").focus();
			return;
		}
		
		if($.trim($("#userPwd1").val()).length <= 0)
		{
			alert("비밀번호를 입력하세요.");
			$("#userPwd1").val("");
			$("#userPwd1").focus();
			return;
		}
		
		if (emptCheck.test($("#userPwd1").val())) 
		{
			alert("비밀번호는 공백을 포함할 수 없습니다.");
			$("#userPwd1").focus();
			return;
		}
		
		if (!idPwCheck.test($("#userPwd1").val())) 
		{
			alert("비밀번호는 영문 대소문자와 숫자로 4~12자리 입니다.");
			$("#userPwd1").focus();
			return;
		}
		
		if ($("#userPwd1").val() != $("#userPwd2").val()) 
		{
			alert("비밀번호가 일치하지 않습니다.");
			$("#userPwd2").focus();
			return;
		}
		
		if($.trim($("#userName").val()).length <= 0)
		{
			alert("사용자 이름을 입력하세요.");
			$("#userName").val("");
			$("#userName").focus();
			return;
		}
		
		if(!fn_validateEmail($("#userEmail").val()))
		{
			alert("사용자 이메일 형식이 올바르지 않습니다.");
			$("#userEmail").focus();
			return;	
		}
		
		$("#userPwd").val($("#userPwd1").val());
		

		//ajax
	});
});

function fn_userReg()
{
	//ajax
}

function fn_validateEmail(value)
{
	var emailReg = /^([\w-\.]+@([\w-]+\.)+[\w-]{2,4})?$/;
	
	return emailReg.test(value);
}
</script>
</head>
<body>
<%@ include file="/WEB-INF/views/include/navigation.jsp" %>
<div class="container">
    <div class="row mt-5">
    	<h1>회원가입</h1>
    </div>
    <div class="row mt-2">
        <div class="col-12">
            <form id="regForm" method="post">
                <div class="form-group">
                    <label for="username">사용자 아이디</label>
                    <input type="text" class="form-control" id="userId" name="userId" placeholder="사용자 아이디" maxlength="12" />
                </div>
                <div class="form-group">
                    <label for="userPwd1">비밀번호</label>
                    <input type="password" class="form-control" id="userPwd1" name="userPwd1" placeholder="비밀번호" maxlength="12" />
                </div>
                <div class="form-group">
                    <label for="userPwd2">비밀번호 확인</label>
                    <input type="password" class="form-control" id="userPwd2" name="userPwd2" placeholder="비밀번호 확인" maxlength="12" />
                </div>
                <div class="form-group">
                    <label for="userName">사용자 이름</label>
                    <input type="text" class="form-control" id="userName" name="userName" placeholder="사용자 이름" maxlength="15" />
                </div>
                <div class="form-group">
                    <label for="userEmail">사용자 이메일</label>
                    <input type="text" class="form-control" id="userEmail" name="userEmail" placeholder="사용자 이메일" maxlength="30" />
                </div>
                <input type="hidden" id="userPwd" name="userPwd" value="" />
                <button type="button" id="btnReg" class="btn btn-primary">등록</button>
            </form>
        </div>
    </div>
</div>
</body>
</html>
```



# 회원가입 컨트롤러 구현하기

```
//회원가입폼
@RequestMapping(value="/user/regForm", method=RequestMethod.GET)
public String regForm(HttpServletRequest request, HttpServletResponse response)
{
   String cookieUserId = CookieUtil.getHexValue(request, AUTH_COOKIE_NAME);

   if(!StringUtil.isEmpty(cookieUserId))
   {
     CookieUtil.deleteCookie(request, response, AUTH_COOKIE_NAME);

     return "redirect:/";
   }
   else
   {
     return "/user/regForm"; 
   }
}
```
















