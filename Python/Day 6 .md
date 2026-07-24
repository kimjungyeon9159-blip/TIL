
## 실습예제1




```
data = [
    {
        'name': 'galxy flip',
        'company': 'samsung',
        'is_collapsible': True,
    },
    {
        'name': 'ipad',
        'is_collapsible': False
    },
    {
        'name': 'galxy fold',
        'company': 'samsung',
        'is_collapsible': True
    },
    {
        'name': 'galxy note',
        'company': 'samsung',
        'is_collapsible': False
    },
    {
        'name': 'optimus',
        'is_collapsible': False
    },
]

key_list = ['name', 'company', 'is_collapsible']

# 아래에 코드를 작성하시오.
for item in data:
    for key in key_list:
        value = item.setdefault(key, 'unknown')  # key가 없으면 'unknown'을 추가하고 반환
        print(f'{key}은/는 {value}입니다.')
    print()  # dict 사이 구분을 위한 빈 줄

```



## 출력결과


$ python ws_6_c.py 
name은/는 galxy flip입니다.
company은/는 samsung입니다.
is_collapsible은/는 True입니다.

name은/는 ipad입니다.
company은/는 unknown입니다.
is_collapsible은/는 False입니다.

name은/는 galxy fold입니다.
company은/는 samsung입니다.
is_collapsible은/는 True입니다.

name은/는 galxy note입니다.
company은/는 samsung입니다.
is_collapsible은/는 False입니다.

name은/는 optimus입니다.
company은/는 unknown입니다.
is_collapsible은/는 False입니다.


##### 주의점

1)**D.setdefault(k,v)** 의 의미는 딕셔너리 D에서 키 k와 연결된 값을 반환. k가 D의 키가 아니면 값 v와 연결한 키 k를 D에 추가하고 v를 반환.
따라서, **value = item.setdefault(key, 'unknown')**  # key가 없으면 'unknown'을 추가하고 반환
2)dict사이 구분을 위한 빈 줄을 출력 결과에 내기 위해서는  **print()** 쓰기

