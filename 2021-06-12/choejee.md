# 빈 라이프사이클
 
스프링 컨테이너 생성 -> 스프링 빈 생성 -> 의존관계 주입 -> 초기화 콜백 -> 사용 -> 소멸전 콜백 -> 스프링 종료

* 초기화 콜백 : 빈이 생성되고, 빈의 의존관계 주입이 완료된 후 호출
* 소멸전 콜백 : 빈이 소멸되기 직전에 호출
 
<br>
 
💡 객체의 생성과 초기화를 분리하자. 
>생성자는 파라미터를 받고, 메모리를 할당해서 객체를 생성하는 책임을 가진다. <br>
반면에 초기화는 이렇게 생성된 값들을 활용해서 외부 커넥션을 연결하는등 무거운 동작을 수행한다. <br> 
따라서 객체를 생성하는 부분과 초기화 하는 부분을 명확하게 나누는 것이 유지보수 관점에서 좋다. 
 
 
<br>
<br>
 
 
# 빈 객체의 초기화와 소멸
## 1. 인터페이스를 통한 구현
 
* Bean 객체가 각 인터페이스를 구현하여 지정한 메서드를 호출 
* InitializingBean의 **afterPropertiesSet()** 메서드 오버라이드
* DisposableBean의 **destroy()** 메서드 오버라이드
* 스프링 전용 인터페이스
* 외부 라이브러리에 적용 불가
* 지금은 거의 사용하지 않는 방식

 
<br>
<br>
 
 
## 2. @Bean 어노테이션의 속성 (initMethod, destoryMethod)
* 설정 정보에 지정
* 스프링 빈이 스프링 코드에 의존하지 않는다.
* 설정 정보를 사용하므로 외부 라이브러리에 적용 가능
 
 
<br>
 
 
💡 @Bean의 destroyMethod의 기능
> 기본값이(inferred)(추론)으로 등록되어 있어서 close, shutdown 라는 이름의 메서드를 자동으로 호출한다.<br>
즉, 직접 스프링 빈으로 등록하면 종료 메서드는 따로 적어주지 않아도 잘 동작한다.<br>
추론 기능을 사용하고 싶지 않으면 destoryMethod=""처럼 빈 공백을 지정하면 된다.<br>
 
 
<br>
 
 
~~~java
@Configuration
public class AppConfig {
	
	// 이 경우 destroyMethod 속성을 입력하지 않아도 자동으로 close()메서드를 호출한다.
	@Bean(initMethod = "init", destroyMethod = "close")
	public NetworkClient networkClient() {
        NetworkClient networkClient = new NetworkClient();
        return new NetworkClient();
    }
}

public class NetworkClient {
	public init() {
		...
	}
	
	public close() {
		...
	}
}
~~~


<br><br>

## 3. @PostConstruct, @PreDestroy
* 최신 스프링에서 가장 **권장**하는 방법
* JSR-250라는 자바 표준으로 스프링이 아닌 다른 컨테이너에서도 동작
* 컴포넌트 스캔과 잘 어울린다.
* 외부 라이브러리에 적용 불가. 외부 라이브러리를 초기화, 종료해야 하면 @Bean의 기능을 사용하면 된다.


<br>

~~~java
public class NetworkClient {

    public NetworkClient() {}

    @PostConstruct
	public init() {
		...
	}
	
    @PreDestroy
	public close() {
		...
	}
}
~~~ 

