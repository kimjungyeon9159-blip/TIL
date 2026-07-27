## 실습예제



```
class Myth:
    type_of_myth = 0  # 클래스 변수: 생성된 신화 인스턴스 수

    def __init__(self, name):
        self.name = name  # 인스턴스 속성: 신화의 이름
        Myth.type_of_myth += 1  # 인스턴스 생성될 때마다 1씩 증가

    @staticmethod
    def description():  # 정적 메서드: 신화에 대한 설명 출력
        print('신화는 예로부터 전해 내려오는 신비한 이야기입니다.')


myth1 = Myth("dangun")
myth2 = Myth("greek & rome")

print(myth1.name)
print(myth2.name)
print(Myth.type_of_myth)
Myth.description()

```

#### 주의점

1) **Myth.type_of_myth += 1  # 인스턴스 생성될 때마다 1씩 증가** 은 self.name = name 과 같은 들여쓰기로 적어야함.
2) 인스턴스 매서드와 스태틱 매서드 차이
```
   인스턴스 메서드와 스태틱 메서드, 비유로 정리해볼게요.

인스턴스 메서드 — "이 사람"에 대한 행동

python
class Person:
    def __init__(self, name):
        self.name = name

    def introduce(self):  # self가 있음
        print(f'저는 {self.name}입니다.')

p1 = Person("Alice")
p1.introduce()  # "저는 Alice입니다."

첫 번째 매개변수가 항상 self — "지금 이 인스턴스"를 가리킵니다.
p1.introduce()라고 부르면 파이썬이 자동으로 p1을 self 자리에 넣어줍니다.
누구(어떤 인스턴스)의 데이터를 쓸지가 중요할 때 씁니다. self.name처럼 인스턴스마다 다른 값에 접근해야 하니까요.

스태틱 메서드 — 클래스와 관련은 있지만 "이 사람" 없이도 되는 행동

python
class Person:
    @staticmethod
    def greeting():  # self 없음
        print('안녕하세요!')

Person.greeting()  # 인스턴스 안 만들어도 바로 호출 가능
p1 = Person("Alice")
p1.greeting() # 이것도 가능하지만, self는 안 씀

self도 cls도 받지 않습니다. 그냥 클래스 안에 있는 "일반 함수"라고 봐도 됩니다.
인스턴스의 개별 데이터(self.name 같은 것)를 쓸 필요가 없을 때 씁니다.

[한 줄 구분법] 

self.name처럼 **"이 인스턴스만의 값"**을 다뤄야 한다 → 인스턴스 메서드
인스턴스랑 상관없이 누가 불러도 똑같이 동작한다 → 스태틱 메서드 (예: 단위 변환, 설명 출력, 유효성 검사)
```
3) **print(Myth.type_of_myth)** 과 **Myth.description()** 에 대한 추가 설명

##### print(Myth.type_of_myth)

type_of_myth는 클래스 변수라서 myth1이나 myth2 같은 특정 인스턴스에 속한 게 아니라 Myth 클래스 자체에 붙어있습니다.
__init__이 호출될 때마다 Myth.type_of_myth += 1이 실행됐으니, 지금까지 myth1, myth2 두 개를 만들었다면 이 시점엔 2가 출력됩니다.
myth1.type_of_myth로 접근해도 값은 똑같이 나오지만(인스턴스에서 클래스 변수를 조회하는 건 허용되니까), 이 값이 인스턴스 개별 값이 아니라 클래스 전체가 공유하는 값이라는 걸 명확히 하려고 Myth.type_of_myth로 쓴 겁니다.

##### Myth.description()

description은 @staticmethod로 정의됐기 때문에 self도 cls도 받지 않습니다.
그래서 myth1.description()처럼 인스턴스를 통해 불러도 되고, Myth.description()처럼 클래스 이름으로 바로 불러도 됩니다 — 둘 다 동일하게 동작해요.
여기선 인스턴스와 무관한 공통 설명이라 Myth.description()으로 호출한 겁니다.
