# 42. 익명 클래스보다는 람다를 사용하라

## 익명 클래스

- 함수 객체를 만들던 수단
- 문제점 - 너무 긴 코드
    
    ```java
    Collections.sort(words, new Comparator<String>() {
                public int compare(String s1, String s2) {
                    return Integer.compare(s1.length(), s2.length());
                }
            });
    ```
    

---

## 람다식

- **함수형 인터페이스**의 인스턴스
- 등장배경
    
    자바 8에 함수형 프로그래밍 도입
    
- 장점 - **간단명료**한 코드
    
    ```java
    Collections.sort(words,
                    (s1, s2) -> Integer.compare(s1.length(), s2.length()));
    ```
    

### 사용 규칙

- 타입을 명시해야 코드가 더 명확할 때만 제외하고는, **람다의 모든 매개변수타입은 생략**한다.
    
    컴파일러가 문맥을 살펴 타입을 추론하므로 타입을 명시할 필요가 없다.
    
- **코드 자체로 동작이 명확히 설명되지 않거나, 코드 줄 수가 많아지면** 람다 사용을 지양한다.
    
    람다는 이름이 없고 문서화가 어렵다.
    
- 람다는 함수형 인터페이스에만 사용한다. 다음의 경우, **익명 클래스를 사용**한다.
    - 추상 클래스의 인스턴스를 만들 때,
    - 추상 메서드가 여러 개인 인터페이스의 인스턴스를 만들 때,
    - 함수 객체가 자신을 참조할 때.
        
        람다는 자신을 참조할 수 없다. 람다의 `this`는 바깥 인스턴스를 가리킨다.
        
- 람다를 **직렬화하는 것은 극히 삼가**한다. (익명클래스의 인스턴스도 마찬가지이다.)
    
    직렬화해야하는 객체가 있다면 private 정적 중첩 클래스의 인스턴스를 사용하는 것을 추천한다.
