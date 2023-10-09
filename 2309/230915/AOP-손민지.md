# AOP
AOP(관점지향 프로그래밍, Aspect Oriented Programming)는 **핵심 비즈니스 로직에 있는 공통 관심사항을 분리하여 각각을 모듈화** 하는 것을 의미하며 **공통 모듈인 인증, 로깅, 트랜잭션 처리에 용이**합니다.  

**핵심 비즈니스 로직에 부가기능을 하는 모듈이 중복되어 분포되어 있을 경우 사용**할 수 있습니다.  

AOP의 가장 큰 특징이자 장점은 **중복 코드 제거, 재활용성의 극대화, 변화수용의 용이성**입니다.  

<br>
<br>

## 추가 지식

### 관점지향 프로그래밍(AOP, Aspect Oriented Programming)
AOP는 OOP(Object Oriented Programming, 객체지향 프로그래밍)를 돕는 보조적인 기술로,  
관심사의 분리(기능의 분리)의 문제를 해결하기 위해 만들어진 프로그래밍 패러다임이다.  
기능을 핵심 관심 사항(Core Concern)과 공통 관심 사항(Cross-Cutting Concern)으로 분리시키고  
각각을 모듈화 하는 것을 의미한다.

업무 로직을 포함하는 기능을 핵심 기능(Core Concern),  
핵심 기능을 도와주는 부가적인 기능을 부가 기능(Cross-Cutting Concern)이라고 부른다.  
OOP를 적용하여도 핵심 기능에서 부가 기능을 쉽게 분리된 모듈로 작성하기 어려운 문제점을 AOP가 해결해준다.  
AOP는 부가 기능을 애스펙트(Aspect)로 정의하여, 핵심 기능에서 부가 기능을 분리함으로써 핵심 기능을 설계하고 구현할 때 객체지향적인 가치를 지킬 수 있게 도와주는 개념이다.  
필수적이지만 어쩔 수 없이 반복적으로 사용되는 코드들을 리팩토링할 수 있도록 해준다.  
이로인해 여러 곳에서 사용될 만한 코드들이 한 곳에서 유지하고 관리할 수 있는 이점을 갖게 된다.  

---

### AOP 특징
- 접근 제어 및 부가기능을 추가하기 위해 프록시 패턴 기반
- 프록시가 호출을 가로챔(Intercept)
- Spring은 동적 프록시를 기반으로 AOP를 구현하므로 메소드 조인 포인트(JoinPoint)만 지원
  
---

### AOP 사용법
**스프링부트에서 간단하게 AOP를 적용하는 법 - 3단계**  
1. spring-boot-starter-aop dependency 적용하기  

maven의 fom.xml  
```Java
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-aop</artifactId>
</dependency>
```

gradle의 build.gradle  
```Java
implementation 'org.springframework.boot:spring-boot-starter-aop'
```

AOP 의존성을 추가하고 빌드를 하였으면 AOP를 활성화하겠다는 어노테이션을 추가해주어야 한다.  

<br>

2. @EnableAspectJAutoProxy 어노테이션 추가하기  
```Java
@EnableAspectJAutoProxy
@SpringBootApplication
public class AopApplication {
    public static void main(String[] args) {
        SpringApplication.run(AopApplication.class, args);
    }
}
```

<br>

3. 실제 AOP의 로직을 작성한다. (부가기능을 정의하고 부가기능이 사용될 시점을 정의한다.)  
모든 API에 비즈니스 로직의 실행시간을 측정해야 한다고 가정해보자.
```Java
@Aspect
@Component
public class LogAspect {
    Logger logger =  LoggerFactory.getLogger(LogAspect.class);
    
    //모든 패키지 내의 aop package에 존재하는 클래스
    @Around("execution(**..aop.*.*(..))")
    public Object logging(ProceedingJoinPoint pjp) throws Throwable {
    //해당 클래스 처리 전의 시간
    StopWatch sw = new StopWatch();
    sw.start();
    
    //해당하는 클래스의 메소드 핵심기능을 실행
    Object result = pjp.proceed();
    
    //해당 클래스 처리 후의 시간
    sw.stop();
    long executionTime = sw.getTotalTimeMillis();
    
    String className = pjp.getTarget().getClass().getName();
    String methodName = pjp.getSignature().getName();
    String task = className + ". " + methodName;
    
    log debug("[ExecutionTime] " + task + "-->" + executionTime + "(ms)");
    
    return result;
    }
}
```

AOP 클래스로 설정하기 위해 @Aspect 어노테이션을 추가하고,  
Spring의 빈으로 등록하기 위해 @Component 어노테이션을 추가해주었다. (AOP 사용시 빈 등록은 꼭 해주어야 한다.)  
그리고 우리가 하고자하는 건 모든 API의 실행 시간을 측정하는 것이므로,  
@Around 어노테이션을 통해 aop 패키지에 존재하는 모든 클래스에 해당 AOP를 적용하겠다고 설정해주다.  

그리고 실행 시간 측정을 위해 StopWatch를 생성하여 측정을 시작했고,  
pjp의 proceed를 통해 실제 핵심 로직을 실행하여 Object 클래스로 결과를 받았다.  
(Object 로 결과를 받아야 함!) 이후에 StopWatch를 중단하여 실행 시간을 밀리세컨드로 계산해 로그를 출력하고 함수를 종료시킨다.  
만약 실행 시간 측정을 밀리세컨드가 아닌 세컨드로 변경한다고 했을 때 AOP를 적용하지 않았다면 관련 로직의 모든 코드를 수정해주어야겠지만,  
AOP를 적용함으로써 핵심 로직에 대한 수정 없이 쉽게 이를 처리할 수 있게 되었다.  

<br>

**사용자가 직접 Annotation을 만들어 Aspect를 적용**  
Around를 execution에서 @annotation으로 변경만 해줍니다.  
이렇게 하고 시간측정 AOP를 적용하고 싶은 클래스에 가서 @LogExecutionTime 어노테이션을 붙이면 끝입니다.  

```Java
// 이 어노테이션을 부여하면 해당 메소드의 성능을 로깅합니다.
@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
public @interface LogExecutionTime {
}
```

```Java
@Aspect
@Component
public class LogAspect {
    Logger logger =  LoggerFactory.getLogger(LogAspect.class);
    
    @Around("@annotation(LogExecutionTime)")
    public Object logging(ProceedingJoinPoint pjp) throws Throwable {
    //해당 클래스 처리 전의 시간
    StopWatch sw = new StopWatch();
    sw.start();
    
    //해당하는 클래스의 메소드 핵심기능을 실행
    Object result = pjp.proceed();
    
    //해당 클래스 처리 후의 시간
    sw.stop();
    long executionTime = sw.getTotalTimeMillis();
    
    String className = pjp.getTarget().getClass().getName();
    String methodName = pjp.getSignature().getName();
    String task = className + ". " + methodName;
    
    log debug("[ExecutionTime] " + task + "-->" + executionTime + "(ms)");
    
    return result;
    }
}
```

---

더 많은 내용은 해당 링크 참고  https://dev-coco.tistory.com/81
