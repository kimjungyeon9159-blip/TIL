## 실습예제

### 과제(2)

```
class UserInfo:
    def __init__(self):
        self.user_data = {}

    def get_user_info(self):
        """
        사용자로부터 이름과 나이를 입력받습니다.
        - 이름이 없거나 공백이면 None을 반환합니다.
        - 나이가 숫자가 아니거나 입력되지 않으면 ValueError를 처리하고 False를 반환합니다.
        - 올바르게 입력되면 사용자 정보를 저장하고 True를 반환합니다.
        """
        # TODO: 아래 코드를 문제 요구사항에 맞게 완성하세요.
        name = input('이름을 입력하세요: ')
        if not name.strip():
            return None

        age_input = input('나이를 입력하세요: ')
        try:
            age = int(age_input)
        except ValueError:
            print('나이는 숫자로 입력해야 합니다.')
            return False

        self.user_data['name'] = name
        self.user_data['age'] = age
        return True

    def display_user_info(self):
        """
        저장된 사용자 정보를 출력합니다.
        - 정보가 없으면 "사용자 정보가 입력되지 않았습니다."를 출력합니다.
        """
        # TODO: 아래 코드를 문제 요구사항에 맞게 완성하세요.
        if not self.user_data:
            print('사용자 정보가 입력되지 않았습니다.')
        else:
            print('사용자 정보:')
            print(f'이름: {self.user_data["name"]}')
            print(f'나이: {self.user_data["age"]}')

            


# 아래 코드는 수정하지 마세요.
user = UserInfo()
result = user.get_user_info()

if result is True:
    user.display_user_info()
elif result is None:
    # 이름이 입력되지 않은 경우, display_user_info()가 적절한 메시지를 출력해야 합니다.
    user.display_user_info()
# 나이가 잘못 입력된 경우 (result is False), get_user_info()에서 이미 메시지를 출력했으므로
# 추가적인 동작이 필요 없습니다.

```


### 출력결과


$ python hw_8_4.py 

이름을 입력하세요: 기미

나이를 입력하세요: 15

사용자 정보:

이름: 기미

나이: 15


$ python hw_8_4.py 

이름을 입력하세요: 기미

나이를 입력하세요: 

나이는 숫자로 입력해야 합니다.


$ python hw_8_4.py 

이름을 입력하세요: 

사용자 정보가 입력되지 않았습니다.




### 실습 (3)


```

# 아래 클래스를 수정하시오.
class Animal:
    num_of_animal = 0  # 클래스 속성: 전체 동물 수

    def __init__(self):
        Animal.num_of_animal += 1  # 인스턴스 생성될 때마다 증가
        # 부모의 __init__이 Animal.num_of_animal += 1을 하고 있으니, 
        # 자식이 이걸 호출하면 자연스럽게 전광판이 올라갑니다.

class Dog(Animal):
    def __init__(self):
        super().__init__()  # Animal의 __init__ 호출 -> num_of_animal 증가
        # super().__init__()은 "나(Dog)는 태어났을 때 할 일을 부모(Animal)한테 맡길게"라는 뜻이에요

    def bark(self):
        print('멍멍')


class Cat(Animal):
    def __init__(self):
        super().__init__()  # Animal의 __init__ 호출 -> num_of_animal 증가

    def meow(self):
        print('야옹')

class Pet(Dog, Cat):  # Dog, Cat을 다중 상속
    # Pet은 직접 세지 않고 본사(Animal)에 있는 전광판 숫자를 그대로 읽어서 알려주는 역할 
    @classmethod
    # @classmethod는 "이 안내는 특정 강아지나 고양이 한 마리에 대한 질문이 아니라,
    # 클래스 차원의 질문이다"라는 표시
    # 그래서 인스턴스(pet = Pet())를 안 만들어도 
    # Pet.access_num_of_animal()처럼 바로 물어볼 수 있습니다.
    def access_num_of_animal(cls):
        return Animal.num_of_animal  # 공유되는 클래스 속성 반환


*# dog = Dog()*
*# print(f'동물의 수는 {Pet.access_num_of_animal()}마리입니다.')*
*# cat = Cat()*
*# print(f'동물의 수는 {Pet.access_num_of_animal()}마리입니다.')*


pet = Pet()
pet.bark()  # Dog한테서 물려받은 기능
pet.meow()  # Cat한테서 물려받은 기능
print(Pet.access_num_of_animal())




# Pet(Dog, Cat)이 둘 다 상속받고 있어서, bark()와 meow() 둘 다 호출 가능합니다.
# 만약 Pet(Animal)처럼 Animal만 상속받았다면 pet.bark()나 pet.meow()는 AttributeError가 났을 거예요 — Animal에는 그 메서드들이 없으니까요.

# 실행해보시면 "멍멍", "야옹", 그리고 access_num_of_animal() 결과(1)까지 순서대로 출력될 겁니다. 직접 돌려서 확인해보시겠어요?


````

### 출력결과 

 python ws_8_1.py 
멍멍
야옹
1




