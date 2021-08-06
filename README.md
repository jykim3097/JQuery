# JQuery

21.06.24.   

* 자바스크립트를 **더 간편**하게 사용하게 하는 **자바스크립트의 라이브러리**
	* 자바스크립트 ? 웹 페이지를 동적으로 표현해주는 언어
* 순수 자바스크립트로 코딩하는 것보다 JQuery를 사용하면 더 높은 생산성을 기대할 수 있다
* 자바스크립트와 JQuery를 구분해서 잘 사용해야 한다!!
	* 혼용해서 사용하면 가독성이 떨어지고, 유지보수에 힘들다
	* 눈에 띄진 않지만 속도가 조금 느리다
* 개발 환경 : vscode

## 장점
* 태그를 선택자로 한 번에 선택하는 강력한 방법을 제공한다
* 선택자로 선택한 태그를 제어하는 강력한 기능을 제공한다

## 사용 방법
1. 직접 다운 받아서 사용
	* url 타고 들어가면 문서가 나오는데
	* 사용할 수 있는 기능들이 압축되어 있는 것이다
	* 네트워크 환경이 불안정하면 끊길 수 있기 때문에 직접 다운로드 받는다
	* 다운로드 방법
		1. google에 jquery 검색
		2. download 클릭
		3. uncompressed 3.6.0 버전을 클릭하면 문서 형태가 나온다
		4. 우클릭해 다른 이름으로 저장
		5. workspace에 js 폴더를 만들고 파일을 옮긴다
		6. head 안에 <script src="js/jquery.js"></script>를 넣어 참조한다
2. 아래 링크 사용
```
<script type="text/javascript" src="//code.jquery.com/jquery-3.4.0.min.js"></script>
// 또는
<script type="text/javascript"
src="https://ajax.googleapis.com/ajax/libs/jquery/1.6.2/jquery.min.js "></script>
```

## 함수
* 중요한 것만 외우고, 어떻게 사용하는 지만 알아두면 된다
* 주된 사용방법 **${"선택자"}.함수**

## 선택자
* 태그를 선택하면 같은 이름을 가진 태그를 모두 가져와 **객체(배열) 형태**로 저장한다
	* 값이 하나여도 배열로 반환된다
	* element에 접근하려면 index를 통해 접근한다
* 결론적으로 **$(선택자).제이쿼리함수**로 js 작업을 처리한다
* 출력된 값에 대해 javascript 문법을 사용할 수 있지만 그것은 ~~끔찍한 혼종~~이다
* $("#아이디 태그")
* $(".클래스 태그")
* $("요소[속성=값])
* $(this)

### 자주 사용하는 속성 제어 함수 (필 수 암 기)
#### val
* val() : 태그의 값을 확인
	* 인덱스로 접근하는 게 아니고 태그에 접근
* val(변경값) : 태그의 값을 변경

#### attr
* **매개변수가 한 개 이상**
* attr(속성) : 태그 속성 여부 확인
* attr(속성 변경 값) : 태그 내부 속성 변경
* attr({}) : 여러 값을 한 번에 변경 할 때는 중괄호에 키값 형태로 넣는다
```
$(".test3").attr({
	src : "img/profile.png",
	width : 50,
            height : 50,
            alt : "hell로월드"
})
```

#### css
* css() : css 속성 확인
* css(속성, 변경값) : css 속성 변경
	* 단일 선택자인지 다중 선택자인지 고려하지 않아도 된다.
* css 속성을 {} 형식으로 한 번에 변경할 수 있다.
```
$(".box").css({
            backgroundColor : "skyblue",
            display : "inline-block",
            width : "50px",
            height : "50px",
            border : "1px solid #777",
            margin : "5px"
})
```

#### 문자 조작 html과 text
* html() : html 형태로 값을 얻는다
* html(값) : html 형태로 문자를 변경한다
	* 값을 없애고 싶을 땐 공백을 입력하면 된다
* test(값) : 순수 문자 형태로 입력된다

#### 클래스 조작 addClass, removeClass, toggleClass
* addClass(값) : 클래스 추가
* removeClass(값) : 클래스 삭제
* toggleClass(값) : 토글 클래스

#### 반드시 알아야 하는 제이쿼리 **이벤트 함수**
* $(document).ready
	* window.onload와 유사하다
	* 그런데 window.onload는 단 한 번만 사용할 수 있지만 **ready 함수는 여러 번 사용 할 수 있다.**

* $(document).click, ...
	* js의 on이 붙었던 걸 다 떼고 사용할 수 있다
* 이벤트 위임함수

21.06.25.   
## 비동기 통신 ajax
* 화면 이동 없이 데이터를 공유하는 것(통신)
* 양방향 통신이기 때문에 보내는 값과 받는 값, 어떻게 받을 것인지(rest api), 어떻게 보낼 것인지 등등을 다 생각해야한다
* 문법
	* 키:값을 갖는다
	* 지정된 key에 값을 넣는다
```
$.ajax({
	속성
})
```
* 주요속성
	* data : 보낼 데이터
	* dataType : 서버에서 받아올 데이터의 타입
	* type : 서버로 전송하는 데이터타입 - POST, GET
	* url : 전송할 url
	* contentType : 필수로 지정되어야하는 타입, 보내는 데이터가 '어떤 타입이다'라는 것을 알려준다
	* success : 통신에 성공했을 때 결과를 돌려받을 callback 함수를 적는다
	* error : 통신에 실패했을 때 실행시킬 callback 함수를 적는다

* 서버가 다르면 기본적으로 요청을 차단하게 되어있다 > CORS
* 비동기 서버를 열고 스스로 통신하는 것 ? open API를 사용할 수 있다는 것!

## 달력 datepicker