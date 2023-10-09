# **Spring과 Spring Boot의 차이**

1. 간편한 설정

   - Spring
     - 간단한 H2 데이터베이스 연동에도 xml이나 서블릿 3.0부터는 Java 코드로 별도의 설정이 필요

   - Spring Boot
     - yml에 간단히 설정
     - 프로젝트에 라이브러리만 추가해두면 부트가 Jar 파일을 인지해서 관련된 스프링 설정을 자동으로 처리
     - 메인 클래스의 @SpringBootApplication 어노테이션으로 동작
     - @SpringBootApplication 중 @EnableAutoConfiguration

2. 편리한 의존성 관리 & 자동 권장 버전 관리

   - Spring
     - 개발에 필요한 모듈의 의존성을 각각 다운받고 버전을 명시했어야 함

   - Spring Boot
     - spring-boot-starter로 자주 사용하게 되는 모듈 간의 의존성과 버전 조합을 제공
     - spring-boot-starter-parent는 각 모듈의 현재 Spring Boot 버전에 가장 적합한 버전 제공

3. 내장 서버로 인한 간단한 배포 서버 구축

   - Spring
     - 애플리케이션 WAR 패키징 → WAS 설치 (Tomcat, Undertow, Jetty) → WAS에 WAR 파일 올리기

   - Spring Boot
     - tomcat 내장 서버로 구동 시간 단축
     - 내장 서블릿 컨테이너 덕분에 jar 파일로 간단 배포

4. Spring Security, Spring Data JPA 등의 다른 스프링 프레임워크 요소를 쉽게 사용



[출처]

[[10분 테코톡\] 🦊닉의 Spring vs Spring Boot](https://youtu.be/6h9qmKWK6Io)

[[10분 테코톡\] 🏀 에어의 Spring vs Spring Boot](https://youtu.be/Y11h-NUmNXI)

[[10분 테코톡\] 오잉의 Spring vs Spring Boot](https://youtu.be/YdE4krx0dsM)