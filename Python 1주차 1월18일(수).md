# 1/18(수)

### 함수의 종류

* 내장 함수 : 파이썬에 기본적으로 포함된 함수
* 외장 함수 : import 문을 통해 사용, 외부 라이브러리에서 제공하는 함수
* 사용자 정의 함수 : 사용자가 직접 만드는 함수

#### Output

* Void function : 명시적인 return 값이 없는 경우, None을 반환하고 종료
* Value returning function
  * 함수 실행 후, return문을 통해 값 반환
  * return 진행 시 값 반환 후 함수 바로 종료
* 기본적으로 return값은 여러개 설정해도 한가지만 반환(첫번째 return 값)
* 여러 개 반환 시키려면? → 튜플 사용

#### Input

* Parameter(매개 변수) :  함수를 정의할 때 함수 내부에서 사용되는 변수
* Argument(전달 인자) : 함수를 호출할 때 함수의 parameter를 통해 전달되는 값



### Python의 범위(Scope)

* 함수는 코드 내부에 local scope를 생성하며, 그 외의 공간인 global scope로 구분
* LEGB 순으로 변수를 찾고 없으면 Error
* Global scope : 코드 어디에서든 참조할 수 있는 공간
* Local scope : 함수가 만든 scope 함수 내부에서만 참조 가능

#### 이름 검색 규칙(Name Resolution)

* LEGB Rule을 따름
  * Local scope : 지역 범위(현재 작업 중 범위)
  * Enclosed scope : 지역 범위 한 단계 위 범위
  * Global scope : 최상단에 위치한 범위
  * Built-in scope : 모든 것을 담고 있는 범위

#### Variable

* Global variable
* Local variable

#### Namespace : 어떤 식별자를 기억하는 공간

* 같은 이름이 여러 군데에 존재할 수 있다

* Built-in Namespace :
* Global Namespace : 하나의 파이썬 스크립트 내에서 생성
* Enclosing Namespace : 함수가 중첩되어있을 때 바깥 함수에서 생성
* Local Namespace : 함수 내에서 생성

#### 변수 수명주기(Lifecycle)

* 변수는 각자의 수명주기가 존재
  * built-in scope → 파이썬 실행 이후부터 영원히 유지
  * global scope → 모듈 호출 시점 이후 또는 인터프리터 끝날 때까지 유지
  * enclosed scope → 지역 범위 한 단계 위 범위
  * local scope → 함수 호출 시 생성되고 함수 종료까지 유지

```python
x='글로벌'

def func1():
	x='인클로징!'
	
	def func2():
		x='로컬'
		print(x)
		
	func2()
func1()
```

* global → 함수 내에서  global 변수값을 지정
* nonlocal → local을 감싸고 있는 함수의 변수를 가져옴 (global도 아니고 local도 아닌 함수)



### 함수 범위 주의

* 기본적으로 함수에서 선언된 변수는 Local scope에 생성, 함수 종료 시 사라짐
* 해당 scope에 변수가 없을 경우, LEGB 순으로 검색
  * 함수 내에서 필요한 상위 scope 변수는 argument로 넘겨서 활용할 것
* 상위 scope 변수를 수정하고 싶다면 global, nonlocal 키워드 활용 가능
  * 코드가 복잡해지면 변수 변경 추적이 어렵고, 예기치 못한 오류 발생 가능성 존재
  * 가급적 사용 안하는 걸 추천, 필요하다면 항상 argument로 넘기고 리턴 값을 사용하는 것을 추천