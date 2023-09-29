# "Поколение Python": курс для продвинутых
## 12 Модули random и string
### Орел или Решка
Напишите программу, которая с помощью модуля random моделирует броски монеты. Программа принимает на вход количество попыток и выводит результаты бросков: Орел или Решка (каждое на отдельной строке).
```sh
import random

n = int(input())  # количество попыток

for i in range(n):
    num = random.random()
    if num > 0.5:
        print('Орел')
    else:
        print('Решка')
```
### Кубик
Напишите программу, которая с помощью модуля random моделирует броски игрального кубика c 6 гранями. Программа принимает на вход количество попыток и выводит результаты бросков — выпавшее число, которое написано на грани кубика (каждое на отдельной строке).
```sh
import random

n = int(input())  # количество попыток

for i in range(n):
    num = random.randint(1, 6)
    print(num)
```
### Случайный пароль
Напишите программу, которая с помощью модуля random генерирует случайный пароль. Программа принимает на вход длину пароля и выводит случайный пароль, содержащий только символы английского алфавита a..z, A..Z (в нижнем и верхнем регистре).
```sh
from random import randint

password = ''

for i in range(int(input())):
    num = randint(0, 1)
    if num == 0:
        letter = randint(65, 90)
    elif num == 1:
        letter = randint(97, 122)
    password += chr(letter)

print(password)
```
### Лотерейный билет
Лотерейный билет содержит 7 чисел из диапазона от 1 до 49 (включительно).
Напишите программу, которая с помощью модуля random генерирует 7 различных случайных чисел для лотерейного билета. Программа должна вывести числа в порядке возрастания на одной строке через один символ пробела.
```sh
import random

ans = set()
while len(ans) != 7:
    ans.add(random.randrange(1, 50))
print(*sorted(ans))
```
### IP адрес 
IP адрес состоит из четырех чисел из диапазона от 0 до 255 (включительно) разделенных точкой.
Напишите функцию generate_ip(), которая с помощью модуля random  генерирует и возвращает случайный корректный IP адрес.
```sh
from random import randint

def generate_ip():
    ip = [str(randint(0, 255)) for i in range(4)]
    ip = '.'.join(ip)
    return ip
```
### Почтовый индекс
Почтовый индекс в Латверии имеет вид: LetterLetterNumber_NumberLetterLetter, где Letter – заглавная буква английского алфавита, Number – число от 0 до 99 (включительно).
Напишите функцию generate_index(), которая с помощью модуля random генерирует и возвращает случайный корректный почтовый индекс Латверии.
```sh
from random import randint

def letter():
    letter = chr(randint(65, 90))
    return letter


def number():
    number = str(randint(0, 99))
    return number


def generate_index():
    index = letter() + letter() + number() + '_' + number() + letter() + letter()
    return index

print(generate_index())
```
### Перемешанная матрица
Напишите программу, которая с помощью модуля random перемешивает случайным образом содержимое матрицы (двумерного списка).
```sh
from random import shuffle

matrix = [[1, 2, 3, 4],
          [5, 6, 7, 8],
          [9, 10, 11, 12],
          [13, 14, 15, 16]]

shuffle(matrix)
```
### Лотерейные билеты
Напишите программу, которая с помощью модуля random генерирует 100 случайных номеров лотерейных билетов и выводит их каждый на отдельной строке. Обратите внимание, вы должны придерживаться следующих условий:

- номер не может начинаться с нулей;
- номер лотерейного билета должен состоять из 7 цифр;
- все 100 лотерейных билетов должны быть различными.

```sh
from random import randint

numbers = set()
while len(numbers) < 100:
    numbers.add(randint(1000000, 9999999))

ticket = list(numbers)
for i in ticket:
    print(i)
```
### Анаграмма
Анаграмма – это слово образованное путём перестановки букв, составляющих другое слово.

