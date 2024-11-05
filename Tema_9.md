# Тема 9. Базовые операции языка Python
Отчет по Теме #9 выполнил:
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
class Tolya:
    __slots__ = ['name']

    def __init__(self, name):
        if name == 'Tolya':
            self.name = f"I am {name}"
        else:
            self.name = f"I'm not {name}"

person1 = Tolya('Kolya')
person2 = Tolya('Tolya')
print(person1.name)
print(person2.name)
```
  ### Результат
  
![image](https://github.com/user-attachments/assets/e46336be-a2d6-4d25-b2b1-44bf535e300e)


## Лабараторная работа 2

 ```python
class Icecream:
    def __init__(self, ingr=None):
        if isinstance(ingr, str):
            self.ingr = ingr
        else:
            self.ingr = None
    
    def comp(self):
        if self.ingr:
            print(f"Icecream with {self.ingr}")
        else:
            print('Reg ic')

ic=Icecream()
ic.comp()
ic = Icecream('Choco')
ic.comp()
ic= Icecream(5)
ic.comp()
```

### Результат

![image](https://github.com/user-attachments/assets/1bc2aa9f-20ee-412b-8aa8-4d598296fbb9)


## Лабараторная работа 3

 ```python
class MC:
    def __init__(self, val):
        self._val = val
    def set_val(self, val):
        self._val = val
    def get_val(self):
        return self._val
    def del_val(self):
        del self._val
    val = property(get_val, set_val, del_val, "123")

obj = MC(42)
print(obj.get_val())
obj.set_val(45)
print(obj.get_val())
obj.set_val(100)
print(obj.get_val())
obj.del_val()
print(obj.get_val())
```
### Результат

![image](https://github.com/user-attachments/assets/1c66aaf5-9174-4c5e-8c4b-b5acf2d7a2a0)


## Лабараторная работа 4

 ```python
class Mam:
    className = 'Mam'

class Dog(Mam):
    spec = 'canine'
    s='wow'

class Cat(Mam):
    spec = 'feline'
    s='meow'

dog = Dog()
print(f"Dog is {dog.className}, but they say {dog.s}")
cat = Cat()
print(f"Cat is {cat.className}, but they say {cat.s}")
```
### Результат

![image](https://github.com/user-attachments/assets/be91a2ad-83f3-4b59-80a2-3d20ba995946)


## Лабараторная работа 5

 ```python
class rus:
    @staticmethod
    def greeting():
        print("Хэй")

class eng:
    @staticmethod
    def greeting():
        print("Hey")

def greet(lang):
    lang.greeting()

tolya = rus()
greet(tolya)
notrus = eng()
greet(notrus)
```
### Результат

![image](https://github.com/user-attachments/assets/44fac0f2-f653-4b3f-889c-10fb9f458db1)



# Самостоятельные работы

## Самостоятельная работа №1

 ```python
class Tomato:
    
    states = {'Отсутствует': 0, 'Цветение': 1, 'Зеленый': 2, 'Красный': 3}
    
    def __init__(self, index):
        self._index = index
        self._state = self.states['Отсутствует']
        
    def grow(self):
        if self._state < 3:
            self._state += 1
        
    def is_ripe(self):
        return True if self._state == 3 else False
 
class TomatoBush:
    
    def __init__(self, num):
        self.tomatoes = [Tomato(index) for index in range(1, num+1)]
        
    def grow_all(self):
        for tomato in self.tomatoes:
            tomato.grow()
            
    def all_are_ripe(self):
        return all([tomato.is_ripe() for tomato in self.tomatoes])
    
    def give_away_all(self):
        self.tomatoes = []
 
class Gardener:
    
    def __init__(self, name, plant):
        self.name = name
        self._plant = plant
        
    def work(self):
        self._plant.grow_all()
        
    def harvest(self):
        if self._plant.all_are_ripe():
            print('Урожай собран!')
            self._plant.give_away_all()
        else:
            print('Томаты еще не дозрели')
            
    @staticmethod
    def knowledge_base():
        print('Справка по садоводству:')
        print('1. Не забывайте регулярно поливать и подкармливать растения')
        print('2. Определите правильное расстояние между растениями, чтобы они не мешали друг другу в росте')
        print('3. Удалите поврежденные листья и плоды, чтобы предотвратить распространение болезней')
        
Gardener.knowledge_base()
 
bush = TomatoBush(5)
gardener = Gardener('John', bush)
 
gardener.work()
gardener.work()
gardener.work()
 

gardener.harvest()
 
gardener.work()
gardener.harvest()
gardener.work()
gardener.harvest()
gardener.work()
gardener.harvest()

gardener.work()
gardener.harvest()
```

### Результат

![image](https://github.com/user-attachments/assets/4f00b0ee-05fd-4b6e-afe2-397cb1f56390)


## Краткий вывод:
В результате выполнения программы, садовод по имени Джон ухаживает за куста с пятью томатами, которые, после нескольких вызовов методов роста, проверяются на зрелость. Если все томаты созрели, садовод может собрать урожай, при этом выводится соответствующее сообщение. 


# Общий вывод 

Операторы, условия, циклы играют важнейшую роль в языке программирования Python, обеспечивая гибкость и эффективность в обработке данных и создании программ. Вот что стоит отметить:

Использование условных операторов:
Python предоставляет условные операторы (например, if, elif, else), которые позволяют программе принимать решения на основе заданных условий.

Циклы:
Язык Python поддерживает циклы for и while, которые позволяют многократно выполнять блоки кода. Это полезно для обработки данных в массивах, списках и других структурах данных.

Операторы, условия и циклы в Python предоставляют мощные инструменты для создания программ и решения разнообразных задач. Эти базовые знания являются фундаментом для разработки сложных программ и эффективной работы с данными.
