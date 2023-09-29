# "Поколение Python": курс для продвинутых
## 16 Итоговая работа на функции
### Письмо для экзамена
Напишите функцию generate_letter(), которая будет собирать электронное письмо в соответствии с шаблоном:
```sh
To: <mail>
Приветствую, <name>!
Вам назначен экзамен, который пройдет <date>, в <time>.
По адресу: <place>. 
Экзамен будет проводить <teacher> в кабинете <number>. 
Желаем удачи на экзамене!
```
```sh
def generate_letter(mail, name, date, time, place, teacher='Тимур Гуев', number=17):
    return f'To: {mail}\nПриветствую, {name}!\nВам назначен экзамен, который пройдет {date}, в {time}.\nПо адресу: {place}.\nЭкзамен будет проводить {teacher} в кабинете {number}.\nЖелаем удачи на экзамене!'
```
### Pretty print
Напишите функцию pretty_print(), которая выводит содержимое списка с рамкой. 
```sh
def pretty_print(data, side='-', delimiter='|'):
    info_str = '' + delimiter
    for i in data:
        info_str += f' {i} {delimiter}'
    delimiter_str = (' ' + (len(info_str) - 2) * f'{side}' + ' ')
    print(f'{delimiter_str}\n{info_str}\n{delimiter_str}')
```
### concat()
Напишите функцию concat(), принимающую переменное количество аргументов и объединяющую их в одну строку через разделитель (sep). Если разделитель не задан, им служит пробел.
```sh
def concat(*args, sep=' '):
    return sep.join(map(str, args))
```
### product_of_odds()
Перепишите функцию product_of_odds() в функциональном стиле с использованием встроенных функций filter() и reduce().
```sh
from functools import reduce
def product_of_odds(data):  # data - список целых чисел
    return reduce(lambda x, y: x * y, filter(lambda x: x % 2 == 1, data), 1)
```
### "word"
Дан список слов words. Допишите код после оператора распаковки (*), который оборачивает в двойные кавычки все элементы списка words, а затем печатает результат на одной строке через пробел.
```sh
words = 'the world is mine take a look what you have started'.split()

print(*map(lambda x: '"' + x + '"', words))
```
### Числа-палиндромы 1
Дан список целых чисел numbers. Допишите код после оператора распаковки (*), для удаления из списка всех чисел-палиндромов и печати результата на одной строке через пробел.
```sh
numbers = [18, 191, 9009, 5665, 78, 77, 45, 23, 19991, 908, 8976, 6565, 5665, 10, 1000, 908, 909, 232, 45654, 786]
print(*filter(lambda x: str(x) != str(x)[::-1], numbers))
```
### Числа-палиндромы 2
Дан список numbers, состоящий из кортежей. Допишите пропущенную часть программы, чтобы список sorted_numbers был упорядочен по убыванию среднего арифметического элементов кортежей списка numbers.
```sh
numbers = [(10, -2, 3, 4), (-13, 56), (1, 9, 2), (-1, -9, -45, 32), (-1, 5, 1), (17, 0, 1), (0, 1), (3,), (39, 12),
           (11, -23), (10, -100, 21, 32), (3, -8), (1, 1)]

sorted_numbers = sorted(numbers, key=lambda x: sum(x) / len(x), reverse=True)

print(sorted_numbers)
```
### call()
Напишите функцию call(), которая принимает произвольную функцию и аргументы для неё и делает вызов переданной функции, возвращая ее значение.
```sh
def call(name, *args):
    return name(*args)
```
### compose()
Напишите функцию compose(), которая принимает на вход две других одноаргументных функции f и g и возвращает новую функцию. Эта новая функция также должна принимать один аргумент x и применять к нему исходные функции в нужном порядке: для функций f и g порядок применения должен выглядеть, как f(g(x)).
```sh
def compose(name1, name2):
    return lambda x: name1(name2(x))
```
### arithmetic_operation()
Напишите функцию arithmetic_operation(), которая принимает символ одной из четырех арифметических операций (+, -, *, /) и возвращает функцию двух аргументов для соответствующей операции.
```sh
def arithmetic_operation(operation):
    if operation == '+':
        return lambda x, y: x + y
    elif operation == '-':
        return lambda x, y: x - y
    elif operation == '*':
        return lambda x, y: x * y
    elif operation == '/':
        return lambda x, y: x / y
```
### В одну строку
Дана строка из разделенных пробелами слов в разных регистрах. Напишите программу, которая отсортирует слова независимо от регистра, а затем выведет их. Отсортированные слова должны выводиться на печать в исходном регистре, в каком переданы программе на вход.
```sh
print(*sorted(input().split(), key=lambda x: x.lower()))
```
### Гематрия слова
Гематрией слова называется сумма числовых значений входящих в него букв.

Напишите программу, которая выводит слова в начальном регистре (каждое на отдельной строке) в порядке возрастания их гематрии. Если гематрия слов совпадает, они выводятся в алфавитном (лексикографическом) порядке.
```sh
def gematre(word):
    return sum([ord(i.upper()) - ord('A') for i in word])


words = sorted([input() for i in range(int(input()))])

print(*sorted(words, key=gematre), sep='\n')
```
### Сортировка IP-адресов
Напишите программу, которая считывает IP-адреса и выводит их в порядке возрастания в соответствии с десятичным представлением.
```sh
def ip_10_to_2(ip):
    ip = map(int, ip.split('.'))
    power = [3, 2, 1, 0]
    number_2 = sum(list(map(lambda x, y: x * 256 ** y, ip, power)))
    return number_2


ips = [input() for i in range(int(input()))]
print(*sorted(ips, key=ip_10_to_2), sep='\n')
```