# String, StringBuffer, StringBuilder
Java에서 **문자열을 다루는** 대표적인 클래스들

- **String은 불변**의 속성을 가지며, **StringBuffer와 StringBuilder는 가변**의 속성을 가집니다.  
String 클래스는 불변하기 때문에 문자열을 수정하는 시점에 새로운 String 인스턴스가 생성됨  
따라서 문자열 추가, 수정, 삭제 등의 연산이 빈번하게 발생하는 경우에 String 클래스를 사용하면 힙 메모리(Heap)에 많은 Garbage가 생성되어 힙 메모리 부족으로 성능에 치명적인 영향을 끼침   
- **StringBuffer는 동기화를 지원하여 멀티 쓰레드 환경**에서 주로 사용하며,  
- **StringBuilder는 동기화를 지원하지 않아 싱글 쓰레드 환경**에서 주로 사용합니다.  

아래와 같은 경우에 맞게 사용  
String : 문자열 연산이 적고 멀티쓰레드 환경일 경우  
StringBuffer : 문자열 연산이 많고 멀티쓰레드 환경일 경우  
StringBuilder : 문자열 연산이 많고 단일쓰레드이거나 동기화를 고려하지 않아도 되는 경우  
