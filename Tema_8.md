# Тема 8
Отчет по Теме #8 выполнил:
- Зуб Никита Валерьевич
- ИВТ-22-1

| Задание | Лаб_раб | Сам_раб |
| - | - | - |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |


# Лабараторные работы 
   ## Лабараторная работа 1

  ```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model= model

my_car=Car("Save", "Me")
```
  ### Результат
  ![image](https://github.com/user-attachments/assets/b0a1c22f-f1e2-4835-b4ff-f95928f61249)

## Лабараторная работа 2
  
 ```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model= model

    def drive(self):
        print(f"Driving the {self.make} {self.model}")
my_car=Car("Save", "Me")
my_car.drive()
```

### Результат

![image](https://github.com/user-attachments/assets/fe31ffe3-a1cb-4d22-b7be-63c8badd8306)



## Лабараторная работа 3
  
 ```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model= model

    def drive(self):
        print(f"Driving the {self.make} {self.model}")

class ECar(Car):
    def __init__(self, make, model, bc):
        super().__init__(make, model)
        self.bc = bc

    def charge(self):
        print(f"Charging the {self.make} {self.model} with {self.bc} kWh")

my_Ecar=ECar("Tesla", "S", 75)
my_Ecar.drive()
my_Ecar.charge()
```
### Результат

![image](https://github.com/user-attachments/assets/1e588f8d-9ba9-47f3-8708-6b90a9fffbaf)


## Лабараторная работа 4

 ```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model= model

    def drive(self):
        print(f"Driving the {self.make} {self.model}")


my_car=Car("Tesla", "S")
print(my_car.make)
my_car.drive()
```
### Результат

![image](https://github.com/user-attachments/assets/dccd5f5c-846c-4a09-8f5d-d25d7efd2c30)



## Лабараторная работа 5

 ```python
class Shape:
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height
    
class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3,14*self.radius*self.radius
```
### Результат

![image](https://github.com/user-attachments/assets/0c5597d8-7dc2-41ac-88ab-be783a35ac48)




# Самостоятельные работы

## Самостоятельная работа №1

 ```python
class Mood:
    def __init__(self, food, sleep):
        self.food = food
        self.sleep= sleep

    def awail(self):
        print(f"I have {self.food} {self.sleep}")

my_mood=Mood("No food", "No sleep")
my_mood.awail()
```

### Результат

![image](https://github.com/user-attachments/assets/b93531d7-d8a3-4d8b-90a5-7db84963786b)



## Краткий вывод:
Класс представляет собой шаблон для создания объектов. Он устанавливает характеристики (атрибуты) и действия (методы) этих объектов.
## Самостоятельная работа №2

 ```python
class Mood:
    def __init__(self, food, sleep):
        self.food = food
        self.sleep= sleep

    def awail(self):
        print(f"I have {self.food} {self.sleep}")

my_mood=Mood("No food", "No sleep")
my_mood.awail()
```

### Результат

![image](https://github.com/user-attachments/assets/4c51e6d4-7c1b-4f15-8306-65a440ad9407)


## Краткий вывод:

Атрибуты в объектно-ориентированном программировании являются переменными, которые отражают состояние объекта и определяют его особенности.

## Самостоятельная работа №3

 ```python
class Mood:
    def __init__(self, food, sleep):
        self.food = food
        self.sleep= sleep

class EMood(Mood):
    def __init__(self, food, sleep, emoites):
        super().__init__(food, sleep)
        self.e = emoites

    def feel(self):
        print(f"I have {self.food} {self.sleep} and {self.e}")
my_mood=EMood("no food", "no sleep", "depression")
my_mood.feel()
```

### Результат

![image](https://github.com/user-attachments/assets/01ba0d2a-8727-4f77-b386-57727806637c)


## Краткий вывод:

Наследование дает возможность создавать новые классы, основываясь на уже существующих. Новый класс (подкласс) наследует атрибуты и методы своего родительского класса (суперкласса), что способствует повторному использованию кода и улучшению его организации.

## Самостоятельная работа №4

 ```python
class Mood:
    def __init__(self, food, sleep):
        self.food = food
        self.sleep= sleep

class EMood(Mood):
    def __init__(self, food, sleep, emoites):
        super().__init__(food, sleep)
        self.e = emoites

    def feel(self):
        print(f"I have {self.food} {self.sleep} and {self.e}")
my_mood=EMood("no food", "no sleep", "depression")
my_mood.feel()
```

### Результаты

![image](https://github.com/user-attachments/assets/e729b03c-01cd-4130-a65a-6e6f79552172)


## Краткий вывод:

Инкапсуляция обеспечивает скрытие внутренних аспектов реализации и защиту состояния объекта от несанкционированного доступа. Это достигается с использованием модификаторов доступа, таких как добавление одного или двух подчеркиваний перед именем атрибута.

## Самостоятельная работа №5

 ```python
class Mood:
    def __init__(self, food, sleep):
        self.food = food
        self.sleep= sleep

class EMood(Mood):
    def __init__(self, food, sleep, emoites):
        super().__init__(food, sleep)
        self.e = emoites

    def feel(self):
        print(f"I have {self.food} {self.sleep} and {self.e}")
my_mood=EMood("no food", "no sleep", "depression")
my_mood.feel()
```

### Результат

![image](https://github.com/user-attachments/assets/32ed235a-9b0d-4b04-9d2d-d75066c03142)



## Краткий вывод:
Полиморфизм позволяет взаимодействовать с объектами различных классов через общий интерфейс. Это означает, что один и тот же метод может функционировать по-разному в зависимости от объекта, инициирующего его вызов.

# Общий вывод 

Объектно-ориентированное программирование (ООП) — это парадигма, основанная на понятии "объектов", которые являются экземплярами классов. ООП помогает организовать код более структурировано, облегчая его переиспользование и сопровождение.
