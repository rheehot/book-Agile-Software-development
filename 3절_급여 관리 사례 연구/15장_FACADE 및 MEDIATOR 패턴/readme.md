## FACADE

FACADE 패턴은 복잡하고 일반적인 인터페이스를 가진 객체 그룹에 간단하고 구체적인 인터페이스를 제공하고자 할 때 사용한다.
 
예를 들어, 우리가 직접 작성한 어플리케이션에 DB와 연동되어야 하는 Product라는 객체가 있고, DB 연동 작업을 처리할 수 있도록 하는 java.sql 패키지가 있다고 해보자. 이 때 java.sql 패키지의 세부 사항을 모두 알고 있고, 결과로 Product 객체에게 DB 사용을 가능케 하는 아주 간단한 인터페이스를 제공하는 DB 클래스를 만든다. 이 DB 클래스의 존재는 Product 클래스로 하여금 java.sql 패키지에 대해 아무것도 알 필요가 없게 해주며, 이는 소프트웨어 설계의 복잡성을 낮추는 이득을 가져다 준다. 

> 맥락이 다른 객체 그룹의 복잡한 인터페이스를 사용하기 쉽게 간단한 인터페이스로 바꿔주는, proxy의 개념이라고 이해하면 될 것 같다.

> 여러 백엔드 프레임워크에서 제공하는 repository 객체들도 DB 사용에 대한 세부사항을 은닉화해주는 facade의 일종이라고 할 수 있을 것이다.

FACADE 패턴은 팀원들과의 합의가 있어야 한다. 프록시 역할을 해주는 독립된 클래스를 만드는 것이기 때문에, 특정 작업을 원하는 객체는 이 프록시 객체에 대해 **알고 있어야 한다.**

> FACADE 패턴을 비롯해 이 책에서 소개하는 디자인 패턴 중 일부는 DDD에서 접한 적이 있던 것들이다. 다만 이 책에서는 기술적인 관점에서의 근본적인 디자인 패턴을 소개하고 있고, DDD는 도메인 영역에 대해 개념적인 관점에서 적용할 만한 패턴을 알려준다. 예를 들어 이 책에서는 FACADE 패턴을 기술적으로 서로 다른 인터페이스를 가진 객체 그룹 사이의 소통을 원활히 하기 위한 수단으로 설명하는 반면, DDD에서는 서로 다른 BOUNDED CONTEXT를 가진 도메인 모델 사이에서 소통의 수단으로 이 패턴을 활용한다.

## MEDIATOR

FACADE가 자신의 정책을 가시적이고 강제적인 방식으로 적용하는 반면, MEDIATOR는 자신의 정책을 은밀하고 강제적이지 않은 방식으로 적용한다. 적용해야 할 정책의 크기가 그렇게 크지 않거나, 정책 적용을 명시적이지 않고 은밀하게 해야하는 상황이라면 FACADE보다 MEDIATOR 패턴을 사용하는게 나을 것이다.

> MEDIATOR 패턴은 FACADE보다 훨씬 은밀한 방식으로 정책을 적용하기 때문에 사용하는 사람도 스스로 MEDIATOR 패턴을 활용하고 있다는 것을 모를 수도 있다는 생각이 들었다. 따라서 MEDIATOR 패턴에서 중요하게 생각해야 할 점은 "언제 MEDIATOR 패턴을 써야하는가" 라기 보다는 "언제 FACADE 패턴으로 전환해야 하는가"라고 생각한다.