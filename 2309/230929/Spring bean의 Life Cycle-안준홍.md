# Spring Bean의 Life Cycle
1. Spring IOC 컨테이너 생성
<br>

2. Spring Bean 생성
3. 의존관계 주입
4. 초기화 콜백 메소드 호출
5. 객체 사용
6. 객체 소멸 전 콜백 메소드 호출
7. Spring 종료


```markdown
**Spring Bean이란?**
IOC 컨테이너에 등록된 객체를 말합니다.
```

<br>

### Spring에서 빈 생명주기 콜백 관리 방법

1. 인터페이스( InitializingBean, DisposableBean )
2. 설정 정보에 초기화 메소드, 종료 메소드 지정
3. @PostConstruct, @PreDestroy 어노테이션 지원

---
### 참조
- https://dodokwon.tistory.com/57