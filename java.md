## Primitive type과 Reference type의 차이

- primitive type은 **문자형(char), 정수형(byte, int, short, long), 실수형(float, double), 논리형(boolean)** 이 있으며 이들은 stack 영역에 실제 값이 바로 저장된다.
- reference type은 **primitive type을 제외한 모든 타입**이다. 대표적으로 class, interface등이 있으며 이들은 stack 영역에 객체의 주소값이 저장되고, 실제 데이터는 heap 영역에 저장된다. 객체의 주소는 항상 4byte이다.
- reference type 중 wrapper class라는 것이 존재하는데, 이는 primitive type을 객체화한 것이다. 모든 primitive type은 wrapper class로 변환할 수 있다.
- (추가) java.math 라이브러리에 BigInteger와 BigDecimal 클래스를 제공한다. BigInteger는 8바이트로 표현할 수 없는 큰 정수를 문자열로 다룰 수 있게한다. BigDecimal은 오차 없는 실수 표현을 문자열로 가능하게 한다.



## 박싱, 언박싱에 대한 설명

- primitive type에서 wrapper class가 되는 과정을 Boxing이라고 하고,  wrapper class 에서 primitive type이 되는 과정을 Unboxing이라고 한다. 보통 이 과정은 타입이 일치한다면 컴파일러에 의해 자동으로 이뤄진다.
- (추가) wrapper class와 비교를 할 때는 .equals() 메서드를 사용하는 것이 안전하다. 하지만 같은 타입의 primitive type의 변수와 비교를 할 때는 컴파일러가 자동으로 박싱과 언박싱을 해줘서 비교 가능하다.



## 제네릭에서 Primitive type을 사용하지 못하는 이유

- Java의 제네릭은 언어가 설계된지 수년 후에 추가된 기능이다. 추가될 때, 제네릭은 기존의 Java 및 라이브러리들과 호환됐어야 했기 때문에 제네릭의 기능에 제한이 생겼다.
- 제네릭의 타입은 컴파일 시간에 결정된다. 컴파일러가 제네릭으로 사용되는 모든 타입을 Object 타입으로 변환할 수 있어야 하기 때문에 Primitive type은 사용될 수 없다.



## call by value와 call by reference의 차이

- **원본 값이 변경되느냐 안되느냐**가 가장 큰 차이점이다.
- call by value는 어떤 함수를 호출할 때, parameter로 값을 복사해서 전달하는 방식이다.
- call by reference는 어떤 함수를 호출할 때, parameter로 주소 값을 전달해서 실제 값에 대한 alias를 구성하고, 함수에서 값을 수정하면 원본 값도 수정되는 방식이다.
- 다만 **Java 에서는 call by value만 지원**하고 있다. 엄밀히 말해보면, 객체를 전달했을 때 이는 객체의 복사본이고, object reference라고 부른다. obejct reference는 필드 또는 메서드에 대해 접근을 허용하는 방식이다. 따라서 이는 call by reference처럼 보이지만, 메모리 상 서로 다른 주소값을 가지고 있다.



## Overload와 Override의 차이

- 오버로딩: 하나의 클래스 내에 동일한 이름의 메서드가 존재하는 경우를 의미한다. 매개변수의 개수, 타입, 반환타입 등이 다를 수 있다. 다만, 반환타입만 다른 것으로는 오버로딩이 될 수 없다. 즉, 매개변수의 개수 및 타입으로만 오버로딩된 메서드를 구별할 수 있다.
- 오버라이딩: 부모 클래스로부터 상속받은 메서드를 자식 클래스에서 재정의하는 경우를 의미한다. 오버라이딩된 메서드는 반환타입, 메서드명, 매개변수 등 구현부를 제외한 다른 부분은 모두 동일해야 한다. 접근 제어자는 부모보다 같거나 넓은 범위의 접근 제어자를 사용할 수 있다.



## Java의 메모리(스택 & 힙)에 관한 내용

- 