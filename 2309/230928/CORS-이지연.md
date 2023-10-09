# CORS(Cross-Origin Resource Sharing)란 무엇인가요?
CORS(Cross-Origin Resource Sharing)는 웹 브라우저에서 다른 출처(origin)의 자원을 요청하는 것을 제어하는 보안 메커니즘입니다.

브라우저에서는 보안적인 이유로 cross-origin HTTP 요청들을 제한합니다. 그래서 cross-origin 요청을 하려면 서버의 동의가 필요합니다. 만약 서버가 동의한다면 브라우저에서는 요청을 허락하고, 동의하지 않는다면 브라우저에서 거절합니다.

CORS를 구현하기 위해서는 서버에서 Access-Control-Allow-Origin 헤더를 설정하고, 프론트엔드에서 XMLHttpRequest 객체를 사용하여 요청을 보내야 합니다.

그래서 브라우저에서 cross-origin 요청을 안전하게 할 수 있도록 하는 메커니즘입니다.
