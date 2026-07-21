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



