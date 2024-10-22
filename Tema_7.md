# Тема 7. Работа с файлами
Отчет по Теме #7 выполнил:
- Зуб Никита Валерьевич
- ИВТ-22-1

| Задание | Лаб_раб | Сам_раб |
| - | - | - |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |
| Задание 6 | + |  |
| Задание 7 | + |  |
| Задание 8 | + |  |
| Задание 9 | + |  |
| Задание 10 | + |  |

# Лабараторные работы 
   ## Лабараторная работа 1
  ### Результат
  
![image](https://github.com/user-attachments/assets/10ef45a3-b923-4f12-bc28-b5efecf3b304)


## Лабараторная работа 2

 ```python
f = open("input.txt", "r")
print(f.readline())
f.close()

```

### Результат

![image](https://github.com/user-attachments/assets/6a35c3e3-eaa5-4445-aba0-7ad9d3d452f6)


## Лабараторная работа 3

 ```python
f = open("input.txt", "r")
print(f.readlines())
f.close()

```
### Результат

![image](https://github.com/user-attachments/assets/abeb28d5-a5a1-49e4-a34b-621bbb7f9e72)

## Лабараторная работа 4

 ```python
with open("input.txt") as f:
    print(f.readlines())

```
### Результат

![image](https://github.com/user-attachments/assets/69ccce09-741c-4a2d-aa49-9ad51adc9135)


## Лабараторная работа 5

 ```python
with open("input.txt") as f:
    print(f.read())

```
### Результат

![image](https://github.com/user-attachments/assets/c1b030d5-eb1c-4599-bc21-73362f6bcf6a)

## Лабораторная работа 6
 ```python
with open("input.txt", "a+") as f:
    f.write("\nLast")

with open("input.txt", "r") as f:
    result = f.readlines()
    print(result)

```
### Результат
![image](https://github.com/user-attachments/assets/dbb9f5ec-1be9-42c1-a8ca-601eab85bbe1)


## Лабораторная работа 7
 ```python
lines = ["one", "two", "three"]
with open("input.txt", "w") as f:
    for line in lines:
        f.write("Cycle run " + line + "\n")
    print("Done!")

```
### Результат
![image](https://github.com/user-attachments/assets/0c6789d7-b21f-4695-bbde-9118fb848079)
![image](https://github.com/user-attachments/assets/dbb9f5ec-1be9-42c1-a8ca-601eab85bbe1)


## Лабораторная работа 8
 ```python
import os


def print_docs(directory):
   all_files = os.walk(directory)
   for catalog in all_files:
       print(f"Papca {catalog[0]} contains: ")
       print(f"Directories: {', '.join([folder for folder in catalog[1]])}")
       print(f"Files: {', '.join(file for file in catalog[2])}")
       print("-"*40)

print_docs("C:/Users/user/Desktop/3курс/инженерия")

```
### Результат
![image](https://github.com/user-attachments/assets/d34ebe69-6f8d-4cc0-ac5d-d2f5f1b842bf)




## Лабораторная работа 9
 ```python
def longest_words(file):
    with open(file, encoding="utf-8") as f:
        words = f.read().split()
        max_lenght = len(max(words, key=len))
        for word in words:
            if len(word) == max_lenght:
                sought_words = word

        if len(sought_words) == 1:
            return sought_words[0]
        return sought_words


print(longest_words("input.txt"))

```
### Результат
![image](https://github.com/user-attachments/assets/4ac57d35-4471-4f24-b902-c0229a824c5f)



## Лабораторная работа 10
 ```python
import csv, datetime, time

with open("rows_300.csv", "w", encoding="utf-8", newline="") as f:
    writer = csv.writer(f)
    writer.writerow(["№", "Sec", "Microsec"])
    for line in range(1,301):
        writer.writerow([line, datetime.datetime.now().second,
                         datetime.datetime.now().microsecond])
        time.sleep(0.01)

```
### Результат
![image](https://github.com/user-attachments/assets/14760cce-01f0-453a-95ac-f2feeba6552b)



# Самостоятельные работы

## Самостоятельная работа №1

 ```python
import string

with open("input.txt", "r", encoding="utf-8") as f:
    file = f.readlines()

    deleted_words = list(string.punctuation)
    deleted_words.append("—")

    all_words = 0
    most_pop_dict = {}

    for line in file:
        line_words = line.split()

        for words in line_words:
            words = words.lower()

            if words not in deleted_words:

                for j in range(len(deleted_words)):
                    if deleted_words[j] in words:
                        words = words.replace(deleted_words[j], "")

                all_words += 1
                most_pop_dict[words] = most_pop_dict.get(words, 0) + 1

    most_pop_word = max(most_pop_dict, key=most_pop_dict.get)
    print(f"Самое популярное слово в тексте: '{most_pop_word}'. Оно встречается {most_pop_dict[most_pop_word]} раз/а.")
    print(all_words)

    f.close()

```
### Результат
![image](https://github.com/user-attachments/assets/8f14c627-7db2-400b-816a-3c88723e7a1d)
![image](https://github.com/user-attachments/assets/d3c07f30-4f59-4929-8821-4885d593045c)


## Краткий вывод:
В данной программе открывается текстовый файл, содержащий более 200 слов. Сначала создаётся список с символами, которые следует игнорировать при подсчёте (например, точки, запятые, двоеточия и т. д.). Затем формируется словарь, где ключами будут слова, а значениями — количество их вхождений в файле. 

Программа использует три вложенных цикла for. В первом из них происходит чтение строк из файла, и строки разбиваются на слова по пробелам. Далее эти слова переводятся в нижний регистр, чтобы обеспечить корректный подсчёт. Затем выполняется проверка: если слово содержит запрещённый символ, он удаляется (например, слово "да" и "да." считаются разными из-за точки в конце). Если слово не является запрещённым и не содержит изолированных символов, оно добавляется в словарь. Если слово уже существует в словаре, счётчик его вхождений увеличивается на единицу.

После обработки всех строк, программа находит слово с наибольшим количеством вхождений в словаре с помощью функции max и выводит результат в консоль.
## Самостоятельная работа №2

 ```python
def set_expenses(day: str, money: int):
    with open("input.txt", "r+") as file:
        lines = file.readlines()
        if int(lines[0]) < 0:
            print("У вас уже имеется долг, поэтому тратить больше нельзя!")
            return

        lines[0] = str(int(lines[0]) - money) + "\n"
        flag = False

        for i in range(len(lines)):
            if day in lines[i]:
                if i + 1 < len(lines):
                    lines[i + 1] = str(int(lines[i + 1]) + money) + "\n"
                else:
                    lines.append(str(money) + "\n")
                flag = True
                break

        if not flag:
            lines.append(day + "\n")
            lines.append(str(money) + "\n")

        if int(lines[0]) >= 0:
            print(f"Запись о тратах успешно добавлена! У вас осталось {lines[0].strip()} рублей!")
        else:
            print(f"Запись о тратах успешно добавлена! Сейчас у вас образовался долг в размере "
                  f"{lines[0].strip()} рублей!")

        file.seek(0)
        file.writelines(lines)
        file.truncate()

    question()


def get_expenses(day: str):
    with open("input.txt", "r") as file:
        lines = file.readlines()

        flag = False

        for i in range(len(lines)):
            if day in lines[i]:
                print(f"{lines[i].strip()} вы потратили {lines[i + 1].strip()} рублей.")
                print(f"У вас осталось {lines[0].strip()} рублей!")
                flag = True
                break

        if not flag:
            print("Записи для этого числа не создано, пожалуйста, создайте её!")

    question()


def question():
    user_say = input("Введите '+', если вы хотите добавить запись, "
                     "или '=', если вы хотите узнать траты за определённую дату: \n")
    if user_say == "+":
        user_say = input("Введите дату и количество денег, которые были потрачены в эту дату через пробел: \n")
        parts = user_say.split()
        day = parts[0] + " " + parts[1]
        money = int(parts[2])
        set_expenses(day, money)
    elif user_say == "=":
        day = input("Введите число за которое вы хотите узнать траты: \n")
        get_expenses(day)


if __name__ == '__main__':
    question()


```

### Результат
![image](https://github.com/user-attachments/assets/728f4d17-98d6-45e5-b09c-4cc533fd9e30)



## Краткий вывод:
  В программе реализуются две функции: первая для записи расходов, вторая для получения расходов за определённый день. Изначально имеется текстовый файл, в котором в первой строке указана сумма денег, доступная для расходов. При запуске программы пользователю предлагается выбрать, хочет ли он записать расходы или узнать информацию о них.

Если пользователь решает записать расходы, ему необходимо ввести дату в формате "день месяц" и сумму расходов. Затем вызывается первая функция, которая проверяет, есть ли запись за указанный день в файле. Если записи нет, она создаёт новую в конце файла в формате "дата" и "расходы", размещая их на двух подряд идущих строках. Если запись уже существует, новая сумма расходов добавляется к уже зарегистрированным, а из бюджета вычитается соответствующая сумма. В случае, если бюджет станет равным нулю или меньше, программа уведомит об этом и не позволит записать новые расходы.

Если пользователь выбирает получение информации о расходах, он должен указать дату. Если запись о расходах в этот день присутствует в файле, будет предоставлена справка о расходах за указанный день и оставшемся бюджете.
## Самостоятельная работа №3
 ```python
with open("input.txt", "r") as file:
    lines = file.readlines()

    summ_letters = 0
    summ_words = 0
    summ_lines = len(lines)
    for i in range(len(lines)):
        summ_words += len(lines[i].split())
        for k in range(len(lines[i])):
            if (lines[i][k] != ".") and (lines[i][k] != " ") and (lines[i][k] != "\n"):
                summ_letters += 1
    print(summ_letters)
    print(summ_words)
    print(summ_lines)

```

### Результат
![image](https://github.com/user-attachments/assets/f33fffd4-c2d3-4fa6-8fcf-b9e6ca22025a)


## Краткий вывод:
  В программе сначала открывается файл, после чего создаются переменные для подсчёта количества символов, слов и строк. Число строк определяется сразу, основываясь на длине списка, где каждая строка представлена отдельным элементом. 

Затем запускается цикл for, который осуществляет подсчёт слов путём разделения элементов исходного списка на отдельные слова. Далее идёт вложенный цикл, который подсчитывает количество символов при условии, что символ не является точкой, пробелом или символом новой строки. 

После завершения всех подсчётов информация о количестве символов, слов и строк выводится на консоль.

## Самостоятельная работа №4

 ```python
with open("input.txt", "r") as file:
    line = list(file.readline().split())

    input_str = ("Hello, world! Python IS the programming language of thE future. My EMAIL is...\n"
                 "PYTHON is awesome")
    index_next_line = input_str.index("\n")
    print(index_next_line)
    input_list = input_str.split()

    for i in range(len(input_list)):
        for k in range(len(line)):
            if line[k] in input_list[i].lower():
                for j in line[k]:
                    input_list[i] = input_list[i].lower().replace(j, "*")

    out_string = ""
    for i in input_list:
        out_string += i + " "
        if len(out_string) == index_next_line + 1:
            out_string += "\n"
    print(out_string)

```

### Результаты
![image](https://github.com/user-attachments/assets/b344977d-9991-43ee-92e4-1fd8f2d84d12)



## Краткий вывод:
  В программе происходит открытие файла, из которого формируется список запрещённых слов. Далее создаётся переменная для исходного текста, который затем преобразуется в список, разделяя слова по пробелам. После этого выполняется проверка, присутствует ли запрещённое слово в каждом из слов текста. Если такое слово найдено, то выполняется посимвольная замена символов исходного слова на '*', заменяя те символы, которые входят в состав запрещённого слова. В конце результаты выводятся на консоль.

## Самостоятельная работа №5

Напишите программу, которая удаляет определенное слово из файла.

 ```python
def remove_word_from_file(file_path, word_to_remove):
    try:
        with open(file_path, 'r', encoding='utf-8') as file:
            lines = file.readlines()
        updated_lines = [line.replace(word_to_remove, '') for line in lines]
        with open(file_path, 'w', encoding='utf-8') as file:
            file.writelines(updated_lines)

        print(f"Слово '{word_to_remove}' было удалено из файла '{file_path}'.")
    
    except FileNotFoundError:
        print(f"Файл '{file_path}' не найден.")
    except Exception as e:
        print(f"Произошла ошибка: {e}")

def main():
    file_path = 'input.txt'  
    word_to_remove = 'hello'  

    remove_word_from_file(file_path, word_to_remove)

if __name__ == "__main__":
    main()

```
### Результат

![image](https://github.com/user-attachments/assets/f442587b-636e-4008-8b01-723bc76fb3ab)
![image](https://github.com/user-attachments/assets/bf9498a4-551d-4d39-abc5-38ca41409d23)
![image](https://github.com/user-attachments/assets/c60dcf03-63d9-41b9-bf87-c433aa99fd89)


## Краткий вывод:
  Программа ищет выбранное слово в файле и при его наличии удаляет. 


# Общий вывод 

В Python для работы с файлами используется функция open(), которая позволяет открывать файлы для чтения или записи. Содержимое файлов можно извлекать с помощью метода read() или записывать, используя метод write(). Это предоставляет программам возможность взаимодействовать с файлами. 

Завершение работы с файлами важно для предотвращения утечек ресурсов, и для этого следует использовать метод close(). Python поддерживает текстовые и бинарные файлы, а также файлы, в которые можно добавлять данные. 

При работе с файлами могут возникать ошибки, поэтому рекомендуется использовать конструкции обработки исключений, такие как try и except, для повышения надежности кода.

Хорошее владение навыками работы с файлами не только помогает в управлении данными программ, но также повышает безопасность и устойчивость приложений.

