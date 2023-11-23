### Comparable
Comparable 인터페이스는 객체를 정렬하는데 사용되는 메소드인 compareTo() 메소드를 정의
- 기본 정렬 순서는 오름차순

- 자바에서 같은 타입의 인스턴스를 비교해야만 하는 클래스는 모두 Comparable 인터페이스를 구현(Boolean을 제외한 래퍼 클래스나 String, Time, Date와 같은 클래스의 인스턴스는 모두 정렬 가능)
```java
class Car implements Comparable<Car> {
    private String modelName;
    private int modelYear;
    private String color;

    Car(String mn, int my, String c) {
        this.modelName = mn;
        this.modelYear = my;
        this.color = c;
    }

 
    public int compareTo(Car obj) {
        if (this.modelYear == obj.modelYear) {
            return 0;
        } 
        else if(this.modelYear < obj.modelYear) {
            return -1;
        } 
        else {
            return 1;
        }
    }
}
```

### Comparator
Comparator 인터페이스는 내림차순이나 아니면 다른 기준으로 정렬하고 싶을 때 사용할 수 있다

-  compare() 메소드를 재정의하여 사용
```java
class DescendingOrder implements Comparator<Integer> {
    public int compare(Integer o1, Integer o2) {
        if(o1 instanceof Comparable && o2 instanceof Comparable) {
            Integer c1 = (Integer)o1;
            Integer c2 = (Integer)o2;
            return c2.compareTo(c1);
        }
        return -1;
    }
}
```

### 출처

https://www.tcpschool.com/java/java_collectionFramework_comparable