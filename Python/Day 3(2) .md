# 재귀함수 활용시 기억할 것

1. 종료 조건을 명확히 할 것
2. 반복되는 호출이 종료 조건을 향하도록 할 것
3. 함수 내부에서는 자기 자신을 호출해야하지만  반드시 return으로 호출하지는 않아도 됨.
4. recursion을 구글에 찾아보면? 이스터에그 처럼 계속해서 물어봄
5. 팩토리얼을 이번에 기억하기

# 함수와 스코프

스코프 -함수의 범위
로컬스코프, 글로벌 스코프 - 함수 바디를 기준으로 내부,외부

built-in scope : 파이썬 실행될 때부터 항상 유지
global scope : 모듈이 포출된 시점 이후 혹은 인터프리터가 끝날 때 까지 유지
local scope : 함수가 호출될 때, 생성되고, 함수가 종료될 때까지 유지






### 재귀함수 만들기 실습

```
def recur_example(number):
    
    """
        함수(2) 실행
            number에 2 할당
            if 2 == 1 조건문 만족하지 않음
            else문 2 + 함수(2-1) 
                결과를 알기위해서는 함수(2-1)의 실행 결과가 필요

                함수(2-1) 실행
                    number에 1 할당
                    if 1 == 1 조건문 만족하므로 1 반환
            
            else문의 2 + 함수(2-1)중, 함수(2-1)의 실행결과가 1임을 알게되었음 
            2 + 1 반환
        결과 : 3  
    """
    if number == 1:
        return 1
    else:
        return number + recur_example(number - 1)
result_1 = recur_example(5)
print(result_1) # 5 + 4 + 3 + 2 + 1 = 15

# 거듭 제곱 재귀 함수
# base = 밑, exponent = 지수
# base의 exponent승 == 2의 3승
def power(base, exponent):
    """
        함수(2, 3) 실행
            base에 2 할당, exponent에 3할당
            지수가 0이 된 경우, 1을 반환 | 2의 0승은 1

            아닌경우, 지수가 0이 될 때까지 [exponent - 1] 을 다시 지수에 할당하여 함수 호출
                2 * 함수(2, 3-1)

            모든 상황을 반복하는 과정
            2 * (2 * (2 * 1))  
            결과 : 8
    """
    if exponent == 0:
        return 1 
    else:
        return base * power(base, exponent-1)
    
result_2 = power(2, 3)
print(result_2) # 2 * 2 * 2 * 1 = 8

# 모든 자릿수 더하기 함수
def sum_of_digits(number):

    """
        함수(321) 실행
        number가 10 미만인 경우, number 반환

        아닌경우, number가 10 미만이 될 때까지, number를 10으로 나눈 몫을 다시 number에 할당하여 함수 호출
            number를 10으로 나누 나머지 + 함수(number를 10으로 나눈 몫)
            1 + (321 // 10)

        모든 상황을 반복하는 과정
        1 + 2 + 3
        결과 : 6
    """
    if number <10:
        return number
    else:
        return number % 10 + sum_of_digits(number//10)
    
result_3 = sum_of_digits(321)
print(result_3) # 1 + 2 + 3 = 6

```



#### 출력값
$ python ws_3_c.py 

15

8

6






## 내장함수의 이름을 절대 변수명으로 쓰면 안되는 이유,

*global에서 써버리면 built-in 에 써버리면 아래와 같이 오류가 생김*

```

# [2] 내장(Built-in) 이름을 덮어쓰는 실수
# - sum은 원래 내장 함수인데, 변수명으로 써버리면 함수가 사라짐
# - 이후 sum(...)을 호출하면 '정수를 호출하려 한다'는 TypeError
# - 실무에서도 자주 나오는 실수: list, str, id, type, max 등에 주의
# =============================================================

# 내장 함수 sum의 이름을 사용해버려서 오류가 발생하는 예시
print(sum)  # <built-in function sum>
print(sum(range(3)))  # 3
sum = 5
print(sum)  # 5
print(sum(range(3)))  # TypeError: 'int' object is not callable


```

## LEGB 퀴즈

```
 =============================================================
# [3] LEGB Rule 퀴즈
# - 파이썬이 이름을 찾는 순서
#   L(Local 지역) => E(Enclosing 감싸는 함수) => G(Global 전역) => B(Built-in 내장)
#
# [풀이 힌트]
#  inner_func(y) 의 y는 '매개변수' => Local
#  x는 inner_func 안에 없으므로 Enclosing(outer_func)의 'E'
#  안쪽에서 값을 바꾼 것이 아니므로 바깥 x, y는 그대로 유지됨
# =============================================================

# LEGB Rule 퀴즈
x = 'G'
y = 'G'


def outer_func():
    x = 'E'
    y = 'E'

    def inner_func(y):
        z = 'L'
        print(x, y, z)  # E P L

    inner_func('P')
    print(x, y)  # E E


outer_func()
print(x, y)  # G G


```

