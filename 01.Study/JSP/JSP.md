## 순수 Servlet: Java코드에 HTML을 작성하는 형태
## JSP (Java Server Page) : html에 Java코드를 작성하는 형태
Servlet으로 응답페이지를 출력하는 작업을 jsp에게 전달하여 대신 처리 할 수 있도록 한다.
jsp 페이지에서는 각 html 요소를 serrvlet 코드화 시켜서 컴파일 후 페이지를 띄워준다.

이때 jsp페이지에 전달할 값이 있다면 해당 데이터들을 내장 객체에 담아서 전달해야한다.
사용할 영역 - request의 attribute 영역
사용 방법 request.setAttribute("키","벨류값");
위와같이 키-벨류(값) 묶음으로 담아서 전달한다.
`setAttribute(String,Object);`
응답 페이지에 데이터 전달하기.

## jsp에게 위임하기 위한 용도의 객체 
`RequestDispatcher` - java로 가져온걸 jsp에게 html이랑 같이 처리해달라고 할때 사용하는 객체
```Java
package com.kh.controller;
import java.io.IOException;
import java.util.Arrays;
import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
@WebServlet("/test2")

						...
						...
						
		//전달값을 담아준reqquest객체와 응답을 위한 객체인 response를 함께 출력해줄 
		//jsp에게 윟임한다 
		//jsp에서 해당 데이터를 사용하고 응답 처리를 할 수 있도록. 
		//이때 jsp에게 위임하기 위한 용도의 객체:RequestDispatcher
		//1) 응답하고자 하는 뷰 JSP를 선택해서 위임하기 
		RequestDispatcher view = request.getRequestDispatcher("/view/responsePage.jsp");
															//여기가 뷰jsp를 잡아온 부분이다.
		
		//2) 응답페이지 경로 선택후 포워딩(위임해주기) 
		view.forward(request, response);  //request와 response 전달하며 요청 흐름 위임하기.
		
		
	}
```

JSP 상단 `<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%> `
각종 형식등을 명시해주는 코드가 상단에 들어가야 JSP이다.  
```java script page
<%@ 
	// 해당 영역은 스크립틀릿 이라고 해서  jsp 문서 내에 자바코드를 사용 할 수 있는 영역
	// 현재 jsp에서 필요한 데이터는 servlet에서 request 객체의 attribute 영역에 담고놨고
	//해당 데이터를 추출하여 원하는 html 요소 사이에 넣어서 출력 형식을 만들어주어야한다.
	//attribute 영역에 담긴 값을 추출하는 방법
	//request.getAttribute ("키"); 
	//이때 반환되는 value 값의 자료형은 Object이기 때문에 형 변환을 해서 사용한다. 
%>
```

담을때는 setAttribute  꺼낼때는 getAttribute 

![[JSP_경로설정부분.png]]
404 오류는 경로 오류다.
드래그 해둔 부분들 (경로 지정 및 받는 경로를 확인해야한다.)

```JSP
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>피자 주문 페이지</title>
</head>
<body>
<h1>피자 주문 페이지</h1>
<%@include file = "today.jsp" %>
<h2>오늘 날짜</h2>

</body>
</html>
```