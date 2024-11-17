# Тема 10. Декораторы и исключения
Отчет по Теме #10 выполнил:
- Зуб Никита Валерьевич
- ИВТ-22-1

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |


знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1
### Написать программу, которая будет считать числа Фибоначчи для 100 и запустить её без декоратора и с ним, посмотреть разницу во времени. При запуске без декоратора для наглядности хватит 10 секунд ожидания.

```python
from functools import lru_cache


@lru_cache(None)
def fib(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    return fib(n - 1) + fib(n - 2)


if __name__ == "__main__":
    print(fib(100))
```
### Результат.
![image](https://github.com/user-attachments/assets/15c059fd-7198-45ec-8ecf-ebe9bae7ec87)


## Лабораторная работа №2
### Написать декоратор для функции, который будет принимать все параметры и проверять, чтобы возраст был больше 0 и меньше 130.

```python
def check(input_func):
    def output_func(*args):
        name, age = (
            args[0],
            args[1],
        )

        if age < 0 or age > 130:
            age = "Wrong input"
        input_func(name, age)

    return output_func


@check
def personal_info(name, age):
    print(f"Name: {name} Age: {age}")


if __name__ == "__main__":
    personal_info("Tom", 52)
    personal_info("Rudy", -1)
    personal_info("Lora", 131, 0, 4, 5)
```
### Результат.
![image](https://github.com/user-attachments/assets/b69e6391-ce49-4ce9-8b5b-b174c37737ec)


## Лабораторная работа №3
### Написать исключения для функции, чтобы неподходящий тип данных не ломал код.

```python
def data(*args):
    try:
        for i in range(len(*args)):
            try:
                result = (args[0][i] * 15) // 10
                print(result)
            except Exception as ex:
                print(ex)
    except Exception as e:
        print(e)
    finally:
        print("Information has been processed")


if __name__ == "__main__":
    data([10, -1, "Grgr", "Monkey", "f", "low", 100])
```
### Результат.
![image](https://github.com/user-attachments/assets/0664789a-17fc-4d9d-96a6-10b5d8450245)


## Лабораторная работа №4
### Написать исключение, которое будет вызываться в случае, если в функцию проверки имени при регистрации передана строка длиннее десяти символов, а если имя имеет допустимую длину, то в консоль выводится "Успешная регистрация"

```python
class NegativeValueException(Exception):
    pass


def check_name(name):
    if len(name) > 10:
        raise NegativeValueException("Name is bigger than 10 simbols")
    else:
        print("Successful")


if __name__ == "__main__":
    name = "12345678910"
    check_name(name)
```
### Результат.
![image](https://github.com/user-attachments/assets/e0a62fec-82be-4679-ab24-fea80b623eba)


## Лабораторная работа №5
### Создать логгер, вывести все логи в консоль.

```python
class SiteChecker:
    def __init__(self, func):
        print("> Класс SiteChecker метод __init__: успешный запуск")
        self.func = func

    def __call__(self):
        print("> Проверка перед запуском", self.func.__name__)
        self.func()
        print("> Проверка безопасного включения")


@SiteChecker
def site():
    print("Усердная работа сайта")


if __name__ == "__main__":
    print(">> Сайт запущен")
    site()
    print(">> Сайт выключен")
```
### Результат.
![image](https://github.com/user-attachments/assets/a0f72660-06b0-470a-9d54-902436a614a4)


## Самостоятельная работа №1
### Написать декоратор для функции, который будет выяснять за какое время она выполняется.

```python
import time


def fib():
    fib1 = fib2 = 1

    for i in range(2, 200):
        fib1, fib2 = fib2, fib1 + fib2
        print(fib2, end=" ")


if __name__ == "__main__":
    a = time.time()
    fib()
    b = time.time()
    print(f"\nПрограмма выполнялась {int((b - a) * 1000)} миллисекунд")
```
### Результат.
![image](https://github.com/user-attachments/assets/5244c438-4456-4f1a-9968-c0de6ba38810)

## Выводы
Время выполнения установлено, программа работает правильно.

## Самостоятельная работа №2
### Написать код, который будет вызывать исключение, если файл пустой, и выводить информацию из файла, если нет.

```python
def check_file(name):
    try:
        f = open(name)

        f_str = f.readlines()
        f_str[0] = f_str[0]
        for i in f_str:
            print(i, end="\n")
    except:
        print("Файл пустой")


if __name__ == "__main__":
    check_file("input1.txt")
    check_file("input2.txt")
```
### Результат.
![image](https://github.com/user-attachments/assets/cd54f4e0-8c26-4967-8cc2-a5ce22f4c4ed)

## Выводы
Программа работает правильно.

## Самостоятельная работа №3
### Написать функцию, которая складывает 2 и введенное пользователем число, но если пользователь введет строку или другой неподходящий тип данных, то в консоль выведется ошибка.

```python
def func(x):
    try:
        print(2 + int(x))
    except ValueError:
        print("Неподходящий тип данных. Ожидалось число")


if __name__ == "__main__":
    func(input("Введите число: "))
```
### Результат.
![image](https://github.com/user-attachments/assets/2d1fc2d3-d05a-4b9a-8891-1a343eddfae4)


## Выводы
Тесты проведены, программа работает правильно.

## Самостоятельная работа №4
### Cоздать свою программу с использованием декоратора на двух функциях.

```python
def convert_to_data_type(data_type):
    def decorator(func):
        def wrapper(*args, **kwargs):
            result = func(*args, **kwargs)
            return data_type(result)

        return wrapper

    return decorator


@convert_to_data_type(int)
def add_numbers(x, y):
    return x + y


@convert_to_data_type(str)
def concatenate_strings(x, y):
    return x + y


result = add_numbers(100, 1)
print("Result:", result, type(result))

result = concatenate_strings("Sleepy", "Head")
print("Result:", result, type(result))
```
### Результат.
![image](https://github.com/user-attachments/assets/73dd5058-4963-4cbf-aa16-9a7de84d9298)

## Выводы
Программа суммирует входные данные, отображает результат и тип данных. Для вывода типа данных был применен декоратор.

## Самостоятельная работа №5
### Создать свою программу с использованием исключения.

```python
def divide(a, b):
    try:
        result = a / b
    except ZeroDivisionError as e:
        print("Ошибка деления на ноль:", e)
        return None
    else:
        return result


def read_file(filename):
    try:
        with open(filename, "r") as file:
            content = file.read()
    except FileNotFoundError as e:
        print(f"Файл {filename} не найден:", e)
        return ""
    else:
        return content


print(divide(101, 0))
print(read_file("nonexistent.txt"))
```
### Результат.
![image](https://github.com/user-attachments/assets/c7e4036e-e970-49fd-a22d-039a443c0be3)

## Выводы
Программа содержит две функции, для каждой из которых предусмотрено индивидуальное исключение: одно для деления на ноль, другое — для отсутствия файла. Исключения функционируют правильно.

## Общие выводы по теме
Изучили декораторы, применили их на практике и ознакомились со структурой и использованием исключений в Python.