Напишите программу, которая считывает одно слово и выводит с помощью модуля random его случайную анаграмму.
```sh
from random import shuffle

word = input()
letters = list(word)
shuffle(letters)

print(''.join(letters))
```
### Бинго
Напишите программу, которая с помощью модуля random генерирует и выводит случайную карточку для игры в бинго.
```sh
from random import sample

numbers = [i for i in range(1, 76)]   # создаем список из чисел от 1 до 75
bingo = sample(numbers, 24)           # выбираем 24 числа
matrix = [[0] * 5 for i in range(5)]  # создаем нулевую матрицу

# заполнение матрицы числами из списка bingo
number = 0
for i in range(5):
    for j in range(5):
        if i == j and i == 2:
            continue
        else:
            matrix[i][j] = bingo[number]
            number += 1

# вывод матрицы
for i in range(5):
    for j in range(5):
        print(str(matrix[i][j]).ljust(3), end=' ')
    print()
```
### Тайный друг 🌶️
Напишите программу, которая случайным образом назначает каждому ученику его тайного друга, который будет вместе с ним решать задачи по программированию.
```sh
from random import randrange

n = int(input())
names = [input() for i in range(n)]

friends = []
i = 0
while len(friends) < n:
    num = randrange(n)
    if num != i and names[num] not in friends:
        print(names[i], '-', names[num])
        friends.append(names[num])
        i += 1
```
### Генератор паролей 1
Напишите программу, которая с помощью модуля random генерирует n паролей длиной m символов, состоящих из строчных и прописных английских букв и цифр, кроме тех, которые легко перепутать между собой:
- «l» (L маленькое);
- «I» (i большое);
- «1» (цифра);
- «o» и «O» (маленькая и большая буквы);
- «0» (цифра).
```sh
from string import *
from random import randrange

symbols = ''.join((set(ascii_letters) | set(digits)) - set('lI1oO0'))

def generate_password(length):
    password = [symbols[randrange(len(symbols))] for i in range(length)]
    return ''.join(password)


def generate_passwords(count, length):
    for i in range(count):
        print(generate_password(length))
    pass


n, m = int(input()), int(input())

generate_passwords(n, m)
```
### Генератор паролей 2 🌶️
Напишите программу, которая с помощью модуля random генерирует n паролей длиной m символов, состоящих из строчных и прописных английских букв и цифр, кроме тех, которые легко перепутать между собой:
- «l» (L маленькое);
- «I» (i большое);
- «1» (цифра);
- «o» и «O» (маленькая и большая буквы);
- «0» (цифра).

Дополнительное условие: в каждом пароле обязательно должна присутствовать хотя бы одна цифра и как минимум по одной букве в верхнем и нижнем регистре.
```sh
from string import *
from random import randrange

symbols = ''.join((set(ascii_letters) | set(digits)) - set('lI1oO0'))


def generate_password(length):
    count = 0
    while count < 2:
        password = [symbols[randrange(len(symbols))] for i in range(length)]
        flag_numeric, flag_upper, flag_lower = False, False, False
        for i in range(length):
            if password[i].isnumeric() == True:
                flag_numeric = True
            if password[i].isupper() == True:
                flag_upper = True
            if password[i].islower() == True:
                flag_lower = True
        if flag_numeric * flag_upper * flag_lower == 1:
            count = 3
    return ''.join(password)


def generate_passwords(count, length):
    for i in range(count):
        print(generate_password(length))
    pass


n, m = int(input()), int(input())
generate_passwords(n, m)

```
### Монте-Карло 
Напишите программу, которая при помощи метода Монте-Карло вычисляет площадь фигуры.
```sh
from random import uniform

n = 10 ** 6  # количество испытаний
k = 0
s0 = 16
for _ in range(n):
    x = uniform(-2, 2)
    y = uniform(-2, 2)

    if x ** 3 + y ** 4 + 2 >= 0 and 3 * x + y ** 2 <= 2:
        k += 1

print((k / n) * s0)
```
### Число π
Напишите программу, которая при помощи метода Монте-Карло определяет приближённое значение числа π.
```sh
from random import uniform

n = 10 ** 6  # количество испытаний
k = 0
s0 = 4
for _ in range(n):
    x = uniform(-1, 1)
    y = uniform(-1, 1)

    if x ** 2 + y ** 2 <= 1:
        k += 1

print((k / n) * s0)
```