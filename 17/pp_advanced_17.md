# "Поколение Python": курс для продвинутых
## 17 Работа с файлами
### Содержимое файла
На вход программе подается строка с именем текстового файла. Напишите программу, которая выводит на экран его содержимое.
```sh
file_name = input()

file = open(file_name,'r')

info = file.read()

file.close()

print(info)
```
### Предпоследняя строка
На вход программе подается строка с именем текстового файла. Напишите программу, которая выводит на экран его предпоследнюю строку.
```sh
file_name = input()

file = open(file_name, 'r')

info = file.readlines()

file.close()

print(info[-2])
```
### Случайная строка
Вам доступен текстовый файл lines.txt из нескольких строк. Напишите программу, которая выводит на экран случайную строку из этого файла.
```sh
from random import choice

file = open('lines.txt', 'r')
info = file.readlines()
file.close()

print(choice(info))
```
### Сумма двух-1
Вам доступен текстовый файл numbers.txt из двух строк, на каждой из них записано целое число. Напишите программу, выводящую на экран сумму этих чисел.
```sh
file = open('numbers.txt', 'r')
info = file.readlines()
file.close()

numbers = [int(info[i]) for i in range(len(info))]
print(sum(numbers))
```
### Сумма двух-2
Вам доступен текстовый файл nums.txt. В файле записано два целых числа, они могут быть разделены символами пробела и конца строки. Напишите программу, выводящую на экран сумму этих чисел.
```sh
file = open('nums.txt', 'r')
info = file.readlines()
file.close()

info = ''.join(info).split()
numbers = [int(info[i]) for i in range(len(info))]
print(sum(numbers))

```
### Общая стоимость
Вам доступен текстовый файл prices.txt с информацией о заказе из интернет магазина. В нем каждая строка с помощью символа табуляции (\t) разделена на три колонки:

- наименование товара;
- количество товара (целое число);
- цена (в рублях) товара за 1 шт (целое число).

