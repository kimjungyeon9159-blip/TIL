## 실습예제(과제1)

```
# 아래 함수를 수정하시오.
def count_character(sentence,char):
    """주어진 문자열에서 특정 문자의 개수를 세어 반환하는 함수입니다.
    >>> count_character(hello)
    1
    """
    return sentence.count(char)

result = count_character("Hello, World!", "o")
print(result)  # 2
```

### 주의점

1) return 작성 할 때 .count 앞에 함수 적용 대상인 객체를 적어 주어야한다
2) 매개변수를 작성할 때,  return에 적용할 객체와 반환값으로 필요한 객체 char을 모두 () 안에 작성하는 것으로 이해해보자

   
