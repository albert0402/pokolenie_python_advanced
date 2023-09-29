# "Поколение Python": курс для продвинутых
## 15  Функции
### matrix()
Напишите функцию matrix(), которая создает, заполняет и возвращает матрицу заданного размера.
```sh
def matrix(n=1, m=None, value=0):
    if m is None:
        m = n
    return(n * [m * [value]])
```
### count_args()
Напишите функцию count_args(), которая принимает произвольное количество аргументов и возвращает количество переданных в нее аргументов.
```sh
def count_args(*args):
    return len(args)
```
### sq_sum()
Напишите функцию sq_sum(), которая принимает произвольное количество числовых аргументов и возвращает сумму их квадратов.
```sh
def sq_sum(*args):
    return sum([i**2 for i in args])
```
### mean()
Напишите функцию mean(), которая принимает произвольное количество аргументов и возвращает среднее арифметическое переданных в нее числовых (int или float) аргументов.
```sh
def mean(*args):
    numbers = [i for i in args if type(i) is int or type(i) is float]
    if len(numbers) == 0:
        return 0.0
    else:
        return sum(numbers)/len(numbers)
```
### greet()
Напишите функцию greet(), которая принимает произвольное количество аргументов строк имен (как минимум одно) и возвращает приветствие в соответствии с образцом.
```sh
def greet(names, *args):
    s = 'Hello, ' + names
    name = [i for i in args]
    if len(name) > 0:
        for i in range(len(name)):
            if i == len(name):
                s += name[i]
            else:
                s += ' and '
                s += name[i]
    return s + '!'
```
### print_products()
Напишите функцию print_products(), которая принимает произвольное количество аргументов и выводит список продуктов (любая непустая строка) по образцу: <номер продукта>) <название продукта> (нумерация продуктов начинается с единицы). Если среди переданных аргументов нет ни одного продукта, необходимо вывести текст Нет продуктов.
```sh
def print_products(*args):
    count = 0
    for i in args:
        if type(i) is str and len(i) > 1:
            count += 1
            print(count, ') ', i, sep='')
    if count == 0:
        print('Нет продуктов')
```
### info_kwargs()
Напишите функцию info_kwargs(), которая принимает произвольное количество именованных аргументов и печатает именованные аргументы в соответствии с образцом: <имя аргумента>: <значение аргумента>, при этом имена аргументов следуют в алфавитном порядке (по возрастанию).
```sh
def info_kwargs(**kwargs):
    for key, value in sorted(kwargs.items()):
        print(key + ':', value)
```
### key 1
Дан список numbers, содержащий кортежи чисел. Напишите программу, которая с помощью встроенных функций min() и max() выводит те кортежи (каждый на отдельной строке), которые имеют минимальное и максимальное среднее арифметическое значение элементов.
```sh
def avg(numbers):
    return sum(numbers) / len(numbers)


numbers = [(10, 10, 10), (30, 45, 56), (81, 39), (1, 2, 3), (12,),
           (-2, -4, 100), (1, 2, 99), (89, 9, 34), (10, 20, 30, -2),
           (50, 40, 50), (34, 78, 65), (-5, 90, -1, -5),
           (1, 2, 3, 4, 5, 6), (-9, 8, 4), (90, 1, -45, -21)]

print(min(numbers, key=avg))
print(max(numbers, key=avg))
```
### key 2
Напишите программу, которая сортирует список points координат точек плоскости в соответствии с расстоянием от начала координат (точки 
(0;0). Программа должна вывести отсортированный список.
```sh
from math import sqrt, pow

def distance(points):
    x = points[0]
    y = points[1]
    return sqrt(pow(x, 2) + pow(y, 2))


points = [(-1, 1), (5, 6), (12, 0),
          (4, 3), (0, 1), (-3, 2),
          (0, 0), (-1, 3), (2, 0),
          (3, 0), (-9, 1), (3, 6), (8, 8)]

points = sorted(points, key=distance)
print(points)
```
### key 3
Дан список numbers, содержащий кортежи чисел. Напишите программу, которая сортирует и выводит список numbers в соответствии с суммой минимального и максимального элемента кортежа.
```sh
def min_max(number):
    mn = min(number)
    mx = max(number)
    return mn + mx


numbers = [(10, 10, 10), (30, 45, 56), (81, 80, 39),
           (1, 2, 3), (12, 45, 67), (-2, -4, 100),
           (1, 2, 99), (89, 90, 34), (10, 20, 30),
           (50, 40, 50), (34, 78, 65), (-5, 90, -1)]

numbers = sorted(numbers, key=min_max)
print(numbers)
```
### Сортируй как хочешь
Список athletes содержит сведения о спортсменах в виде кортежей: (имя, возраст, рост, вес).

Напишите программу сортировки списка спортсменов по указанному полю:
- 1: по имени;
- 2: по возрасту;
- 3: по росту;
- 4: по весу.
```sh
def name(athlete):
    return athlete[0]


def age(athlete):
    return athlete[1]


def height(athlete):
    return athlete[2]


def weight(athlete):
    return athlete[3]


sort = {1: name, 2: age, 3: height, 4: weight}

athletes = [('Дима', 10, 130, 35), ('Тимур', 11, 135, 39),
            ('Руслан', 9, 140, 33), ('Рустам', 10, 128, 30),
            ('Амир', 16, 170, 70), ('Рома', 16, 188, 100),
            ('Матвей', 17, 168, 68), ('Петя', 15, 190, 90)]

number = int(input())

for i in sorted(athletes, key=sort[number]):
    print(*i)
```
### Математические функции
Напишите программу, которая принимает число и название функции, а выводит результат применения функции к данному числу.
```sh
from numpy import sqrt, abs, sin

def power2(number):
    return pow(number, 2)


def power3(number):
    return pow(number, 3)


def koren(number):
    return sqrt(number)


def modul(number):
    return abs(number)


def sinus(number):
    return sin(number)


operation = {'квадрат': power2, 'куб': power3, 'корень': koren, 'модуль': modul, 'синус': sinus}

number = int(input())
func = input()

print(operation[func](number))
```
### Интересная сортировка-1
На вход программе подается строка натуральных чисел. Из элементов строки формируется список чисел.

Напишите программу сортировки списка чисел в порядке неубывания суммы их цифр. При этом, если два числа имеют одинаковую сумму цифр, следует сохранить их взаиморасположение в начальном списке.
```sh
def comparator(n):
    return sum([int(i) for i in str(n)])

numbers = [int(i) for i in input().split()]

print(*sorted(numbers, key=comparator))
```
### Интересная сортировка-2
На вход программе подается строка натуральных чисел. Из элементов строки формируется список чисел.

Напишите программу сортировки списка чисел в порядке неубывания суммы их цифр. При этом, если у двух чисел одинаковая сумма цифр, их следует вывести в порядке неубывания.
```sh
def comparator(n):
    return sum([int(i) for i in str(n)]), n


numbers = [int(i) for i in input().split()]

print(*sorted(numbers, key=comparator))
```
### map
Напишите программу, которая с помощью функции map() округляет все элементы списка numbers до 
2 десятичных знаков, а затем выводит их, каждый на отдельной строке.
```sh
def map(function, items):
    result = []
    for item in items:
        result.append(function(item))
    return result


def round2(number):
    return round(number, 2)


numbers = [3.56773, 5.57668, 4.00914, 56.24241,
           9.01344, 32.12013, 23.22222, 90.09873,
           45.45, 314.1528, 2.71828, 1.41546]

print(*map(round2, numbers), sep='\n')
```
### filter() и map()
Напишите программу, которая с помощью функций filter() и map() отбирает из заданного списка numbers трёхзначные числа, дающие при делении на 
5 остаток 2, и выводит их кубы, каждый в отдельной строке.
```sh
def map(function, items):
    result = []
    for item in items:
        result.append(function(item))
    return result


def filter(function, items):
    result = []
    for item in items:
        if function(item):
            result.append(item)
    return result


def move_with_numbers(number):
    if number // 1000 == 0 and number // 100 > 0 and number % 5 == 2:
        return number


def kube(number):
    return pow(number, 3)


numbers = [1014, 1321, 675, 1215, 56, 1386, 1385, 431, 1058, 486, 1434, 696, 1016, 1084, 424, 1189, 475, 95, 1434, 1462,
           815, 776, 657, 1225, 912, 537, 1478, 1176, 544, 488, 668, 944, 207, 266, 1309, 1027, 257, 1374, 1289, 1155,
           230, 866, 708, 144, 1434, 1163, 345, 394, 560, 338, 232, 182, 1438, 1127, 928, 1309, 98, 530, 1013, 898, 669,
           105, 130, 1363, 947, 72, 1278, 166, 904, 349, 831, 1207, 1496, 370, 725, 926, 175, 959, 1282, 336, 1268, 351,
           1439, 186, 273, 1008, 231, 138, 142, 433, 456, 1268, 1018, 1274, 387, 120, 340, 963, 832, 1127]

print(*map(kube, filter(move_with_numbers, numbers)), sep='\n')

```
### reduce() и map()
Напишите программу для вычисления и вывода суммы квадратов элементов списка numbers.
```sh
def reduce(operation, items, initial_value):
    acc = initial_value
    for item in items:
        acc = operation(acc, item)
    return acc

def map(function, items):
    result = []
    for item in items:
        result.append(function(item))
    return result

def power2(number):
    return number ** 2

def plus(number1, number2):
    return number1 + number2


numbers = [97, 42, 9, 32, 3, 45, 31, 77, -1, 11, -2, 75, 5, 51, 34, 28, 46, 1, -8, 84, 16, 51, 90, 56, 65, 90, 23, 35,
           11, -10, 70, 90, 90, 12, 96, 58, -8, -4, 91, 76, 94, 60, 72, 43, 4, -6, -5, 51, 58, 60, 30, 38, 67, 62, 36,
           72, 34, 82, 62, -1, 60, 82, 87, 81, -7, 57, 26, 36, 17, 43, 80, 40, 75, 94, 91, 64, 38, 72, 29, 84, 38, 35,
           7, 54, 31, 95, 78, 27, 82, 1, 64, 94, 31, 29, -8, 98, 24, 61, 7, 73]

numbers = map(power2, numbers)

print(reduce(plus, numbers, 0))

```
### filter(), map() и sum()
Напишите программу для вычисления и вывода суммы квадратов двузначных чисел, которые делятся на 
7 без остатка.
```sh
def map(function, items):
    result = []
    for item in items:
        result.append(function(item))
    return result


def filter(function, items):
    result = []
    for item in items:
        if function(item):
            result.append(item)
    return result


def power2(number):
    return pow(number, 2)


def abs_del7_two(number):
    number = abs(number)
    if number % 7 == 0 and 9 < number < 100:
        return number


numbers = [77, 293, 28, 242, 213, 285, 71, 286, 144, 276, 61, 298, 280, 214, 156, 227, 228, 51, -4, 202, 58, 99, 270,
           219, 94, 253, 53, 235, 9, 158, 49, 183, 166, 205, 183, 266, 180, 6, 279, 200, 208, 231, 178, 201, 260, -35,
           152, 115, 79, 284, 181, 92, 286, 98, 271, 259, 258, 196, -8, 43, 2, 128, 143, 43, 297, 229, 60, 254, -9, 5,
           187, 220, -8, 111, 285, 5, 263, 187, 192, -9, 268, -9, 23, 71, 135, 7, -161, 65, 135, 29, 148, 242, 33, 35,
           211, 5, 161, 46, 159, 23, 169, 23, 172, 184, -7, 228, 129, 274, 73, 197, 272, 54, 278, 26, 280, 13, 171, 2,
           79, -2, 183, 10, 236, 276, 4, 29, -10, 41, 269, 94, 279, 129, 39, 92, -63, 263, 219, 57, 18, 236, 291, 234,
           10, 250, 0, 64, 172, 216, 30, 15, 229, 205, 123, -105]

print(sum(map(power2, filter(abs_del7_two, numbers))))
```
### func_apply()
Напишите функцию func_apply(), принимающую на вход функцию и список значений и возвращающую список, в котором каждое значение будет результатом применения переданной функции к переданному списку.
```sh
def func_apply(func, numbers):
    result = []
    for i in numbers:
        result.append(func(i))
    return result
```
### lambda()
Написать программу, которая:
- преобразует список floats в список чисел, возведенных в квадрат и округленных с точностью до одного десятичного знака;
фильтрует список words  и оставляет только палиндромы длиной более 
4 символов;
- находит произведение чисел из списка numbers.
```sh
from functools import reduce

floats = [4.35, 6.09, 3.25, 9.77, 2.16, 8.88, 4.59, 34.23, 12.12, 4.67, 2.45, 9.32]
words = ['racecar', 'akinremi', 'deed', 'temidayo', 'omoseun', 'civic', 'TATTARRATTAT', 'malayalam', 'nun']
numbers = [4, 6, 9, 23, 5]

map_result = list(map(lambda num: round(num*num, 1), floats))
filter_result = list(filter(lambda name: len(name) > 4 and list(name) == list(name)[::-1], words))
reduce_result = reduce(lambda num1, num2: num1 * num2, numbers, 1)

print(map_result)
print(filter_result)
print(reduce_result)
```
### Большие города filter(), map(), sorted() и reduce()
Напишите программу, которая с помощью встроенных функций filter(), map(), sorted() и reduce() выводит в алфавитном порядке список primary городов с населением более
10000000 человек
```sh
from functools import reduce


def add(a, b):
    return b.append(a)


data = [['Tokyo', 35676000, 'primary'],
        ['New York', 19354922, 'nan'],
        ['Mexico City', 19028000, 'primary'],
        ['Mumbai', 18978000, 'admin'],
        ['Sao Paulo', 18845000, 'admin'],
        ['Delhi', 15926000, 'admin'],
        ['Shanghai', 14987000, 'admin'],
        ['Kolkata', 14787000, 'admin'],
        ['Los Angeles', 12815475, 'nan'],
        ['Dhaka', 12797394, 'primary'],
        ['Buenos Aires', 12795000, 'primary'],
        ['Karachi', 12130000, 'admin'],
        ['Cairo', 11893000, 'primary'],
        ['Rio de Janeiro', 11748000, 'admin'],
        ['Osaka', 11294000, 'admin'],
        ['Beijing', 11106000, 'primary'],
        ['Manila', 11100000, 'primary'],
        ['Moscow', 10452000, 'primary'],
        ['Istanbul', 10061000, 'admin'],
        ['Paris', 9904000, 'primary']]

new_data = list(filter(lambda x: x[1] > 10_000_000 and x[2] == 'primary', data))
n_d = sorted(new_data, key=lambda new_data: new_data[0])
out = reduce(lambda str, n_d: str + n_d[0] + ', ', n_d, 'Cities: ')

print(out[:-2])
```
### Деление
Напишите функцию func, используя синтаксис анонимных функций, которая принимает целочисленный аргумент и возвращает значение True, если он делится без остатка на 19 или на 13 и False в противном случае.
```sh
func = lambda number: True if number % 19 == 0 or number % 13 == 0 else False
```
### English
Напишите функцию func, используя синтаксис анонимных функций, которая принимает строковый аргумент и возвращает значение True, если переданный аргумент начинается и заканчивается на английскую букву a (регистр буквы неважен) и False в противном случае.
```sh
func = lambda str: str[0].lower() == 'a' and str[-1].lower() == 'a'
```
### is_non_negative_num
Напишите функцию is_non_negative_num, используя синтаксис анонимных функций, которая принимает строковый аргумент и возвращает значение True, если переданный аргумент является неотрицательным числом (целым или вещественным) и False в противном случае.
```sh
is_non_negative_num = lambda str: str.lower() == str.upper() and str[0] != '-' and str.count('.') <= 1
```
### is_num
Напишите функцию is_num, используя синтаксис анонимных функций, которая принимает строковый аргумент и возвращает значение True, если переданный аргумент является числом (целым или вещественным) и False в противном случае.
```sh
is_num = lambda str: str.lower() == str.upper() and str.count('.') <= 1 and '-' not in str[1:]
```
### filter() и sorted()
Напишите программу, которая с помощью встроенных функций filter() и sorted() выводит слова из списка words, имеющие длину ровно 6 символов. Слова следует вывести в алфавитном порядке на одной строке, разделив символом пробела.
```sh
words = ['beverage', 'monday', 'abroad', 'bias', 'abuse', 'abolish', 'abuse', 'abuse', 'bid', 'wednesday', 'able',
         'betray', 'accident', 'abduct', 'bigot', 'bet', 'abandon', 'besides', 'access', 'friday', 'bestow', 'abound',
         'absent', 'beware', 'abundant', 'abnormal', 'aboard', 'about', 'accelerate', 'abort', 'thursday', 'tuesday',
         'sunday', 'berth', 'beyond', 'benevolent', 'abate', 'abide', 'bicycle', 'beside', 'accept', 'berry',
         'bewilder', 'abrupt', 'saturday', 'accessory', 'absorb']

out_words = sorted(list(filter(lambda word: len(word) == 6, words)))
print(*out_words)
```
### map() и filter()
Напишите программу, которая с помощью встроенных функций map() и filter() удаляет из списка numbers все нечетные элементы, большие 
47, а все четные элементы нацело делит на два (целочисленное деление – //). Полученные числа следует вывести на одной строке, разделив символом пробела и сохранив исходный порядок.
```sh
numbers = [46, 61, 34, 17, 56, 26, 93, 1, 3, 82, 71, 37, 80, 27, 77, 94, 34, 100, 36, 81, 33, 81, 66, 83, 41, 80, 80,
           93, 40, 34, 32, 16, 5, 16, 40, 93, 36, 65, 8, 19, 8, 75, 66, 21, 72, 32, 41, 59, 35, 64, 49, 78, 83, 27, 57,
           53, 43, 35, 48, 17, 19, 40, 90, 57, 77, 56, 80, 95, 90, 27, 26, 6, 4, 23, 52, 39, 63, 74, 15, 66, 29, 88, 94,
           37, 44, 2, 38, 36, 32, 49, 5, 33, 60, 94, 89, 8, 36, 94, 46, 33]

out_numbers = map(lambda x: x // 2 if x % 2 == 0 else x,
                  filter(lambda number: not (number % 2 and number > 47), numbers))

print(*out_numbers)
```
### США
Список data содержит информацию о численности населения некоторых штатов США. Напишите программу сортировки по убыванию списка data на основании последнего символа в названии штата. 
```sh
data = [(19542209, 'New York'), (4887871, 'Alabama'), (1420491, 'Hawaii'), (626299, 'Vermont'),
        (1805832, 'West Virginia'), (39865590, 'California'), (11799448, 'Ohio'), (10711908, 'Georgia'),
        (10077331, 'Michigan'), (10439388, 'Virginia'), (7705281, 'Washington'), (7151502, 'Arizona'),
        (7029917, 'Massachusetts'), (6910840, 'Tennessee')]

data.sort(key=lambda data: data[1][-1], reverse=True)

for i in data:
    print(i[1] + ':', i[0])
```
### Длина
Список data содержит слова на русском языке. Напишите программу его сортировки по возрастанию длины слов, а затем в лексикографическом порядке. Отсортированные слова следует вывести на одной строке, разделив символом пробела.
```sh
data = ['год', 'человек', 'время', 'дело', 'жизнь', 'день', 'рука', 'раз', 'работа', 'слово', 'место', 'лицо', 'друг',
        'глаз', 'вопрос', 'дом', 'сторона', 'страна', 'мир', 'случай', 'голова', 'ребенок', 'сила', 'конец', 'вид',
        'система', 'часть', 'город', 'отношение', 'женщина', 'деньги']

data = sorted(data)
data.sort(key=lambda data: len(data))
print(*data, sep=' ')
```
### mixed_list 1
Список mixed_list содержит целочисленные и строковые значения. Напишите программу, которая с помощью встроенной функции max() находит и выводит наибольшее числовое значение в указанном списке.
```sh
mixed_list = ['tuesday', 'abroad', 'abuse', 'beside', 'monday', 'abate', 'accessory', 'absorb', 1384878, 'sunday',
              'about', 454805, 'saturday', 'abort', 2121919, 2552839, 977970, 1772933, 1564063, 'abduct', 901271,
              2680434, 'bicycle', 'accelerate', 1109147, 942908, 'berry', 433507, 'bias', 'bestow', 1875665, 'besides',
              'bewilder', 1586517, 375290, 1503450, 2713047, 'abnormal', 2286106, 242192, 701049, 2866491, 'benevolent',
              'bigot', 'abuse', 'abrupt', 343772, 'able', 2135748, 690280, 686008, 'beyond', 2415643, 'aboard', 'bet',
              859105, 'accident', 2223166, 894187, 146564, 1251748, 2851543, 1619426, 2263113, 1618068, 'berth',
              'abolish', 'beware', 2618492, 1555062, 'access', 'absent', 'abundant', 2950603, 'betray', 'beverage',
              'abide', 'abandon', 2284251, 'wednesday', 2709698, 'thursday', 810387, 'friday', 2576799, 2213552,
              1599022, 'accept', 'abuse', 'abound', 1352953, 'bid', 1805326, 1499197, 2241159, 605320, 2347441]

max_num = max(filter(lambda x: type(x) == int, mixed_list))
print(max_num)
```
### mixed_list 2
Список mixed_list содержит целочисленные и строковые значения. Напишите программу его сортировки по неубыванию значений элементов, при этом числа должны следовать до строк.  Элементы отсортированного списка выведите на одной строке, разделив символом пробела.
```sh
mixed_list = ['beside', 48, 'accelerate', 28, 'beware', 'absorb', 'besides', 'berry', 15, 65, 'abate', 'thursday', 76,
              70, 94, 35, 36, 'berth', 41, 'abnormal', 'bicycle', 'bid', 'sunday', 'saturday', 87, 'bigot', 41, 'abort',
              13, 60, 'friday', 26, 13, 'accident', 'access', 40, 26, 20, 75, 13, 40, 67, 12, 'abuse', 78, 10, 80,
              'accessory', 20, 'bewilder', 'benevolent', 'bet', 64, 38, 65, 51, 95, 'abduct', 37, 98, 99, 14, 'abandon',
              'accept', 46, 'abide', 'beyond', 19, 'about', 76, 26, 'abound', 12, 95, 'wednesday', 'abundant', 'abrupt',
              'aboard', 50, 89, 'tuesday', 66, 'bestow', 'absent', 76, 46, 'betray', 47, 'able', 11]

print(*sorted(mixed_list, key= str))
```
### Противоположный цвет
Напишите программу, которая по трем компонентам заданного цвета, находит компоненты противоположного цвета. 
```sh
print(*map(lambda x: 255 - int(x), input().split()))
```
### Значение многочлена 🌶️
На вход программе на первой строке подаются коэффициенты многочлена, разделенные символом пробела и целое число 
x на второй строке. Напишите программу, которая вычисляет значение указанного многочлена при заданном значении 
x.
```sh
def evaluate(coefficients, x):
    sum = coefficients[-1]
    for i in range(1, len(coefficients)):
        sum += coefficients[-1 - i] * x ** i
    print(sum)


evaluate(list(map(int, input().split())), int(input()))
```
### ignore_command()
Функция ignore_command() принимает на вход один строковый аргумент command – команда, которую нужно проверить,
и возвращает значение True, если в команде содержится подстрока из списка ignore и False – если нет.
```sh
def ignore_command(command):
    ignore = ['alias', 'configuration', 'ip', 'sql', 'select', 'update', 'exec', 'del', 'truncate']
    result = any(map(lambda x: x in command, ignore))
    return result
```
### Страны
Используя параллельную итерацию сразу по трем спискам countries, capitals и population выведите информацию о стране.
```sh
countries = ['Russia', 'USA', 'UK', 'Germany', 'France', 'India']
capitals = ['Moscow', 'Washington', 'London', 'Berlin', 'Paris', 'Delhi']
population = [145_934_462, 331_002_651, 80_345_321, 67_886_011, 65_273_511, 1_380_004_385]

for i in zip(countries, capitals, population):
    print(i[1], 'is the capital of', i[0] + ', population equal', i[2], 'people.')
```
### Внутри шара
На вход программе подаются три строки текста с вещественными числами, значениями абсцисс (x), ординат (y) и аппликат (z) точек трехмерного пространства. Напишите программу для проверки расположения всех точек с введенными координатами внутри либо на поверхности шара с центром в начале координат и радиусом 
R = 2.
```sh
abscissas = [float(i) for i in input().split()]
ordinates = [float(i) for i in input().split()]
applicates = [float(i) for i in input().split()]

print(all(map(lambda x: x[0]**2 + x[1]**2 + x[2]**2 <= 4, zip(abscissas, ordinates, applicates))))
```
### Корректный IP-адрес
Напишите программу с использованием встроенной функции all() для проверки корректности IP-адреса: все ли октеты в IP-адресе – числа со значением от 
0 до 255.
```sh
print(all(map(lambda num: num.isdigit() and 0<=int(num)<=255, input().split('.'))))
```
### Интересные числа
На вход программе подаются два натуральных числа a и b. Напишите программу с использованием встроенной функции all() для обнаружения всех целых чисел в диапазоне 
[a; b], которые делятся на каждую содержащуюся в них цифру без остатка.
```sh
start, stop = int(input()), int(input())

numbers = []
for i in range(start, stop+1):
    num = i

    delit = []
    while i > 0:
        delit.append(i % 10)
        i //= 10
    if 0 in delit:
        continue
    out = []
    for i in delit:
        if num % i == 0:
            flag = True
            out.append(flag)
        else:
            flag = False
            out.append(flag)
    if all(out):
        numbers.append(num)

print(*numbers)
```
### Хороший пароль
Хороший пароль по условиям этой задачи состоит как минимум из 
7 символов, содержит хотя бы одну цифру, заглавную и строчную букву. Напишите программу со встроенной функцией any() для определения хорош ли введенный пароль.
```sh
password = list(input())

print('YES' if (len(password) >= 7) * (any(map(lambda x: x.isdigit(), password))) * (any(map(lambda x: x.isupper(), password))) * any(map(lambda x: x.islower(), password)) == 1 else 'NO')
```
### Отличники
Учитель Тимур проверял контрольные работы по математике в нескольких классах онлайн-школы BEEGEEK и решил убедиться, что в каждом классе есть хотя бы один отличник – ученик с оценкой 
5 по контрольной работе. Напишите программу с использованием встроенных функций all(), any() для помощи Тимуру в проверке.
```sh
botan_in_class = []
for amount_class in range(int(input())):
    score = []
    for student in range(int(input())):
        info = input().split()
        score.append(info[1])
    botan_in_class.append(any(map(lambda x: x == '5', score)))
print('YES' if all(botan_in_class) else 'NO')
```