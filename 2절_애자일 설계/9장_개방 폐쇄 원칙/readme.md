### 소프트웨어 객체는 확장에 대해 열려 있어야 하고, 수정에 대해서는 닫혀 있어야 한다.

#### 1. 확장에 대해 열려 있다.

모듈의 동작을 쉽게 확장할 수 있다는 것을 의미한다. 애플리케이션의 요구 사항이 변경될 때, 이 변경에 맞게 새로운 동작을 추가해 모듈을 확장할 수 있다.

#### 2. 수정에 대해 닫혀 있다.

어떤 모듈의 동작을 확장하는 것이 그 모듈의 소스 코드의 변경으로 이어지는 것은 아니다. 한 객체의 변경이 의존관계를 가지는 다른 객체의 변경으로 이어지지 말아야 한다.

우리는 이 말의 의미를 곰곰이 생각해보아야 한다. 얼핏 보기엔 이 두 원칙은 서로 대립되는 것 처럼 보인다. 모듈을 수정하지 않고 동작을 확장하는 것이 어떻게 가능할까?

## 해결책은 추상화이다

예를 들어 Server라는 클래스에 의존하는 Client 클래스가 있다고 생각해보자. Server의 동작은 변경 및 확장될 가능성이 있다. 이러한 상황에서 Client가 Server라는 구체적(concrete)인 클래스에 의존성을 가진다면, 이는 OCP를 위반하는 것이다. OCP를 지키려면 Client가 Server를 직접 사용하는 것이 아닌, 추상 인터페이스를 하나 두어 이를 사용하도록 하고, Server는 이 인터페이스의 구현체가 되도록 한다. 이렇게 하면 Server의 세부 구현 사항이 수정되어도 Client의 코드는 변경할 필요가 없으며(변경에 대해 닫혀 있다), 추상 인터페이스를 구현하는 또 다른 Server 객체가 추가되어도 기존 코드의 변경 없이 동작을 확장할 수 있다.(확장에 대해 열려 있다)

## 경직성의 악취 vs 불필요한 복잡성의 악취

OCP의 개념은 명확하지만, 실무에 이를 적용하기란 생각보다 쉽지 않다. 앞선 장에서 설명했듯이 원칙은 언제나 사용할 수 있는 향수가 아니며, 존재하는 문제를 해결하기 위한 수단으로 사용해야 한다. OCP 또한 수정되고 확장될 가능성이 높은 객체를 추상화해야 그 원칙이 가치를 발한다고 할 수 있다. 무턱대고 모든 의존관계를 가지는 객체에 인터페이스를 두는 것은 불필요한 복잡성의 악취를 풍기게 한다.

> 따라서 우리는 추후에 어떤 종류의 변경이 발생할 지 적절하게 예측할 수 있는 능력을 갖추는 것이 매우 중요하다고 생각한다. 이는 이론적으로 배울 수 있는 것이 아니라 경험으로 부딪혀야 하는 문제인데, 빠른 반복 주기를 가진 애자일 프랙티스는 변경에 민감하게 반응할 수 있는 적절한 환경이라고 생각한다.

> OCP는 SOLID 원칙 중에서도 객체 지향 설계의 핵심을 담은 가장 중요한 원칙이라고 생각한다. 소프트웨어 설계에 많은 노력을 들이는 이유는 결국 유지보수성과 재사용성이라고 생각하는데, OCP는 이러한 소프트웨어 설계의 궁극적인 목표와 직접적으로 맞닿아 있는 것 같다.
