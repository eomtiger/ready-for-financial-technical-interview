# Wrapper Class란?
> 래퍼 클래스란 기본 자료 타입(char, int, float, double, boolean 등)들을 객체로 다루기 위해서 사용하는 클래스를 말합니다.

자바는 모든 기본타입 값을 갖는 객체를 생성할 수 있습니다.
|기본 타입(primitive type)|래퍼 클래스(wrapper class)|
|---|---|
|byte|Byte|
|char|Character|
|int|Integer|
|float|Float|
|double|Double|
|boolean|Boolean|
|long|Long|
|short|Short|

<br>

### 박싱(Boxing)과 언박싱(UnBoxing)
> 기본 타입에서 래퍼 클래스로 변환하는 것을 **박싱**  
래퍼 클래스에서 기본 타입으로 변환하는 것을 **언박싱**이라고 합니다.

자바에서는 모든 경우는 아니지만 대부분의 경우에 자동 박싱(auto boxing) 또는 자동 언방식(auto unboxing)이 이루어집니다.

<Br>

---

### 참고
- https://dev-coco.tistory.com/9