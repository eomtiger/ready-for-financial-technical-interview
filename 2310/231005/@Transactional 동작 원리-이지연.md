# @Transactional의 동작 원리
@Transactional을 메소드 또는 클래스에 명시하면, AOP를 통해 Target이 상속하고 있는 인터페이스 또는 Target 객체를 상속한 Proxy 객체가 생성되며, Proxy 객체의 메소드를 호출하면 Target 메소드 전 후로 트랜잭션 처리를 수행합니다.


***


- Caller에서 AOP 프록시를 탄다. 이때 타겟을 호출하지는 않고, 프록시를 호출한다.
- AOP 프록시는 트랜잭션 Advisor를 호출한다. 이 과정에서 커밋이 되거나 롤백이 된다.
- Custom Advisor가 있다면, 트랜잭션 Advisor 실행 전후로 동작한다.
- Custom Advisor는 타겟 메소드를 호출하여, 비즈니스 로직을 호출한다.
- 후에 순서대로 리턴된다.

### Spring AOP
Spring AOP는 일반적으로 두 가지 방식이 있다. (JDK Dynamic Proxy와 CGLIB)   
AOP 프록시 생성 과정에서 타겟 객체가 하나 이상의 인터페이스를 구현하고 있는 클래스라면 JDK Dynamic Proxy를 사용하고, 그렇지 않다면 CGLIB를 사용한다.

- **JDK Dynamic Proxy**
  java.lang에 포함되어 있는 Reflection의 Proxy 클래스가 말 그대로 동적으로 생성한다고 하여 Dynamic Proxy라고 부른다. 타겟의 Interface를 기준으로 Proxy를 생성한다는 것이 Dynamic Proxy의 핵심이라고 할 수 있다.
- **CGLIB (Code Generator Library)**
  스프링 부트는 CGLIB가 default다. CGLIB는 클래스의 바이트 코드를 조작하여 프록시 객체를 생성하는 라이브러리이다. CGLIB를 사용하여 인터페이스가 아닌 타겟에 대해서 프록시를 생성할 수 있다.

  
