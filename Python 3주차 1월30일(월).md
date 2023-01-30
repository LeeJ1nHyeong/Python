# 1/30(월)

### 함수 vs 메서드

* 함수는 단독으로 사용가능, 메서드는 객체 안에 있는 함수로 객체 없이 사용 불가



## 객체 지향 프로그래밍(Object-Oriented Programming, OOP)

* 컴퓨터 프로그래밍의 패러다임 중 하나
* 컴퓨터 프로그램을 명령어의 목록으로 보는 시각에서 벗어나 여러 개의 독립된 단위, 즉 "객체"들의 모임으로 파악하고자 하는 것
* 각자의 객체는 메세지를 주고받고 데이터를 처리할 수 있다.
* 지향 → 기반으로 바꿔서 해석하면 쉽게 이해될수도 있음.



### 절차 지향 프로그래밍

* 프로그램 전체가 유기적인 흐름으로 연결

* 기능 중심의 프로그램

* 순서가 정해져 있어 실행이 빠름

* 하지만 하드웨어가 발전하면서 소프트웨어도 점점 커지고 복잡한 설계가 요구됨

  → 소프트웨어 위기(Software Crisis)

* '절차'대신 핵심이 되는 '데이터' 중심으로 생각하자 == OOP

### 객체 지향 프로그래밍

* 프로그램을 여러 개의 독립된 객체들과 그 객체 간의 상호작용으로 파악하는 프로그래밍 방법

  ex) 콘서트

  * 가수 객체
  * 감독 객체
  * 관객 객체

* 장점

  * 잘 만들어 놓으면 계속해서 재사용 가능
  * 객체 그 자체로 데이터와 행동이 정의됨(독립적) == 개발자가 내부 구조를 몰라도 그냥 가져다가 다른 객체와 조립하면서 개발 가능
  * 객체 단위로 모듈화시켜 개발 가능 → 많은 인원이 참여하는 대규모 소프트웨어 개발 가능
  * 개발 용이성, 유지 보수 편의성, 신뢰성을 바탕으로 생산성 대폭 증가

* 단점

  * 설계 시 많은 노력과 시간이 필요함
    * 다양한 객체들의 상호 작용 구조를 만들기 위해 많은 시간과 노력이 필요 (초기 비용이 든다)
  * 실행 속도가 상대적으로 느림
    * 절차 지향의 경우 컴퓨터 처리구조와 비슷하여 실행속도가 빠름



### OOP 기초

#### 객체

* 클래스에서 정의한 것을 토대로 메모리(실제 저장공간)에 할당된 것
* 프로그램에서 사용되는 데이터 또는 식별자에 의해 참조되는 공간
* 속성과 행동으로 구성된 모든 것
  * 속성 → 변수,   행동 → 함수 또는 메서드로 설계
* 클래스로 만든 객체 → 인스턴스

```python
name = 'Lee'
print(type(name))  # <class 'str'>

age = 28
print(type(age))  # <class 'int'>
```

​	→ 파이썬은 모든 것이 객체(Object) == 파이썬의 모든 것엔 속성과 행동이 존재

#### 객체와 인스턴스

* 객체 == 나만의 타입을 만듦
* 인스턴스 == 그 객체에서 만든 실제 사례
* 객체의 설계도(클래스)를 가지고 객체(인스턴스)를 생성한다.

 #### 객체의 특징

* 타입(type) : 어떤 연산자(operator)와 조작(method)이 가능한가?
* 속성(attribute) : 어떤 상태(데이터)를 가지는가?
* 조작법(method) : 어떤 행위(함수)를 할 수 있는가?



### OOP 문법

#### 기본 문법

```python
# 클래스 정의 == 나만의 타입 생성, 무언가를 생성하는 틀 제작
class MyClass:
    pass

# 인스턴스 생성
my_instance = Myclass()

# 메서드 호출
my_instance.my_method()

# 속성 접근
my_instance.my_attribute
```

* 클래스 : 객체들의 분류 / 설계도(Class)
* 인스턴스 : 하나하나의 실체 / 예(Instance)

```python
class Person:
	pass
	
print(type(Person)) # <class 'type'>

person1 = Person()

print(isinstance(person1, Person)) # True
print(type(person1)) # <class '__main<<.Person'>
```

#### 객체 비교하기