Напишите программу, выводящую на экран общую стоимость заказа.
```sh
file = open('prices.txt', 'r')

cost = 0
for line in file:
    info = line.split('\t')
    cost += int(info[1]) * int(info[2])

print(cost)

file.close()
```
### Переворот строки
Вам доступен текстовый файл text.txt с одной строкой текста. Напишите программу, которая выводит на экран эту строку в обратном порядке.
```sh
with open('text.txt', encoding='utf-8') as file:
    info = file.read()[::-1]
    print(info)
```
### Обратный порядок
Вам доступен текстовый файл data.txt, в котором записаны строки текста. Напишите программу, выводящую все строки данного файла в обратном порядке: сначала последнюю, затем предпоследнюю и т.д.
```sh
with open('data.txt') as file:
    text = [line.strip() for line in file][::-1]
    print(*text, sep='\n')
```
### Длинные строки
Вам доступен текстовый файл lines.txt, в котором записаны строки текста. Напишите программу, которая выводит все строки наибольшей длины из файла, не меняя их порядок.
```sh
with open('lines.txt') as file:

    max_length = len(max(file.readlines(), key=len))
    file.seek(0)

    text = [line.strip() for line in file]

    for i in text:
        if len(i) == max_length - 1:
            print(i)
```
### Сумма чисел в строках
Напишите программу, которая вычисляет сумму чисел в каждой строке и выводит эту сумму на экран (для каждой строки выводится сумма чисел в этой строке).
```sh
with open('numbers.txt', 'r') as file:
    for stroka in file:
        line = map(int, stroka.split())
        print(sum(line))
```
### Сумма чисел в файле
Напишите программу, которая вычисляет сумму всех чисел, записанных в файле.
```sh
with open('nums.txt', 'r') as file:
    summa = 0
    for stroka in file:
        numbers = ''
        for elem in list(stroka):
            if elem.isdigit() == False:
                elem = ' '
                numbers += elem
            else:
                numbers += elem
        summa += sum(map(int, numbers.split()))

print(summa)
```
### Статистика по файлу
Вам доступен текстовый файл file.txt, набранный латиницей. Напишите программу, которая выводит количество букв латинского алфавита, слов и строк. Выведите три найденных числа в формате, приведенном в примере.
```sh
with open('file.txt', 'r') as file:
    count_lines = 0
    count_words = 0
    count_letters = 0
    for line in file:
        count_lines += 1
        count_words += len(line.split())
        for elem in line:
            if elem.isalpha():
                count_letters += 1

print(f'Input file contains:\n{count_letters}letters\n{count_words} words\n{count_lines} lines')
```
### Random name and surname
Напишите программу, которая c помощью модуля random создает 
3 случайные пары имя + фамилия, а затем выводит их, каждую на отдельной строке.
```sh
from random import choice

with open('first_names.txt', 'r') as f_names, open('last_names.txt', 'r') as f_surnames:
    names = [name.strip() for name in f_names]  # Имена
    surnames = [surname.strip() for surname in f_surnames]  # Фамилии

print(*[f'{choice(names)} {choice(surnames)}' for _ in range(3)], sep='\n')
```
### Необычные страны
Напишите программу выводящую все страны, название которых начинается с буквы 'G', численность населения которых больше чем
500000 человек, не меняя их порядок.
```sh
with open('population.txt', 'r') as file:
    for line in file:
        info = line.split()
        if info[0][0] == 'G' and int(info[-1]) > 500_000:
            print(info[0])
```
### CSV-файл
Вам доступен CSV-файл data.csv, содержащий информацию в csv формате. Напишите функцию read_csv для чтения данных из этого файла. Она должна возвращать список словарей, интерпретируя первую строку как имена ключей, а каждую последующую строку как значения этих ключей.
```sh
def read_csv():
    data = []
    with open('data.csv', 'r') as file:
        name = file.readline().strip().split(',')
        for line in file:
            info = line.strip().split(',')
            data.append(dict(zip(name, info)))
    return(data)
```
### Входная строка
Напишите программу, которая считывает строку текста и записывает её в текстовый файл output.txt.
```sh
with open('output.txt', 'w') as data:
    info = input()
    print(info, file=data)
```
### Случайные числа
Напишите программу, записывающую в текстовый файл random.txt 25 случайных чисел в диапазоне от 
111 до 777 (включительно), каждое с новой строки.
```sh
from random import randint

with open('random.txt', 'w') as file_data:
    for i in range(25):
        print(randint(111, 777), file=file_data)
```
### Нумерация строк
Вам доступен текстовый файл input.txt, состоящий из нескольких строк. Напишите программу для записи содержимого этого файла в файл output.txt в виде нумерованного списка, где перед каждой строкой стоит ее номер, символ ) и пробел. Нумерация строк должна начинаться с 1.
```sh
with open('input.txt', 'r') as input_file, open('output.txt', 'w') as out_file:
    for line in enumerate(input_file, 1):
        print(f'{line[0]}) {str(line[1]).strip()}', file=out_file)
```
### Подарок на новый год
Напишите программу для добавления 5 баллов к каждому результату теста и вывода фамилий и новых результатов тестов в файл new_scores.txt.
```sh
with open('class_scores.txt', 'r') as old_file, open('new_scores.txt', 'w') as new_file:
    for line in old_file:
        data = line.split()
        if int(str(data[1]).strip()) + 5 > 100:
            data[1] = 100
            print(f'{data[0]} {data[1]}', file=new_file)
        else:
            data[1] = int(str(data[1]).strip()) + 5
            print(f'{data[0]} {data[1]}', file=new_file)
```
### Загадка от Жака Фреско 🌶️
Напишите программу создания файла answer.txt и вывода в него списка козлов, которые удовлетворяют условию загадки от Жака Фреско.
```sh
with open('goats.txt', 'r') as info_data, open('answer.txt', 'w') as out_data:
    colours = []
    goats = []
    flag_colours = False
    flag_goats = False

    for line in info_data:
        if flag_goats:
            goats.append(line.strip())

        if line.strip() == 'GOATS':
            flag_colours = False
            flag_goats = True

        if flag_colours:
            colours.append(line.strip())

        if line.strip() == 'COLOURS':
            flag_colours = True

    amount_goats = len(goats)
    out = []
    for i in range(len(colours)):
        if round((goats.count(colours[i]) / amount_goats) * 100) > 7:
            out.append(colours[i])

    print(*sorted(out), file=out_data, sep='\n')
```
### Конкатенация файлов 🌶️
На вход программе подается натуральное число n и n строк с названиями файлов. Напишите программу, которая создает файл output.txt и выводит в него содержимое всех файлов, не меняя их порядка. Смотрите Примечание 2 для понимания работы программы.
```sh
list = []

n = int(input())

for i in range(n):
    with open(str(input()), 'r', encoding='UTF-8') as file:
        lines = file.readlines()
        list.extend(lines)

with open('output.txt', 'w', encoding='UTF-8') as output:
    output.writelines(list)
```
### Лог файл 🌶️
Напишите программу, которая создает файл output.txt и выводит в него имена всех пользователей (не меняя порядка следования), которые были в сети не менее часа.
```sh
with open('logfile.txt', 'r') as log, open('output.txt', 'w') as out:
    for line in log:
        info = line.strip().split(',')
        time_in = info[1].split(':')
        time_out = info[2].split(':')
        working_time = (int(time_out[0]) - int(time_in[0])) * 60 + (int(time_out[1]) - int(time_in[1]))
        if working_time >= 60:
            print(info[0], file=out)
```