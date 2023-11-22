# Web Server
웹 브라우저(클라이언트)로부터 HTTP 요청을 받아 HTML 문서와 같은 정적 컨텐츠*를 제공하는 프로그램  
ex) Nginx, Apache 등

> *정적 컨텐츠  
> 요청 인자 값에 상관없이 달라지지 않는 컨텐츠 (html, css, image 등)  
> 어느 사용자가 요청하든 항상 동일한 컨텐츠

### Web Server의 기능
- 클라이언트로부터 HTTP 요청을 받음
- 정적 컨텐츠를 요청 시 정적 컨텐츠 제공
- 동적 컨텐츠 요청 시 WAS로 전달하여 WAS가 처리한 결과를 클라이언트에 전달
<br>

# WAS (Web Application Server)
DB 조회나 다양한 비즈니스 로직 처리를 요구하는 동적 컨텐츠*를 제공하기 위해 만들어진 프로그램  
ex) Apache Tomcat, PHP, ASP, .NET 등

> *동적 컨텐츠  
> 요청 인자에 따라 바뀔 수 있는 컨텐츠

### WAS의 기능
- 클라이언트로부터 HTTP 요청을 받음 (대부분의 WAS는 Web Server를 내장하고 있음)
- 요청에 맞는 정적 컨텐츠를 제공
- DB조회나 다양한 비즈니스 로직 처리를 통해 동적 컨텐츠를 제공
<br>

# Web Server와 WAS를 구분하는 이유
자원 이용의 효율성 및 장애 극복, 배포 및 유지보수의 편의성을 위해 Web Server와 WAS를 분리  
Web Server를 WAS 앞에 두고 필요한 WAS들을 Web Server에 플러그인 형태로 설정하면 더욱 효율적인 분산 처리가 가능  

### Web Server와 WAS 같이 사용할 경우 장점
- 기능을 분리하여 서버 부하 방지  
  정적 컨텐츠는 Web Server, 동적 컨텐츠는 WAS가 담당하도록 설정  
  WAS가 정적 컨텐츠 요청까지 처리하면 부하가 커지게 되고 동적 컨텐츠 처리가 지연됨에 따라 수행 속도가 느려짐
- 여러 대의 WAS 연결 가능  
  대용량 웹 어플리케이션의 경우(여러 개의 서버 사용) 무중단 운영을 위한 장애 극복에 쉽게 대응
- 여러 웹 어플리케이션 서비스 가능  
  예를 들면 하나의 서버에서 PHP Application과 Java Application을 함께 사용하는 경우
- 물리적으로 분리하여 보안 강화  
  SSL에 대한 암복호와 처리에 Web Server를 사용
<br>

---

### 참고
https://gyoogle.dev/blog/web-knowledge/Web%20Server%EC%99%80%20WAS%EC%9D%98%20%EC%B0%A8%EC%9D%B4.html  
https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html  
https://www.youtube.com/watch?v=mcnJcjbfjrs  
