## 실습예제


### (과제1)


##### 문제

주어진 문자열에서 특정 문자의 개수를 세는 count_character 함수를 작성하시오. 

문자열과 대상 문자를 인자로 받아 개수를 반환해야 한다.

##### 실행결과
				
2




```

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


   

### (과제 2)



##### 문제


주어진 리스트에서 최솟값과 최댓값을 찾는 find_min_max 함수를 작성하시오.

리스트를 인자로 받아 최솟값과 최댓값을 튜플로 반환해야 한다.


##### 실행결과

(1,7)





*두가지 풀이가 있음 , 메서드를 사용하는 것과 안하는 것*




<메서드를 사용하는 것>

```


def find_min_max(box):
    """주어진 리스트에서 최솟값과 최댓값을 찾아 반환하는 함수입니다.
    >>>find_min_max([1,2,3])
    (1,3)"""
    box.sort()
    return (box[0], box[-1])


result = find_min_max([3, 1, 7, 2, 5])
print(result)  # (1, 7)

```


<메서드를 사용하지 않는 것>


```


def find_min_max(box):
    """주어진 리스트에서 최솟값과 최댓값을 찾아 반환하는 함수입니다.
    >>>find_min_max([1,2,3])
    (1,3)"""

	return (min(box), max(box))


result = find_min_max([3, 1, 7, 2, 5])
print(result)  # (1, 7)


```



