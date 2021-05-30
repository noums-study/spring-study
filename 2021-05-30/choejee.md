## Bean 이란?
* IoC 컨테이너가 자바 객체를 만들면 이 객체를 스프링 빈(Bean)이라고 부른다.
스프링 빈과 자바 일반 객체와의 차이점은 없다.
단지 IoC 컨테이너에 의해 만들어진 객체를 스프링 빈이라고 부를 뿐이다.
<br>
<br>

## Bean 등록
1. XML
* xml파일에 직접 설정
* 일일히 모든 빈과 의존성을 설정해야하므로 굉장히 번거롭고 불편

2. Component Scanning
* 클래스에 특정 애노테이션을 부여하고, 이 애노테이션을 부여한 클래스를 찾아서 자동으로 빈을 등록해주는 방식 
* 이러한 방식을 '빈 스캐닝'이라 하고, 이런 작업을 담당하는 객체를 '빈 스캐너'라고 한다.
* 스프링의 빈 스캐너는 지정된 패키지 하위에 있는 모든 패키지를 대상으로 필터를 적용해서 빈 등록을 위한 클래스를 찾는다. 
* 이 필터에 적용되는 애노테이션을 stereotype 애노테이션이라고 한다. 

* @Component
    * @Repository
    * @Service
    * @Controller
    * @Configuration

3. Java Coding
* 자바 코드를 통해 인스턴스를 생성하면서 의존성을 주입하는 방식
* 클래스 레벨에서는 @Configuration을 붙이고, 메서드 레벨에서는 @Bean 애노테이션을 붙인다. 
<br>
<br>

## 의존 관계 자동 주입
* IoC 컨테이너에 빈으로 등록되어야 가져다 쓸 수 있다.(의존성 주입)

1. @Autowired
* 주입하려고 하는 객체의 타입이 일치하는 객체를 자동으로 주입한다.
* 필드, 생성자, Setter에 붙일 수 있다. 
* 단, @Autowired를 필드, Setter에 붙여서 사용할 경우 반드시 기본 생성자가 정의되어 있어야 한다. 

2. @Resource
* 주입하려고 하는 객체의 이름(id)이 일치하는 객체를 자동으로 주입한다.
* Java 제공 애노테이션이며 필드, Setter에 붙일 수 있다. 생성자에는 붙일 수 없다.
* @Autowired와 마찬가지로 반드시 기본 생성자가 정의되어 있어야 한다.
<br>
<br>

## ref
* https://nkcnow.tistory.com/
* https://atoz-develop.tistory.com/entry/Spring-DI-%EC%95%A0%EB%85%B8%ED%85%8C%EC%9D%B4%EC%85%98-%EC%A0%95%EB%A6%AC-Autowired-Resource-Inject