* ==
  * 동등한(equal)
  * 변수가 참조하는 객체가 동등한(내용이 같은) 경우 True
  * 두 객체가 같아 보이지만 실제로 동일한 대상을 가리키고 있다고 확인해 준 것은 아님
* is
  * 동일한(identical)
  * 두 변수가 동일한 객체를 가리키는 경우 True

#### 속성

* 특정 데이터 타입/클래스의 객체들이 가지게 될 상태/데이터를 의미
* 클래스 변수 /  인스턴스 변수가 존재

#### 인스턴스와 클래스 간의 이름 공간(namespace)

* 클래스를 정의하면 클래스와 해당하는 이름 공간 생성
* 인스턴스를 만들면, 인스턴스 객체가 생성되고 이름 공간 생성
* 인스턴스에서 특정 속성에 접근하면 인스턴스-클래스 순으로 탐색

```python
# Person 정의
class Person:
    name = 'unknown'
    
    def talk(self):
        print(self.name)
        
p1 = Person()
p1.talk()  # unknown

# p2 인스턴스 변수 설정 전/후
p2 = Person()
p2.talk()  # unknown
p2.name = 'Kim'
p2.talk()  # Kim

print(Person.name)  # unknown
print(p1.name)  # unknown
print(p2.name)  # Kim
```

#### 인스턴스 변수

* 인스턴스가 개인적으로 가지고 있는 속성(attribute)
* 각 인스턴스들의 고유한 변수
* 생성자 메서드(____init____) 에서 self.<name>으로 정의
* 인스턴스가 생성된 이후 <instance>.<name>으로 접근 및 할당

```python
class Person:

    def __init__(self, name):
        self.name = name
       
john = Person('john')
print(john.name)  # john
john.name = 'John Kim'
print(john.name)  # John Kim
```

#### 클래스 변수

* 한 클래스의 모든 인스턴스가 공유하는 값을 의미

* 같은 클래스의 인스턴스들은 같은 값을 갖게 됨

  ex) 특정 사이트의 User 수 등은 클래스 변수를 사용해야 함

* 클래스 선언 내부에서 정의

* <classname>. <name>으로 접근 및 할당

```python
class Circle():
    pi = 3.14  # 클래스 변수 정의
    
    def __init__(self, r):
        self.r = r  # 인스턴스 변수

c1 = Circle(5)
c2 = Circle(10)

print(Circle.pi)  # 3.14
print(c1.pi)  # 3.14
print(c2.pi)  # 3.14

Circle.pi = 5
print(Circle.pi)  # 5
print(c1.pi)  # 5
print(c2.pi)  # 5
```

#### 클래스 변수 활용(사용자 수 계산하기)

* 사용자가 몇 명인지 확인하고 싶다면?
  * 인스턴스가 생성될 때마다 클래스 변수가 늘어나도록 설정할 수 있음

```python
class Person:
    count = 0
    # 인스턴스 변수 설정
    def __init__(self, name):
        self.name = name
        Person.count += 1

person1 = Person('아이유')
person2 = Person('이찬혁')

print(Person.count)
```

#### 클래스 변수와 인스턴스 변수

* 클래스 변수 변경 시 항상 클래스.클래스변수 형식으로 변경

```python
class Circle():
    pi = 3.14  # 클래스 변수 정의
    
    def __init__(self, r):
        self.r = r  # 인스턴스 변수

c1 = Circle(5)
c2 = Circle(10)

print(Circle.pi)  # 3.14
print(c1.pi)  # 3.14
print(c2.pi)  # 3.14

Circle.pi = 5
print(Circle.pi)  # 5
print(c1.pi)  # 5
print(c2.pi)  # 5

c2.pi = 5  # 인스턴스 변수 변경
print(Circle.pi)  # 3.14 (클래스 변수)
print(c1.pi)  # 3.14 (클래스 변수)
print(c2.pi)  # 5 (새로운 인스턴스 변수 생성)
```



### OOP 메서드

#### 메서드

* 특정 데이터 타입/클래스의 객체에 공통적으로 적용 가능한 행위(함수)

```python
class Person:

	def talk(self):
        print('안녕')
        
    def eat(self, food):
        print(f'{food}를 냠냠')
        
person1 = Person()
person1.talk()  # 안녕
person1.eat('피자')  # 피자를 냠냠
person1.eat('치킨')  # 치킨을 냠냠
```

* 메서드 종류 : 인스턴스 메서드, 클래스 메서드, 정적 메서드

