# 1/19(목)

* 함수를 쓰는 이유 → Decomposition(분해), Abstraction(추상화)



## 함수 응용

### 내장 함수(Built-in Functions)

* 파이썬 인터프리터에는 항상 사용할 수 있는 많은 함수와 형(type)이 내장되어 있음

  (MM에 올라온 내장함수 사진 참고)

### map

map(function, iterable)

* 순회 가능한 데이터 구조(iterable)의 모든 요소에 함수(function) 적용하고 그 결과를 map object로 반환

```python
n,m= map(int, input().split()) # input에 3 5 입력
print(n,m) # 3 5
print(type(n), type(m)) # <class 'int'> <class 'int'>
```

* split() → 공백을 기준으로 나눠줌

### fliter

fliter(function, iterable)

* 순회 가능한 데이터 구조(iterable)의 모든 요소에 함수(function) 적용하고 그 결과가 True인 것들을 fliter object로 반환

```python
def odd(n):
    return n % 2
numbers =[1,2,3]
result = filter(odd,numbers)
print(result, type(result)) # <filter object at 0x00000218A1FB2370> <class 'filter'>

print(list(result)) # [1,3]
```

### zip

zip(*iterables)

* 복수의 iterable을 모아 튜플을 원소로 하는 zip object 반환

```python
girls = ['jane', 'ashley']
boys = ['justin', 'eric']
pair = zip(girls, boys)
print(pair, type(pair)) # <zip object at 0x0000027781490880> <class 'zip'>
print(list(pair)) # [('jane', 'justin'), ('ashley', 'eric')]
```

### lambda 함수(익명함수)

lambda [parameter]  : 표현식(매개변수를 이용한 리턴값)

* 표현식을 계산한 결과값을 반환하는 함수, 이름이 없는 함수
* return문을 가질 수 없음, 간편 조건문 외 조건문과 반복문을 가질 수 없음
* 함수를 정의해서 사용하는 것 보다 간결하게 사용 가능
* def 사용 못하는 곳에서도 사용 가능

```python
# 삼각형 넓이 공식 - def
def triangle_area(b,h):
    return 0.5 * b * h
print(triangle_area(5, 6)) # 15.0

# 삼각형 넓이 공식 - lambda
triangle_area = lambda b, h : 0.5 * b * h
print(triangle_area(5, 6)) # 15.0
```

```python
rlt = (lambda x: x * x)(4)
print(rlt) # 16

my_func = lambda n : n*2
print(my_func(2)) # 4
```

* function 자리에 lambda로 함수 입력해도 적용됨 (간단한 함수 입력할 때 활용하면 됨)

### 재귀 함수(Recursive function)

* 자기 자신을 호출하는 함수

* for, while 등의 반복문보다 재귀 함수를 이용할 때가 편한 경우도 존재

* factorial

  ```python
  def factorial(n):
      if n == 0 or n == 1:
          return 1
      else:
          return n * factorial(n-1)
  
  print(factorial(4)) # 24
  ```

* 재귀를 끝낼 조건을 만들어줘야함

  ```python
  def factorial(n):
      return n * factorial(n-1)
  
  print(factorial(4)) # n 무한 반복으로 끝나지 않음(recursion error)
                      # n==0, n==1 조건 만들어줘야함
  ```

* 재귀함수 실행은 처음부터 시작하지만 계산은 마지막부터 시작

	#### 반복문과 재귀함수 비교

* 알고리즘 자체가 재귀적인 표현이 자연스러운 경우 재귀함수 사용
* 재귀 호출 → 변수 사용 줄이기 가능 but 입력 값이 커질 수록 연산속도가 오래 걸림



### Packing/Unpacking

* 패킹/언패킹 연산자 * : 모든 시퀀스 형은 연산자 *(Asterisk)를 이용하여 객체 패킹/언패킹 가능

  ```python
  # 패킹
  a,*b = 1,2,3,4
  print(a,b) # 1 [2,3,4]
  
  # 언패킹
  def my_sum(a,b,c):
      return a+b+c
  
  num_list = [10, 20, 30]
  # rlt = my_sum(num_list[0],num_list[1], num_list[2])
  rlt = my_sum(*num_list) # 리스트 언패킹 적용
  print(rlt) # 60
  ```

### 가변 인자(*args)

* 여러 개의 Positional Argument를 하나의 필수 parameter로 받아서 사용

* 몇 개의 Positional Argument를 받을 지 모르는 함수 정의에 유용

  ```python
  # Positional 가변 인자
  def test(*args):
      print(args,type(kwargs))
      return args
  
  test(1,2,3) # (1, 2, 3) <class 'tuple'>
  
  # Keyword 가변 인자 → **(2개)사용
  def test(**kwargs):
      print(kwargs,type(kwargs))
      return kwargs
  
  test(name='aiden', age=21) # {'name': 'aiden', 'age': 21} <class 'dict'>
  
  # Positional, Keyword 다 넣고 싶을 때
  def test(*args, **kwargs):
      print(args, kwargs,type(kwargs))
      return kwargs
  
  test(1,2,3,4, name='aiden', age=21)
  # (1, 2, 3, 4) {'name': 'aiden', 'age': 21} <class 'dict'>
  ```



## 모듈

* 파이썬에서의 모듈 = pythonfile.py
* 다양한 기능을 하나의 파일로 → 모듈(Module)
* 다양한 파일을 하나의 폴더로 → 패키지(Package)
* 다양한 패키지를 하나의 묶음으로 → 라이브러리(Library)
* 이들을 관리하는 관리자 → pip
* 패키지 활용 공간 → 가상환경

	### 모듈

* 특정 기능을 하는 코드를 파이썬 파일(.py) 단위로 작성한 것

### 패키지

* 여러 모듈의 집합
* 패키지 안에 또 다른 서브 패키지를 포함

##### 모듈, 패키지 불러오기

* import, from 등으로 부름
  * import [모듈]
  * from [모듈] import [불러올 함수]
  * from [모듈] import * → 모듈에 있는 모든 함수 부름
  * from [패키지] import [모듈]
  * from [패키지], [모듈] import [함수]

### 파이썬 라이브러리

* 파이썬에는 기본적으로 설치된 모듈과 내장 함수가 존재

### 파이썬 패키지 관리자(pip)

* PyPI(Python Package Index)에 저장된 외부 패키지들을 설치하도록 도와주는 패키지 관리 시스템
* 패키지 설치
  * $ pip install [패키지명]
  * $ pip install [패키지명]==[버전] → 특정 버전만 설치
  * $ pip install [패키지명]>=[버전] → 특정 버전 이상의 버전들 설치
* 패키지 삭제
  * $ pip uninstall [패키지명]
* 패키지 목록
  * $ pip list
* 특정 패키지 정보
  * $ pip show [패키지명]
* 패키지 관리
  * $ pip freeze > requirements.txt
  * $ pip install -r requirements.txt

### 모듈과 패키지 활용

* 패키지는 여러 모듈/하위 패키지로 구조화
* 모든 폴더에는 __init__.py를 만들어 패키지로 인식

### 가상환경



