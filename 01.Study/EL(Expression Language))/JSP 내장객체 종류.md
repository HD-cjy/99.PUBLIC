데이터를 담을 수 있는  jsp 내장 객체 종류 (scope==영역)
1. SevletContext(Applicaiton Scope)
	- 한 어플리케이션 당 1개만 존재하는 객체
		해당 영역에 데이터를 담으면 애플리케이션 전역에서 사용 가능
2. HttpSession (Session Scope)
	- 한 브라우저당 1개 존재하는 객체 
	  해당 영역에 데이터를 담으면 모든 jsp/ 모든 servlet에서 사용가능.
	  - 값이 한번 담기면 서버가 멈추거나 브라우저가 닫히기 전까지 사용 가능
3. HttpServlet Request(Request Scope)
	- 요청 및 응답시 매번 생성되는 객체 
		  해당 영역에 데이터를 담으면 request 객체를 포워딩 받는 응답 jsp 에서만 사용 가능하다(1회성)
- 공유 범위가 해당 요청에 대한 응답 JSP 뿐이다.
4. PageContext(PageScope)
	- 현재 jps 페이지에서만 사용가능
	- 공유 범위가 가장 작다

위 객체들에 공통메소드 
데이터를 담을 때:    객체.setAttribute(키, 값);
데이터를 꺼낼 때:    객체.getAttribute(키);
데이터를 지울 때:    객체.getAttribute(키);


EL은 getXXX를 통해 값을 추출할 필요 없이 해당 키값만 제시하면 접근이 가능하다. 
내부적으로 해당 Scope 영역에 해당 키값에 담긴 객체를 반환받을 수 있다. 
기본적으로 EL은 JSP 내장 객체를 구분하지 않고 자동적으로 모든 내장 객체에  키값을 검색하여 존재하는 경우 값을 가져온다. 
표기법 : \${ 키값 }

EL표기법으로 키값을 찾을 땐 작은 범위의 Scope 부터 찾아서 
먼저 찾게된 값을 반환한다
page->request->session->application 순으로 찾는다.
만약 모든 영역에서 찾지 못했다면 아무것도 출력하지 않는다. 
(오류 발생하지 않음.)



<%-- 표현법 : \[영역Scope.키\] --%>
	pageScoper에 담긴 값: ${scope} 또는 ${pageScope.scope } 
	pageScope에 담긴 값 : ${scope} 또는 ${pageScope.scope} 
	requestScope에 담긴 값 : ${requestScope.scope}
	sessionScope에 담긴 값 : ${sessionScope.scope} 
	applicationScope에 담긴 값 : ${applicationScope.scope} 
	`존재하지 않는 키값에 접근해보기 ${test} ` ==> 값이 안나옴
	`존재하지 않는 키값에 접근해보기 표현식:<%=request.getAttribute("test")` ==> 값이 null로 나옴



`이름 : ${student.name}` <<< 이 구문은 내부적으로 getter메소드가 있어서 호출해주는 것일 뿐 없으면 작동안한다! 


## EL 연산자 (Operator)



## JSP를 이루는 구성인자
1. Jsp 스크립팅 원소: JSP페이지에서 자바코드를 직접 기술 할 수 있게 하는 기술 
	   Ex)선언문, 스크립틀릿, 표현식
2. 지시어: JSP 페이지 정보에 대한 내용을 표현하거나 다른 페이지를 포함할때 사용
	   ex) Page지시어, include 지시어, taglib지시어(라이브러리 추가시)
3. JSP 액션 태그: XML 기술을 이용하여 기존의 jsp 문법을 확장하는 기술을 제공하는 태그 
   - 표준 액션 태그: (Standard Action Tag): JSP 페이지에서 바로 사용가능
	- 표준 액션 태그는 모든 태그명앞에 jsp: 라는 접두어가 붙는다.
- 커스텀 액션 태크(Custom action Tag) :Jsp 페이지에서 바로 사용이 불가능하고 별도의 라이브러리를 연동해야한다. 
	- 커스텀 액션 태그는 모든 태그명 앞에 jsp: 대신 각각 제공하고 있는 태그 접두어가 붙는다 (JSTL)

