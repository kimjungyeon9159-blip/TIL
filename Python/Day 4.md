### 실습예제(3일차 7번)

```
number_of_people = 0


def increase_user():
    global number_of_people
    number_of_people += 1



def create_user(name, age, address):

    print(f'{name}님 환영합니다!')
    increase_user()
    data = {}
    data['name'] = name
    data['age'] = age
    data['address'] = address
    return data

# 유저 5명이 map으로 처리될 때마다 각자 환영문구 +카운트 증가를 자동으로 이루어지게 하는 함수




name = ['김시습', '허균', '남영로', '임제', '박지원']
age = [20, 16, 52, 36, 60]
address = ['서울', '강릉', '조선', '나주', '한성부']



users=list(map(create_user, name, age, address))




print(users)


```


## 기초예제 100제 (https://codeup.kr/problemsetsol.php?psid=33)

1) 문자 중 ' 또는 " 만 출력하려면 각 문자 앞에 \ 를 붙이면 ( \', \") 가능.
```
print('\"!@#$%^&*()\'') #"!@#$%^&*()'
```
2) 파일명 입력할 때 \를 문자로 입력하려면 안전하게 \\를 적어주어야 \하나도 출력됨.
3) 
