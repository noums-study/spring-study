# SOLID
* 객체 지향 프로그래밍 및 설계의 다섯 가지 기본 원칙
<br>

| 두문자| 약어| 개념 |
|:---:|:---:|:---|
|S|SRP|**단일 책임 원칙 (Single responsibility principle)**<br> 한 클래스는 하나의 책임만 가져야 한다.|
|O|OCP|**개방-폐쇄 원칙 (Open/closed principle)**<br> “소프트웨어 요소는 확장에는 열려 있으나 변경에는 닫혀 있어야 한다.”|
|L|LSP|**리스코프 치환 원칙 (Liskov substitution principle)**<br>“프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서<br> 하위 타입의 인스턴스로 바꿀 수 있어야 한다.” 계약에 의한 설계를 참고하라.|
|I|ISP|**인터페이스 분리 원칙 (Interface segregation principle)**<br>“특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 낫다.”|
|D|DIP|**의존관계 역전 원칙 (Dependency inversion principle)**<br>프로그래머는 “추상화에 의존해야지, 구체화에 의존하면 안된다.”<br>의존성 주입은 이 원칙을 따르는 방법 중 하나다.|
<br>

<br>
<br>

# IoC
* Inversion of Control (제어의 역전)
* 프로그램의 제어 흐름을 직접 제어하지 않고 외부에서 관리하는 것
* 기존에는 의존 관계의 제어를 구현 객체에서 직접 해주었다. 그러나 AppConfig가 등장한 이후에 프로그램의 제어권은 AppConfig가 가져간다. 구현 객체는 자신의 로직을 실행하는 역할만 담당한다. 즉, 객체에 대한 제어권인 바뀐 것이다.
<br>
<br>
<br>

# DI
* Dependency Injection (의존관계 주입)
* 컨테이너가 이미 생성된 빈 객체를 필요한 객체한테 주입한다.

<br>
<br>

## reference
* https://ko.wikipedia.org/wiki/SOLID_(%EA%B0%9D%EC%B2%B4_%EC%A7%80%ED%96%A5_%EC%84%A4%EA%B3%84)
* https://yhmane.tistory.com/127
