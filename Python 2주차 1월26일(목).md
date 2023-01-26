# 1/26(목)

```Python
# 문자열이 주어지면 숫자, 문자, 기호가 몇 개인지 출력하는 함수를 만들어라

def check(input_str):
    char_count = 0
    digit_count = 0
    symbol_count = 0

    for char in input_str:
        if char.isalpha():
            char_count += 1
        elif char.isdigit():
            digit_count += 1
        else:
            symbol_count += 1
    return char_count, digit_count, symbol_count

input_str = "123#$%abc"
char_count, digit_count, symbol_count = check(input_str)
print(f'char: {char_count}, digit: {digit_count}, symbol: {symbol_count}')
# char: 3, digit: 3, symbol: 3
```



## 데이터 구조(이전 수업에서 이어짐)

* 여러 데이터를 효과적으로 사용, 관리하기 위한 구조 (많이 사용해보니까 비슷한 구조가 있음)
* List, Tuple, Dict, Set 등



### 순서가 없는 데이터 구조

#### 셋(Set) → 집합으로 알고 있으면 됨

* 중복 요소 없이 순서에 상관없는 데이터들의 묶음
* 데이터 중복을 허용하지 않기 때문에 중복되는 원소가 있다면 하나만 저장
* 순서가 없기 때문에 인덱스 이용한 접근 불가능
* 담고 있는 요소를 삽입, 변경, 삭제 가능 → 가변 자료형 (Mutable)
* 셋 메서드 종류
  * copy(), add(x), pop() (임의 원소 제거 뒤 반환), remove(s), discard(x), update(t), clear(), isdisjoint(t), issubset(t), issuperset(t)

#### 딕셔너리(Dictionary)

* 키-값(key-value) 쌍으로 이루어진 자료형 (파이썬 버전 3.7 부터는 ordered, 이하 버전은 unordered)

* key → 변경불가능 데이터만 활용가능 (immutable)

  * string, integer, float, boolean, tuple, range 등

* value → 어떠한 형태든 관계없음

* 중요한 딕셔너리 메서드

  * keys() : 딕셔너리 내의 모든 키를 담은 뷰를 반환 (뷰: 반복가능한 객체)

  * values() : 딕셔너리 내의 모든 값을 담은 뷰를 반환

  * get(k) : 키 k의 값을 반환, k가 딕셔너리에 없을 경우 None 반환

    cf) dict['k'] → k가 딕셔너리에 없을 경우 error 발생

  * get(k, v) : 키 k의 값을 반환, k가 딕셔너리에 없을 경우 v 반환

```python
sample_list = [11, 22, 33, 55, 66]

# 주어진 리스트의 3번 인덱스에 있는 항목을 제거하고 변수에 할당하기

print('original list: ', sample_list)  # original list:  [11, 22, 33, 55, 66]

x = sample_list.pop(3)

print('list after: ', sample_list)  # list after:  [11, 22, 33, 66]
print('elem: ', x)  # elem:  55

# sample_list의 가장 뒤에 77 추가하기
sample_list.append(77)
print(sample_list)  # [11, 22, 33, 66, 77]

# 할당해놓은 변수의 값을 sample_list의 2번 인덱스에 추가하기
sample_list.insert(2,x)
print(sample_list)  # [11, 22, 55, 33, 66, 77]
```



```python
my_tuple = (11, 22, 33, 44, 55, 66)

# 주어진 튜플에서 44와 55의 값을 새로운 튜플에 할당하기

new_tuple = my_tuple[3:5]
print(new_tuple)  # (44, 55)

new_tuple = my_tuple[3:-1]
print(new_tuple)  # (44, 55)
```



### 얕은 복사와 깊은 복사 → 조금 더 봐야할 듯

#### 기존 변수 사용 문제점

* 하나의 기억에 하나의 주소가 필요함 == 100개 저장할려면 주소 100개 필요

  → 연속적인 공간에 데이터 저장되도록 하여 맨 처음 기억의 주소만 갖게 함

* 두 변수를 서로 다른 주소를 갖게 하고 싶음 → 깊은 복사

```python
a = [1, 2, 3]
b = a
print(b)  # 얕은 복사
```

* 복사 방법

  * 할당 (Assignment)

  * 얕은 복사 (Shallow copy)

  * 깊은 복사 (Deep copy)

#### 할당 (Assignment)

* 대입 연산자 (=) 활용
  * 대입 연산자를 통한 복사는 해당 객체에 대한 객체 참조를 복사
  * 해당 주소의 일부 값을 변경하는 경우 이를 참조하는 모든 변수에 영향

#### 얕은 복사(Shallow copy)

* Slice 연산자 활용 시 같은 원소를 가져도 다른 주소로 복사됨

  cf) 리스트 내에 리스트가 원소로 존재하는 경우 → 기존 변수로 지정된 값도 같이 바뀜

  ​	→ 깊은 복사라고 생각하면 안됨

#### 깊은 복사(Deep copy)

* import copy

  copy.deepcopy() 사용하여 다른 주소로 할당시켜서 복사하기

##### 결론

* 리스트 복사 시 print 찍어볼 것
* copy.deepcopy() 써도 되지만 컴퓨터 메모리 용량 증가함

```python
test_list = [1, 2, 3, 7, 4, 6, 5]
test_list.sort()
# print(test_list)

scores = [('eng', 88), ('sci', 90), ('math', 80)]

def check(x):
    return x[1]
# 정렬
print(scores)  # [('eng', 88), ('sci', 90), ('math', 80)]
scores.sort(key=check)
print(scores)  # [('math', 80), ('eng', 88), ('sci', 90)]
               # sort 조건 없으면 tuple의 0번 인덱스 기준으로 정렬함
```

```python
test_list = [1, 2, 3, 7, 4, 6, 5]
test_list.sort()
# print(test_list)

scores = [('eng', 88), ('sci', 90), ('math', 80)]

# 정렬
print(scores)  # [('eng', 88), ('sci', 90), ('math', 80)]
scores.sort(key=lambda x: x[1])  # 간단한 함수의 경우 함수 정의 대신 lambda 사용하면 됨
print(scores)  # [('math', 80), ('eng', 88), ('sci', 90)]
```



### 함수 vs 메서드

* 내 생각이라 정답은 아님

  함수 → 매개변수를 활용하여 독립적으로 사용가능

  메서드 → 지정한 특정 자료형(문자열, 리스트, 딕셔너리, 세트 등)에서 기능 수행

  ​				 특정 자료형 없이 독립적으로 사용하면 '정의되지 않음'이라고 뜸

  ​				 메서드와 같은 이름의 새로운 함수를 만들어도 메서드 기능에 영향X

​	