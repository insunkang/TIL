# Spring

## 스프링의 개요

### 1. 프레임 워크

​	완성된 소프트웨어가 아니라 어떤 문제를 해결하기 위해서 잘 설계된 미완의 모듈로 Spring 같은 경우 자바 개발자들이 공통으로 사용할만한 기능을 미리 정의해 놓은 모듈이다.
​																			  \------- 
​																			    |
​															코드를 모아놓은 라이브러리
(해결해야 하는 문제 : 내가 개발하고 싶은 시스템 - 쇼핑몰, 예약관리시스템, 인터넷뱅킹...)
재사용이 가능한 모듈이며 일반적으로 프레임워크를 통해서 개발하는 시스템의 공통모듈은 프레임워크에서 제공

- 개발자가 처리해야하는 대부분의 작업을 프레임워크 내부에서 처리해 주므로 개발을 위한 시간과 노력을 절약할 수 있다.
- 신뢰있는 프로그램을 개발할 수 있다.
- 개발자간의 의사소통이 활발
-  주어진 메뉴얼대로 개발하면 된다. 즉, 프레임워크 내부에서 제공하는 정해진 모듈을 사용해서 개발하면 된다.

### 2. Spring의 특징

 - 경량시스템(포함된 라이브러리가 거의 1MB가 넘지 않기 때문에 가볍다)

 - POJO(Plain Old Java Object)로 개발하기 때문에 작성하는 OOP의 특징을 적용하여 개발하면 된다.

 - spring프레임워크 내부에 Ioc컨테이너를 포함하고 있다.

   1. 의존성을 주입
      시스템 내부(내가 만든 프로그램)에서  사용하는 객체를 직접 생성해서 사용하지 않고 스프링 내부에 존재하는 컨테이너를 통해 필요한 곳에서 사용할 수 있도록
      \-----------

      스프링 내부에서 라이브러리로 존재

      spring-beans-4.2.4.RELEAS.jar

      spring-context-4.2.4.RELEAS.jar

   2. 스프링 내부의 IoC컨테이너를 통해 객체를 관리하면서 커플링을 낮출 수 있다.

   3. 스프링 내부에는 발생할 수 있는 다양한 모든 경우에 반응할 수 있도록 많은 컨테이너 클래스를 제공한다.

   4. 의존성 주입

      1. DL(Dependency Lookup)

         => 컨테이너가 만든 객체를 getBean메소드를 통해 가져와서 사용하는 것

      2. DI (Dependency Injection)

### 3. Spring 컨테이너의 종류

​	BeanFactory : 개발자가 객체를 요청하는 시점에 객체를 생성한다.

​			^

​			|

ApplicationContext : 컨테이너 객체가 생성될때 전달된 xml안에 정의된 모든 빈을 생성하고 의존성 주입을 처리한다.

​			^

​			|

WebApplicationContext

<어노테이션을 활용하기>

- 설정파일에 빈을 등록하지 않고 사용한다.
- 간단하게 기호를 이용하여 빈을 사용할 수 있도록 설정

[규칙]

- 설정파일에 <context:component-scan>엘리먼트를 이용해서 컨테이너가 빈을 찾을 수 있도록 패키지를 등록

- 기본 생성자를 반드시 추가해야 한다.

- 빈 생성을 위해 사용할 수 있는 어노테이션 기호

  - Component : 일반적인 빈

  - Service : 비즈니스로직(DAO제외)이 정의되어 있는 빈을 등록하는 경우 사용

    ​				클래스의 첫 글자를 소문자로 변경한 이름을  빈의 name에 등록

    ​				Dice => dice

    ​				Player => player

  - Repository : DAO를 등록하는 경우 사용

- 빈의 이름을 명시하고 싶으면 ()안에 ""로 정의

  => ex) 빈의 이름을 myplayer

  ​	@Service("빈이름")

  ​	@Service("myplayer")

  ​					\---------------

  ​							|_______________________________________________________ 등록한 빈의 이름은 lookup하거나 의존성 주입할때 사용

DB연동

### <Spring MVC프로젝트 구성 -Maven을 이용하지 않는 경우>

1. Dynamic Web Project 생성

2. 라이브러리를 lib폴더에 복사하기

3. DispatcherServlet을 web.xml에 등록

   => 모든 요청을 DispatcherServlet을 통해 진입하도록 설정해야 스프링이 제공하는 여러가지 기능을
   적용할 수 있다.(frontController 패턴이 적용되어 있다.)

