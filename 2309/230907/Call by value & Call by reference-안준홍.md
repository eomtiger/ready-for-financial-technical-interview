## Call by Value란?
> **값에 의한 호출**로 인자로 받은 값을 복사하여 처리합니다.

## Call by Reference란?
> **참조에 의한 호출**로 인자로 받은 값의 주소를 참조하여 직접 값에 영향을 줍니다.

<br>

---
## 배경지식
### Call by Value - Java, C언어
- 함수가 호출될 때, 메모리 공간 안에서는 함수를 위한 별도의 임시 공간이 생성됩니다.(종료 시 해당 공각 사라짐)  
- `Call by Value` 호출 방식은 함수 호출 시 전달되는 변수 **값을 복사**해서 함수 인자로 전달합니다.
- 복사된 인자는 함수 안에서 지역적으로 사용되기 때문에 **local value** 속성을 가집니다.
> 함수 안에서 인자 값이 변경 되더라도 외부 변수 값은 변경되지 않습니다.

```C
void func(int n) {
    n = 20;
}

void main() {
    int n = 10;
    func(n);
    printf("%d", n); // 10 출력
}
```

<br>

### Call by Reference - C언어
- 함수가 호출될 때, 인자로 전달되는 변수의 reference를 전달합니다.
> 함수 인자 값이 변경되면 아규먼트로 전달된 객체의 값도 변경됩니다.

```C
void func(int *n) {
    *n = 20;
}

void main() {
    int n = 10;
    func(&n);
    printf("%d", n); // 출력 20
}
```

<br>

### JAVA는?
- Java는 `Call by Value`로서만 동작합니다.
- Java는 C와 달리 포인터를 철저하게 숨겨 **직접 메모리 주소에 접근 하지 못하게 조치** 하기 때문에 `Call by Reference`가 될 수 없습니다.
- 그래도 원시값을 복사하느냐, 주소값을 복사하느냐에 따라 변환 결과가 달라지기 때문에 이를 구분하기 위해 `Call by Value` / `Call by Address`로 구분하기도 합니다.

--- 
### 참조
- https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%9E%90%EB%B0%94%EB%8A%94-Call-by-reference-%EA%B0%9C%EB%85%90%EC%9D%B4-%EC%97%86%EB%8B%A4-%E2%9D%93
- https://sudo-minz.tistory.com/91
- https://github.com/gyoogle/tech-interview-for-developer/blob/master/Language/%5Bjava%5D%20Call%20by%20value%EC%99%80%20Call%20by%20reference.md