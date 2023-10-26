# 스프링에서 빈(Bean)을 등록하는 방법
빈을 등록하는 방법은 기본적으로 2 가지가 있습니다.  

1. 우선 가장 쉬운 방법으로 **@Component 어노테이션을 사용**하는 것입니다.  
@Controller, @Service, @Repository는 모두 @Component를 포함하고 있습니다.  

2. **설정 클래스를 따로 만들어 @Configuration 어노테이션을 붙이고,  
해당 클래스 안에서 빈으로 등록할 메소드를 만들어 @Bean 어노테이션을 붙여**주면 자동으로 해당 타입의 빈 객체가 생성됩니다.  

<br>
<br>

## 더 많은 내용
https://dev-coco.tistory.com/69