inner_func은 inner_func이 호출될 때 실행됨. 
호출 된 영역에 () 내부에 있는 요소가 존재하는지, 존재해야 출력이 됨. 


!<풀이예제>( img width="424" height="424" alt="image" src="https://github.com/user-attachments/assets/eca977f1-7512-4cda-9e8b-c0449b80585a" / )



## 함수이름 구성 요소

1) 이름만으로 무엇을 하는지 명확하게 표현하기
3) T/F를 반환한다면 is 또는 has 로 시작하는 것을 추언
4) 프로젝트 전체에서 일관성을 지키는 것이 가독성에 도움을 줌

## 책임분할

1) 한개의 함수에 하나씩 책임이 있어야 하므로 제미나이 등에게
내가 생성한 함수를 책임을 하나씩 가진 함수로 분리해 줄 수 있어?
라고 부탁하는 것도 가능함. 

```
# =============================================================
# [3] 좋은 설계 - 하나의 함수는 하나의 일만 (단일 책임)
# - 각 함수가 작아져서 이름만 봐도 역할이 분명해짐
# - 개별 재사용/테스트가 가능해지고, 수정 범위가 좁아짐
# - 각 함수의 docstring이 곧 그 함수의 책임 정의가 됨
# =============================================================

# 올바른 설계 예시 (책임을 분리한 함수들)
def validate_password(password):
    """비밀번호 유효성 검사"""
    if len(password) < 8:
        raise ValueError('비밀번호는 8자 이상이어야 합니다')


def save_user(user_data):
    """비밀번호 암호화 및 저장"""
    user_data['password'] = hash_password(user_data['password'])
    db.users.insert(user_data)


def send_welcome_email(email):
    """환영 이메일 발송"""
    send_email(email, '가입을 환영합니다!')

```


## 반환(함수는 단 하나의 객체만 반환한다)


```

# =============================================================
# [심화] return은 항상 '단 하나의 값'만 반환한다
# - 쉼표로 여러 값을 적으면 여러 개를 반환하는 것처럼 보이지만,
#   실제로는 자동으로 튜플로 '패킹'되어 하나의 값이 됨
# - 받는 쪽에서 name, age = get_user_info() 처럼 쓰면
#   반대로 '언패킹'되어 각각의 변수에 담김
# =============================================================

def get_user_info():
    name = 'Alice'
    age = 30
    # 콤마(,)로 여러 값을 반환하는 것처럼 보임
    return name, age


# 하지만 반환된 값을 user_data변수에 담아 확인해보면
user_data = get_user_info()

# 단 하나의 튜플을 반환하는 것 입니다.
print(user_data)  # ('Alice', 30)

```


## 람다 표현식(이름이 없는 익명함수를 만드는 것)


1) 이름을 없앤다는 것은 1회용으로 사용하겠다는 의미.
2) sorted 내장 함수

```
# 1. lambda 미사용
# 정렬 기준 함수를 굳이 정의해야 함
def get_age(student):
    return student[1]


# sorted 함수의 key 매개변수에 우리가 만든 get_age 함수를 전달
result = sorted(students, key=get_age)
print(result)  # [('서준', 20), ('지민', 25), ('민우', 30)]


# =============================================================
# [2] lambda 사용 - 한 번만 쓸 함수를 즉석에서 전달
# - 결과는 [1]번과 완전히 동일하지만 코드가 훨씬 간결해짐
# =============================================================

# 2. lambda 사용
"""
get_age처럼 간단하고 한 번만 쓸 함수를 굳이 따로 정의할 필요 없이, lambda로 즉석에서 만들어 전달할 수 있습니다.
key=lambda student: student[1]
-> "정렬할 때 각 데이터를 student라고 부를게."
-> "그리고 그 데이터의 1번 인덱스 값(나이)을 기준으로 삼아줘."
"""
result = sorted(students, key=lambda student: student[1])
print(result)  # [('서준', 20), ('지민', 25), ('민우', 30)]
```


### lpmbda 변경 예시

```
# 람다 표현식 적용 전
def addition(x, y):
    return x + y


# 람다 표현식 적용 후
# def , addition 없어지고 lambda
lambda x, y: x + y

```
