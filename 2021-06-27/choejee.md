# 공통 처리의 구현

웹 개발 시, 공통적으로 처리해야할 업무들이 있다.
예를 들어 로그인 관련(세션 체크)처리, 권한 체크, XSS(Cross Site Script) 방어, PC와 모바일 웹의 분기 처리, 로깅, 인코딩 처리 등이 있다. 
공통 업무에 관련된 코드를 모든 페이지마다 작성해야 한다면
중복된 코드가 많아지고, 프로젝트 단위가 커질수록 서버에 부하를 줄 수 도 있으며, 유지보수에도 어렵다. 
__*즉, 공통 부분은 빼서 따로 관리하는게 좋다.*__

<br>

Spring은 공통 업무를 자동으로 처리할 수 있는 3가지 기능을 제공한다. 

1. Filter
2. Interceptor
3. AOP

세 가지 기능은 모두 어떤 처리를 하기 전에 먼저 실행되거나, 실행한 후에 추가적인 처리를 할 때 사용한다.
반면, 각각의 기능은 적용 시점이 다르다. 

<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcHRhZl%2FbtqBE12ZZ5V%2FXJBrJ8FHof2KXC3xaEYZsK%2Fimg.png">


* 실행 순서는 Filter -> Interceptor -> AOP -> Interceptor -> Filter 
* Filter, Interceptor는 Servlet 단위에서 실행된다.

<br>

##  Filter
정제하다.

* 요청과 응답을 거른 뒤 정제하는 역할이다.
* DispatcherServlet 이전에 **Web Application** 단에서 실행된다. 
* 보통 web.xml 에 설정한다. 
* Log, 인코딩, 보안과 같은 *web 전역적으로 처리해야 하는 로직*은 Filter에서 관리한다.


필터 실행 메서드
* init() - 필터 인스턴스 초기화
* doFilter() - 전/후 처리
* destroy() - 필터 인스턴스 종료

<br>

<img src="https://user-images.githubusercontent.com/8748075/86555900-d9095d00-bfa5-11ea-87f9-fac27fc6de3f.png">


<br><br>


## Interceptor
가로채다.

* DispatcherServlet이 Controller를 호출하기 전, 후로 끼어든다.
* Spring Application의 기능이며 일종의 bean
* 스프링 컨테이너이기에 다른 빈을 주입하여 활용하기 좋다.
* 특정 URI에서만 동작한다.
* 로그인, 사용자 권한 확인 등 *특정 URI에서만 필요한 로직*은 Interceptor에서 관리한다.

<br>

인터셉터 실행 메서드
* preHandler() - Controller 실행 전
* postHandler() - Controller 실행 후 view rendering 이전
* afterCompletion() - view rendering 이후

<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcnB6RX%2FbtqHZIxSOcm%2FEOh03mdZQgNhzKr5mrtFD1%2Fimg.png">
<img src="https://blog.kakaocdn.net/dn/cMejKo/btqH8cjAviy/hisVhNkQLh9Bv4XMjvknL1/img.png">

<br><br>

##  AOP
To be continued ... 

<br>

### References
https://bk-investing.tistory.com/61

https://ksshlee.github.io/spring/web/springboot/interceptor,filte/

https://sallykim5087.tistory.com/158

https://mossgreen.github.io/Servlet-Containers-and-Spring-Framework/
