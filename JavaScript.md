# JavaScript

## <초급>

    1. 문법
       - 사용방법
       - 변수
       - 제어구문
    2. 함수
    3. 객체
       - 내장객체: String, Array, Date, Math
    4. 이벤트 핸들러
    5. 브라우저객체모델(BOM)

## <중급>

1. DOM
2. JSON
3. Ajax
4. 자바스크립트 프로토타입
   - 사용자 정의 객체 정의
   - 클로저

## <고급>

​	자바스크립트의 프레임 워크 사용

 1. bootstrap - css와 javascript의 프레임워크

 2. MEAN stack (full stack 서버단 부터 다 개발 할수 있는)

     io가 빈번하게 발생하는 곳에서 개발 할 수 있다

    - MongoDB
    - ExpressJs(express.js)
    - AngularJs
    - NodeJs

	3.  ReactJs - 웹 UI개발에 사용(facebook이 공개한 오픈소스)

	4.  Vue.js

	5.  D3



# BOM

- 브라우저에 출력되는 모든 구성 요소를 객체로 정의하고 접근
- window
- location
- document
- form(양식태그)
- image

## 1.접근방법

- 모든 객체는 계층 구조를 갖고 있다.
	
- form태그와 form태그 하위 태그를 객체로 접근하기 위해서 name속성을 정의하고 접근
	
	```html
	<form name="myform">
	    아이디:<input type = "text" name = "id">
	    패스워드:<input type = "password" name ="pass">
	</form>
	window.document.폼객체.텍스트객체
	window.document.myfrom.id.속성(메소드)
	
	주로 window.document는 생략
	```

- id를 정의하는 경우

  ```html
  <div id= "mydiv">
  </div>	
  객체 = document.getElementById("mydiv")
  ```

  