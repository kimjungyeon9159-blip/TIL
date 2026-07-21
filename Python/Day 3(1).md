# 함수 

#### 주의점

1. 함수는 보통 동사형태로 변수명을 적음
2. def make_sum(pram1, pram2) 밑에 함수의 바디 부분 작성.
3. return은 반환을 이야기 하기도 하지만, 함수의 종료를 얘기하기도 함.
4. *반환값이 없다면 return none을 반환함.*


### 예시


```
def make_sum(pram1, pram2):
    """이것은 두 수를 받아
    두 수의 합을 반환하는 함수입니다.
    >>>make_sum(1,2)
    3
    """
    return pram1+pram2

result=make_sum(100,30)
print(result)

# =============================================================
# [2] 함수 호출과 반환값 활용
# - 호출한 자리는 '반환된 값'으로 대체된다고 생각하면 이해가 쉬움
#   result = make_sum(100, 30) => result = 130
# =============================================================

# 함수 호출 및 반환 값 할당


# =============================================================
# [3] 반환값이 없는 함수는 None을 반환
# - '출력(print)'과 '반환(return)'은 완전히 다른 개념
# - print()는 화면에 보여줄 뿐, 돌려주는 값은 None
# - 초보자가 가장 많이 혼동하는 지점
# =============================================================

# print() 함수는 반환값이 없다.

value = print('hello world')
print(value)



# -------------------------------------------------------------
# return문이 아예 없는 함수도 마찬가지로 None을 반환
# -------------------------------------------------------------
def my_func():
    print('hello')


result = my_func()
print(result)


```

5. 함수를 한번 만들어 놓으면 아래 어디서든 호출 할 수 있음.
6. *반환값과 출력값이라는건 완전히 다른 개념임을 이해해야한다.*


### 과제1 오답

```
# 아래 함수를 수정하시오.
def add_numbers(pram1,pram2):
    """이것은 두 수를 인자로 받아 합을 결과로 반환하는 함수입니다. 
    >>> add_numbers(1+3)
    4 
    """
    return pram1+pram2

result=add_numbers(3,5)

print(result)


# 수정한 add_numbers() 함수를 호출하시오.
```
#### 주의점
1) 처음 함수 작성할때 두 인자 간 , 로 연결하기 ('+'사용하지 않음)
2) return과 result 헷갈리지 않게 주의하기, return은 값을 반환하는 용도로 def의 내부에 작성해야하는 요소
3) result는 출력을 위해 생성한 단순 변수의 이름
4) def 안 ()에 함수에 사용할 인자르 작성하는 것을 잊지말기


### 실습 1 오답


```
def default_arg_func(arg='기본 값'):
    """입력된 기본 인자값을 return하는 함수
    >>>default_arg_func()"""

    return arg

result_3 = default_arg_func()
result_4 = default_arg_func('다른 값')

print(result_3)
print(result_4)

```

#### 주의점
1) default_arg_func함수의 매개변수 default에 '기본 값' 문자열을 할당하여, 기본 인자값을 가지도록 수정하는 문제임.


# 매개변수와 인자

함수를 정의할 때 : 매개변수, 함수를 호출할 때 : 인자

## 인자

### 1)위치인자


  1. 위치 인자는 함수 호출 시 반드시 값을 전달해야함.
  
  2. 위치 인자는 그 위치에 있는 값이 필수적으로 들어가야함

  3. 인자가 누락되는 것도 안됨.but 기본인자가 있으면 누락되어도 기본인자 활용 가능 (아래 예시)

```
# [2] 기본값 인자 (Default Argument Values)
# - 매개변수에 미리 값을 지정해두면, 호출 시 생략 가능
# - 값을 전달하면 기본값 대신 전달한 값이 사용됨
# - 주의: 기본값이 있는 매개변수는 반드시 뒤쪽에 위치해야 함
# =============================================================

# 2. Default Argument Values
def greet(name, age=20):
    print(f'안녕하세요, {name}님! {age}살이시군요.')


greet('Bob')  # 안녕하세요, Bob님! 20살이시군요.
greet('Charlie', 40)  # 안녕하세요, Charlie님! 40살이시군요.

```

### 2) 키워드 인자

1. 호출 할 때 순서를 생각하지 않고 직접 인자에 키워드를 매칭시켜서 호출할 수 있는 방법.

```
# 3. Keyword Arguments
def greet(name, age):
    print(f'안녕하세요, {name}님! {age}살이시군요.')


greet(name='Dave', age=35)  # 안녕하세요, Dave님! 35살이시군요.
greet(age=35, name='Dave')  # 안녕하세요, Dave님! 35살이시군요.
greet(age=35, 'Dave')  # Positional argument cannot appear after keyword arguments
# greet('Dave', age=35)
```

2. 호출 시 키워드 인자는 위치 인자 뒤에 위치해야 함. 

### 3)가변 인자

```
# =============================================================
# [4] 가변 인자 (*args)
# - 개수를 정하지 않고 위치 인자를 여러 개 받음
# - 전달된 값들은 '튜플'로 묶여서(패킹) 들어옴
# - args는 관례적인 이름일 뿐, 핵심은 앞의 * 기호
# =============================================================

# 4. Arbitrary Argument Lists
def calculate_sum(*args):
    print(args)  # (1, 100, 5000, 30)
    print(type(args))  # <class 'tuple'>


calculate_sum(1, 100, 5000, 30)

```


### 4) 

```
# =============================================================
# [5] 가변 키워드 인자 (**kwargs)
# - 개수를 정하지 않고 키워드 인자를 여러 개 받음
# - 전달된 값들은 '딕셔너리'로 묶여서 들어옴
# =============================================================

# 5. Arbitrary Keyword Argument Lists
def print_info(**kwargs):
    print(kwargs)


print_info(name='Eve', age=30)  # {'name': 'Eve', 'age': 30}

```

### 5) 다섯가지 인자 모두 한번에 적용할 때 지켜야 하는 순서 

## 위치 -기본 -가변 - 가변키워드

#### 인자의 모든 종류를 적용한 예시

```

def func(pos1, pos2, default_arg='default', *args, **kwargs):
    print('pos1:', pos1)
    print('pos2:', pos2)
    print('default_arg:', default_arg)
    print('args:', args)
    print('kwargs:', kwargs)


func(1, 2, 3, 4, 5, 6, key1='value1', key2='value2')
"""
pos1: 1
pos2: 2
default_arg: 3
args: (4, 5, 6)  #튜플로 묶임, 가변인자
kwargs: {'key1': 'value1', 'key2': 'value2'}  #딕셔너리로 묶임
"""

```


### 파이썬 공식 문서 (python document 3.11.15) 들어가서 확인

프린트가 어떤 함수로 구성되어있는지 알기 위해 들어가서 확인해보면 좋을 듯 , 
-> 자습서 , 언어 레퍼런스, 공식 문서, 개념, print
-> 자습서 순서가 파이썬 교재 순서와 일치함. 
-> 라이브러리, 내장함수에 들어가서 함수 확인가능. (별도로 만들지 않아도 존재하는 함수)
-> print() 함수 확인 가능. 
-> object: 가변인자, 나머지는 기본인자들

