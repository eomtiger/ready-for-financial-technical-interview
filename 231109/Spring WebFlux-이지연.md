### Spring WebFlux란?

Spring WebFlux란 Blocking+동기 방식으로 동작하는 Spring MVC의 한계점을 극복하기 위해 Spring5에 처음 등장하게 되었습니다. 기존의 Spring MVC에서는 HTTP 요청들을 큐에 넣어두고, 멀티쓰레드를 기반으로 동작하고 있습니다. 하지만 이러한 방식은 응답성이 상대적으로 떨어지기 때문에 비동기적으로 요청을 처리하기 위한 방법이 필요하게 되었고, 리액티브 프로그래밍을 통해 비동기 데이터 스트림으로 Non-Blocking 애플리케이션을 개발하기 위한 Spring WebFlux 프레임워크가 등장하게 되었습니다.
