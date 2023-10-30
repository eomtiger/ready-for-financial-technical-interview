# 스프링 빈(Bean)
> 스프링 컨테이너에 의해 관리되는 재사용 가능한 소프트웨어 컴포넌트입니다.  
즉, 컨테이너가 관리하는 자바 객체이자 인스턴스화된 객체를 의미합니다.

<br>

### 스프링 빈을 스프링 컨테이너에 등록하는 방법
1. 자바 어노테이션 사용  
Spring에서 Bean을 등록하기 위한 Annotation은 `@Component`을 사용합니다. 하지만 실제로 사용 시 아래 예시처럼 `@Component`을 내포하고 있는 `@Controller` Annotation을 사용하는 경우도 있습니다.
``` java
@Controller
public class HelloController {
    @GetMapping("hello")
    public String hello(Model model){
        model.addAttribute("data", "This is data!!");
        return "hello";
    }
}
```

2. Bean Configuration File에 직접 등록  
아래의 예제와 같이 @Configuration을 이용하면 Spring Project 에서의 Configuration 역할을 하는 Class를 지정할 수 있습니다. 이후 해당 File 하위에 Bean 으로 등록하고자 하는 Class에 @Bean Annotation을 사용해주면 간단하게 Bean을 등록할 수 있습니다.
```java
@Configuration
public class HelloConfiguration {
    @Bean
    public HelloController sampleController() {
        return new SampleController;
    }
}
```

<br>

---

### 참조
- https://melonicedlatte.com/2021/07/11/232800.html