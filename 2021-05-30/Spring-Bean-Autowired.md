# 2021-05-30

## 주제

- 빈 자동/수동 등록 
- 의존 관계 자동 주입
- lombok

### 관련 키워드
- @Component, @ComponentScan
- @Autowired
- @Getter, @Setter ...

### 요약
#### @Data, @Value
- 사용 자제할 것

<br>

#### @Setter
- DB 사용시 쓰지 않는 걸 권장

<br>

#### final 키워드
    불변, 필수

1. final 변수
    - 상수
    - 변수를 선언과 동시에 초기화
    - 오직 get만 가능
<br>

2. final 메서드
    - overriding 불가능
    - 상속 받은 그대로 

<br>

3. final 클래스
    - 상속 불가능
    - subclass 생성 불가능 


<br>

#### 순환 참조
    왜 생성자 주입을 권장하는가?

> 필드 주입과 수정자 주입은 모든 객체 생성이 끝난 후에 의존 관계를 주입한다.<br> 즉, 의존성이 있는 객체가 생성되지 않아도(의존 객체가 null이어도) 객체가 생성된다. (컴파일시 오류가 발생하지 않는다.)
<br>

반면에 **생성자 주입**은 **객체 생성과 동시에 의존 관계를 주입**한다.  객체를 생성할 때, 의존 객체의 null 여부를 검사한다. 
의존 객체가 null일 경우, 컴파일 오류를 발생시켜 런타임 시에 오류가 발생하는 참사를 방지해준다.

<br><br>

## 참여자
- [승연](https://github.com/ssyoni)
- [지현](https://github.com/choejee)
- [나래](https://github.com/mumblecoder)
  
<br/>

## 벌금 💸

