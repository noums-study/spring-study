# AOP

### AOP란?
* Aspect-Oriented Programming

* 부가 기능의 모듈화
	
	- 비즈니스 로직 외에 로그, 권한 체크, 트랜잭션 등과 같은 부가 기능을 인프라 로직이라고 한다.
	- 인프라 로직은 애플리케이션 전 영역에서 나타날 수 있으며 하나의 관심사를 가진다. 
	- 이러한 인프라 로직의 복이 횡단으로 나타나기 때문에 Cross-cutting Concern(횡단 관심사)라고 부른다.


- AOP는 횡단 관심에 따라 프로그래밍 하는 기법
- 자바에서 AOP를 구현한 구현체 : AspectJ
- OOP 보완

>Spring documentation<br>"AOP complements OOP by providing another way of thinking about program structure"


<br>

### AOP 용어


Target
- 어떤 대상에 부가 기능을 부여할 것인가

Aspect
- 부가 기능 모듈
- 부가 기능을 정의한 Advice와 어디에 적용할 지 결정하는 Point Cut을 함께 갖고 있다. 

Advice
- 실질적으로 부가 기능을 담은 구현체 
- 어떤 부가 기능? Before, AfterReturning, AfterThrowing, After, Around(메서드의 실행 전, 후) 

Join Point
- 어디에 적용할 것인가? 메서드, 필드, 객체 생성자 등

>AspectJ는 메서드가 호출될 때, 메서드가 실행될 때, 필드에 접근할 때, 객체가 생성될 때 등
다양하게 Join point를 구현했다.<br>그러나 Spring AOP에서는 메소드가 실행될 때만으로 한정


 Point Cut
 - 실제 Advice가 적용될 지점, Spring AOP에서는 Advice가 적용될 메서드를 선정하는 기능 

Weaving
- 지정된 객체에 Aspect를 적용해서 새로운 프록시 객체를 생성하는 과정을 얘기한다. 

스프링 AOP의 구현 방법
- 프록시 패턴

- proxy (대리)
    - 타겟을 감싸서 타겟의 요청을 대신 받아주는 Wrapping Object이다. 
    - 클라이언트에서 타겟을 호출하면 타겟이 아닌 타겟을 감싸고 있는 프록시가 호출되어, 
	타겟 메소드 실행 전에 선처리, 타겟 메소드 실행 후, 후처리를 실행한다. 
    - AOP에서 프록시는 호출을 가로챈 후, Advice에 등록된 기능을 수행 후 타겟 메소드를 호출한다. 

<br>

### Reference
https://jojoldu.tistory.com/71

https://www.youtube.com/watch?v=Hm0w_9ngDpM&t=668s
