1. POST 방식으로 요청하는 것은 URL의 Body영역에 데이터를 포함시켜 요청한다.
   - 사용자가 입력한 값(데이터) 들이 URL에 노출되지 않는다.
   - get방식에 비해 보안성이 높다
   - 로그인이나 회원가입 같은 경우 POST방식이 적합하다
2. Body영역은 전송하는 길이에 제한이 없다
   - 게시판 작성같은 경우 POST방식이 적합하다.
3. 즐겨찾기는 가능하나 전달되는 데이터가 URL에 노출되지 않기 때문에 같은 화면을 볼 수 없음(실질적으로 불가능 ) 
4.  최대 요청받는 시간이 존재하여 페이지 요청 대기시간이 있다

### 3줄 요약
1. Post 방식은 URL에 값들이 노출되지않는다.
2. 데이터 길이 제한이 없어서 게시판처럼 뭐가 많으면 용이하다.
3. 요청받는 요청대기시간이 있음

![[POST 방식에서의 인코딩.png]]
### POST방식의 경우 깨지는 이유
Post 요청방식은 HTTP body에 전달되어 인ㄱ코딩 설정이 ISO-8859-1로 되어있기때문에
UTF-8인 형태가 깨지는 것이다. 
때문에 POST 요청은 요청 데이터를 추출하기 전 인코딩 설정부터 해야한다.
요청 객체인 request에 인코딩 설정 코드를  넣자. 
`request.setCharacterEncoding("UTF-8");`

![[POST 방식 데이터 안깨지는 것 확인.png]]