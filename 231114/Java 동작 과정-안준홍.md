# Java 동작 과정

1. `javac.exe`라는 컴파일러가 `.java`파일을 `.class`파일(java byte code)로 변환합니다.

<br>

2. `.class` 파일을 **JVM**이 컴퓨터가 읽을 수 있는 기계어로 변환해줍니다.
    ``` md
    **JVM 구조**
    - Class Loader: JVM 내로 `.class`파일을 로드해서 Runtime Data Area에 적재하는 역할입니다.
    - Excution Engine: Runtime Data Area에 올라간 ByteCode(`.class` 파일)를 기계어로 변환해서 명령어 단위로 실행합니다.
    - Runtime Data Area: Byte Code를 적재하는 메모리 영역으로 Method, Heap, Stack, PC Register, Native Method Stack으로 구성되어 있습니다.
    - Garbage Collector: Heap 영역에 적재된 객체들 중 참조되고 있지 않은 객체들을 정리합니다.

    **JVM 동작 과정**
    1. Class Loader에서 `.class`를 로드
    2. Excution Engine에서 인터프리터 or JIT 컴파일러를 통해 각 운영체제에 맞춰 명령어 실행
    ```

<br>

3. JVM의 Exution Engine이 변환한 기계어를 인터프리터 or JIT 컴파일러를 통해 각 운영체제에 맞춰 실행합니다.
    ```md
    **인터프리터**
    - 한 줄씩 해석하고 실행하는 방식의 명령어 실행 방식
    - 줄 단위로 번역, 실행되기 때문에 프로그램의 변화에 대응이 빠르고 시분할 시스템에 적합합니다.

    **JIT(Just In Time) 컴파일러**
    - 한 번에 모두 번역, 실행을 진행하고 번역한 명령어를 캐시에 저장합니다.
    - 캐시에 저장되어 있기에 다시 번역하지 않고 실행이 가능하며, 부분 변경이 있을 경우 해당 부분만 컴파일 후 캐시에 저장합니다.

    -> JVM은 해당 메소드가 얼마나 자주 사용되는지에 따라 실행 방식을 결정합니다. 메소드가 자주 사용되면 JIT 컴파일 방식을 선택하게 됩니다.
    ```