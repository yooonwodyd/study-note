[[자바]]

# 기본형 매개변수와 참조형 매개변수

우리가 흔히 말하는 기본 데이터 타입의 경우,  스택 메모리에 직접 값을 저장하며, 값 자체를 복사하여 전달한다.
객체의 경우 stack 영역에 저장된 heap 메모리 주소로 접근한다. 

이를 통해 봤을 때 매개변수에 int 타입이 주어질 때는, 스택메모리에 값이 복사되어 저장됨으로 두 변수간의 값이 일치 하지 않는다는 것을 이해하기 쉽다.

그렇다면 기본 데이터 타입을 객체처럼 사용하는 Wrapper 클래스의 경우에는 값이 변하지 않을 까?

## Wrapper 클래스 예제
```java
public class Main {  
      
    public static void main(String[] args) {  
        Integer n = 5;  
        printN(n);  
        System.out.println(n);  
    }  
  
    public static void printN(Integer n){  
        System.out.println(n);  
        n = 10;  
    }  
}
```
위 코드의 출력 결과는 기본 데이터 타입과 다르지 않다.

그 이유는 다름이 아니라 해당 클래스가 **불변클래스** 이기 때문이다.

이때 자바는 다음과 같이 동작한다.
```java
Integer x = 5;
x = x + 1; // 새로운 Integer 객체가 생성되어 x가 해당 객체를 참조하게 됨
```

일단. 5는 int 타입이다. Integer x = 5 라는 코드를 자바는 오토박싱이라는 기능을 통해서 자바 컴파일러가 Integer x = Integer.valueOf(5) 와 같이 동작하도록 변화시킨다.

따라서. 위의 코드에서 n = 10의 경우 n에 새로운 힙 메모리 주소값이 들어간 것 이기에 
main 메서드의 n와 값이 일치하지 않는다는 것이다.

