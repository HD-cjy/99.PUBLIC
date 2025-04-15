# HashSet
- HashSet 값만 저장, Index개념이 없음(순서 유효X)
`HashSet 참조변수명 = new HashSet();`

-list와의 차이점 
-리스트는 중복을 허용하고 순서를 유지한다.
- 리스트는 index 개념이 존재한다. 

# Set 저장ㅅ
Set 저장소는 주소값을 기반으로 중복 체크를 하기 떄문에
만약 주소값이 같다면 중복 같지 중복이 아니다 라고 판단한다 .
주소값이 다르면 값이 중복이어도 중복이라고 인식하지 않음
==> 때문에 객체 내부의 데이터가 같다고 해도 주소값이 다르다면 중복으로 판단하지 않는ㄷ것
내부적으로 hashcode메소드와 equals 메소드가 호출되기 때문에 해당 메소드들을 클래스 내부에 재정의하여 필드값을 기준으로 비교 할 수 있도록 한다.

객체 내부에 있는 값들을 기반으로 같은 객체인지 다른 객체인지 판별하기 위한 작업
eqauls 메소드와 hashCode  매소드를 재정의해서 사용 
기본적으로 equals메소드와 hashCode메소드는 최상위 클래스의 메소드를 상속받아 사용하게 되고 이때 해당 메소스들은 주소값을 기반으로 비교하는 구문으로 작성되어있다. 

## HashMap
`HashMap<Key,Value> map = new HashMap<>();`
- 키랑 벨류 두개 들어가니까 제네릭타입도 2개! 

map.get("키값") 을 하면 벨류값 가져다 찍어줌 ㅇㅇ
없는 키값 넣으면 null 반환.
크기는 사이즈로. 
map. replace키로 가져와서 벨류값 새로 지정해주기. // 리플레이스는 없는거 안만들어짐 . 그니까 휴먼에러 줄이기. 
map. remove(키 값)


## Map 에 담긴 데이터 순차적으로 접근하기.
for문 ,향상된 for문 ,list에 넣기도 불가능. 
Iterator로 반복 돌리기. <= 가능성은 있음 but 절차가 있음. 바로는 불가능
Map 을 set으로 변경해서 Iterator 를 사용해서 뽑자.
1. 필요 메소드 map.keySet
   HashMap에서 제공하는 메소드 : Map에 담겨있는 key들을 set에 담아 반환 
2. EntrySet 이용하기.
   Map에 있는 key+value 세트를 Entry라는 형식으로 set에 담아주기 
![[Pasted image 20250321170054.png]]

Map 계열 특성상 순차적으로 접근할 방법으로 Set계열로 변환을 거친다
Map을 Set계열로 변경하여 반복문 ,list 이용 ,irerataor 이용방법
Map을 Set 계열로 바꾸는 두가지 방법
1. keyset();
2. entrySet();

## Properties 
properties: Map계열로 key + value의 형태로 값 저장
Map과 다른점: key,Value 모두 String 자료형으로 다루게 되고 파일입출력을 위한 형태

#### 메소드
- store 메소드 : 파일을 출력하는 메소드 
  properties 객체에 담긴 데이터가 key+value형태로 파일에 담겨서 출력됨
- Properties inputProp = new Properties ();


XML또한 처리 가능. 