4. spring에서 사용할 설정파일을 작성한다.

   => 따로 등록하지 않으면 web프로젝트에서 사용할 스프링설정 파일은 파일명을 작성할때 규칙이 있다.

   [DispatcherServlet을 등록한 서블릿명]-servlet.xml

   ex) 서블릿명 : springapp

   ​	/WEB-INF/

   ​		+

   ​		|_ springapp-servlet.xml

5.  Controller작성하기

   - 기본 web에서 서블릿과 같은 역할을 하는 클래스
   - 실제 처리를 담당하는 클래스

6. 스프링설정파일에 컨트롤러 등록하기

   <bean>태그를 이용해서 5번에서 생성한 컨트롤러 등록하기

   요청 path를 기준으로 컨트롤러를 등록할 것이므로 id속성을 쓰지 않고 name속성을 사용한다.

   DispatcherServlet내부에서 요청path에 맞는 컨트롤러를 getBean할 수 있도록 등록

   [형식]

   \<bean name="요청path" class="컨트롤러 클래스"/>

   .

   [예제]

   /test.do로 TestController를 요청

   \<bean name="/test.do" class="test.TestController"/>

   ->한글 인코딩(web.xml)

   ```html
     <filter>
   		<filter-name>encodingFilter</filter-name>
   		<filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
   		<init-param>
   			<param-name>encoding</param-name>
   			<param-value>EUC-KR</param-value>
   		</init-param>
   	</filter>
   	<filter-mapping>
   		<filter-name>encodingFilter</filter-name>
   		<url-pattern>/*</url-pattern>
   	</filter-mapping>
   ```

### <Spring MVC 구성요소>

스프링 MVC를 구축하고 웹을 실행

스프링이 제공하는 모든 편리한 기능을 잘 활용하기 위해서 스프링이 내가 작성한 자바빈을 관리할 수 있도록 작업해야 한다.(스프링 내부의 컨테이너가 내가 작성한 빈을 생성하고 관리할 수 있도록 작업)

이를 위해 모든 요청을 DispatcherServlet이라는 서블릿을 통해 들어올 수 있도록 처리

1. DispatcherServlet : 클라이언트의 모든 요청을 처리하기 위해 첫 번째로 실행되는 서블릿
2. HandlerMapping : 클라이언트가 요청한 path를 분석해서 어떤 컨트롤러를 실행해야 하는지 찾아서 DispatcherServlet으로 넘겨주는 기능을 실행하는 클래스
3. Controller : 클라이언트의 요청을 처리하는 클래스, DAO의 메소드를 호출하는 기능을 정의
4. ModelAndView : Controller에서 DAO의 메소드 실행결과로 만들어진 데이터에 대한 정보나 응답할 view에 대한 정보를 갖고 있는 객체
5. ViewResolver : ModelAndView에 저장된 view의 정보를 이용해서 실제 어떤 view를 실행해야 하는지 정보를 넘겨주는 객체

===> 스프링MVC를 구축하면 위의 클래스들이 자동으로 실행되묘 일처리를 한다. 
         따라서 필요에 따라 스프링에서 지원하는 ViewResolver나 HandlerMapping객체를 다양하게 등록하고 사용할 수 있다.

===> 기본 설정을 이용하는 경우 개발자는 Controller만 작성하고 설정파일이나 어노테이션으로 등록하면 된다.

### STS

#### Tiles프레임워크를 이용해서 화면 구성하기

1. 라이브러리를 pom.xml에 등록

2. 레이아웃이 적용되어 있는 템플릿파일과 연결할 jsp파일들이 미리 준비되어 있어야 한다.

3. tiles설정파일을 작성(main-tiles.xml)

   - 템플릿을 등록

     : 템플릿의 각 영역을 나누고 각 영역에 기본으로 연결할 jsp파일을 설정한다.

4. 템플릿(레이아웃을 미리 설정해 놓은 파일 - mainLayout.jsp)으로 만들어 놓은 jsp파일의 각각 영역이 템플릿에 등록한 영역과 일치하도록 설정

   => tiles에서 제공하는 태그를 사용한다.

   ​	 내부에서 tiles설정 파일에 등록한 내용과 연결하여 실행하는 작업을 처리하기 위해 tiles에서 제공하는 태그를 써서 작업해야 한다.

5. 스프링 내부에서 실행될때 DispatcherServlet이 뷰 정보를 ViewResolver에게 전달하면 ViewResolver가 tiles프레임워크를 활용해서 뷰를 만들수 있도록 spring설정파일에 등록

   - tiles설정파일이 어떤 파일인지 등록
   - 만들어야 하는 view가 tiles뷰임을 등록

6. 템플릿을 활용해서 만들어질 뷰의 정보를 tiles설정 파일에 등록

   1. 