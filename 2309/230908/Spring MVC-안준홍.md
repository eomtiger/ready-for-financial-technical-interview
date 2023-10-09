# Spring MVC란?
서블릿(Servlet) API를 기반으로 클라이언트의 요청을 처리하는 모듈을 의미합니다.

<br>

# MVC란?
> `Model`, `View`, `Controller`의 약자이며 각 레이어간 기능을 구분하는데 중점을 둔 디자인 입니다.
- `Model` : **데이터 관리 및 비즈니스 로직**을 처리합니다.(DAO, DTO, Service)
- `View` : **비즈니스 로직의 처리 결과를 통해 유저 인터페이스가 표현**되는 구간입니다.(html, jsp, tymeleaf 등으로 화면을 구성하거나 Rest API에서 json 응답으로 구성되기도 합니다.)
- `Controller` : 사용자의 요청을 처리하고 **Model과 View를 중개하는 역할**을 합니다.(Model과 View는 서로 연결되어 있지 않기 때문에 Controller가 사이에서 통신하는 매체가 되어줍니다.)

<br>

# MVC의 요청 처리 흐름
<img src='./assets/MVC.png'>

`DispatcherServlet`: 클라이언트에게 요청을 받아 응답까지의 MVC 처리 과정을 통제합니다.
`HandlerMapping`: 클라이언트의 요청 URL을 처리할 `Controller`를 결정합니다.
`HandlerAdapter`: `HandlerMapping`에서 결정된 `Controller`로 요청을 전달합니다.
`ViewResolver`: `Controller`의 처리 결과를 생성할 view를 결정합니다.

1. 클라이언트가 URL을 통해 요청을 전송
2. `DispatcherServlet`은 `HandlerMapping`을 통해 요청을 전달할 `Controller` 탐색
3. `HandlerAdapter`를 통해 `Controller`에 전달
4. `Controller`는 비즈니스 로직을 처리 후 반환할 view의 이름을 반환
5. `DispatcherServlet`은 `ViewResolver`를 통해 반환할 view를 탐색
6. `Controller`에서 view에 데이터를 전달
7. 데이터가 추가된 view를 클라이언트에게 반환

---
### 참조
- https://dev-coco.tistory.com/163
- https://velog.io/@se_bb/Spring-Framework-7%EA%B0%95-Spring-MVC-%EC%86%8C%EA%B0%9C