#### 인스턴스 메서드

* 인스턴스 변수를 사용하거나 인스턴스 변수에 값을 설정하는 메서드
* 클래스 내부에 정의되는 메서드의 기본
* 호출 시, 첫번째 인자로 인스턴스 자기자신(self)이 자동으로 전달됨

```python
class MyClass:

	def instance_method(self, arg1, ...):
        
my_instance = MyClass()
my_instance.instance_method(...)
```

##### self

* 인스턴스 자기 자신
* 파이썬에서 인스턴스 메서드는 호출 시 첫번째 인자로 인스턴스 자신이 전달되게 설계
  * 매개변수 이름으로 self를 첫번째 인자로 정의
  * 다른 단어로 써도 작동하지만, 파이썬의 암묵적인 규칙

#### 매직 메서드

* Double underscore(__)가 있는 메서드는 특수한 동작을 위해 만들어진 메서드로, 스페셜 메서드 혹은 매직 메서드라고 불림

* 특정 상황에서 자동으로 불리는 메서드

  ex) ____str____(self), ____len____(self), ____lt____(self, other), ____le____(self, other), ____eq____(self, other)

  ​	____gt____(self, other), ____ge____(self, other), ____ne____(self, other)

* 예시

  * 객체 특수 조작 행위 지정 (함수, 연산자 등)
    * ____str____ : 이 객체를 문자열로 표현하면 어떻게 표현할 지 지정
      * print 함수 등에서 객체를 출력하면 자동으로 호출되는 메서드
    * ____gt____ : 부등호 연산자(>, greater than)

```python
class Person:
	def __init__(self, name, age):
        print('생성될 때 자동으로 불러요')
        self.name = name
        self.age = age
        
    def __str__(self):
        pass
    
aiden = Person('aiden',23)        
```

#### 생성자(Constructor) 메서드

* 인스턴스 객체가 생성될 때 자동으로 호출되는 메서드
* 인스턴스 변수들의 초기값을 설정
  * 인스턴스 생성
  * ____init____ 메서드 자동 호출



### 클래스 메서드

* 클래스가 사용할 메서드

* @classmethod 데코레이터를 사용하여 정의

* 호출 시, 첫번째 인자로 클래스(cls)가 전달됨

  ```python
  class MyClass:
  
  	@classmethod
      def class_method(cls, arg1, ...):
  
  MyClass.class_method(...)
  ```

* 예시

  ```python
  class Person:
      count = 0  # 클래스 변수
      def __init__(self, name):  # 인스턴스 변수 설정
          self.name = name
          Person.count += 1
          
      @classmethod
      def number_of_population(cls):
          print(f'인구수는 {cls.count}입니다.')
          
  person1 = Person('아이유')
  person2 = Person('이찬혁')
  
  Person.number_of_population()  # 인구수는 2입니다.
  person1.number_of_population()  # 인구수는 2입니다.
  person2.number_of_population()  # 인구수는 2입니다.
  ```



### 요약정리(조 발표 내용 정리)

예전에는 절차 지향 기반 -> 기능 중심
프로그램이 커지면서 설계에 어려움을 느낌
절차 즉 순서 대신 데이터 중심으로 프로그래밍 시작

클래스 == 만들고 싶은 객체의 틀
인스턴스 == 클래스를 바탕으로 만들어진 객체

클래스 제작자가 초반에만 창작의 고통을 겪기만 하면 이후 다른 사람들이 편해질 수 있다.


(공장으로 비유)
어떤 사업을 진행할 때 a라는 제품이 필요하다면 이들을 만드는 공장이 있다고 가정 (프로그래밍)

한 곳에서 모든 부품을 만들어서 제작 -> 절차 지향

부품 제작 분업화 하여 각각의 부품을 가져와서 조립 -> 객체 지향

부품공장 == Class
부품공장에서 만든 부품 == Instance


함수의 부분집합이 메서드
함수는 단독으로 사용가능 but 메서드는 객체 없이 사용 불가

인스턴스 메서드 → 클래스 내의 인스턴스에 사용하는 메서드
- self : 인스턴스 자기 자신

매직 메서드 : 특수한 동작을 가진 메서드 (필요할 때 기능을 하는 매직 메서드를 찾아 이용하면 됨)
→ ____init____ -> 생성자 메서드
____str____ : 객체출력 시 호출하고 싶은 문자열 호출

클래스 메서드

