# "Поколение Python": курс для продвинутых
## 11 Итоговая работа на словари
### Больше 20
Дополните приведенный код, чтобы в списках значений элементов словаря my_dict  не было чисел, больших 20. При этом порядок оставшихся элементов меняться не должен.
```sh
my_dict = {'C1': [10, 20, 30, 7, 6, 23, 90], 'C2': [20, 30, 40, 1, 2, 3, 90, 12], 'C3': [12, 34, 20, 21],
           'C4': [22, 54, 209, 21, 7], 'C5': [2, 4, 29, 21, 19], 'C6': [4, 6, 7, 10, 55], 'C7': [4, 8, 12, 23, 42],
           'C8': [3, 14, 15, 26, 48], 'C9': [2, 7, 18, 28, 18, 28]}

my_dict = {keys: [i for i in my_dict[keys] if i <= 20] for keys, values in my_dict.items()}

# result = {}
# for keys, values in my_dict.items():
#     temp = []
#     for i in my_dict[keys]:
#         if i < 20:
#             temp.append(i)
#     result[keys] = temp
```
### Домены
Словарь emails содержит информацию об электронных адресах пользователей, сгруппированных по домену. Дополните приведенный код, чтобы он вывел все электронные адреса в алфавитном порядке, каждый на отдельной строке, в формате username@domain.
```sh
emails = {'nosu.edu': ['timyr', 'joseph', 'svetlana.gaeva', 'larisa.mamuk'],
          'gmail.com': ['ruslan.chaika', 'rustam.mini', 'stepik-best'],
          'msu.edu': ['apple.fruit', 'beegeek', 'beegeek.school'],
          'yandex.ru': ['surface', 'google'],
          'hse.edu': ['tomas-henders', 'cream.soda', 'zivert'],
          'mail.ru': ['angel.down', 'joanne', 'the.fame.moster']}

mail = []
for domain, names in emails.items():
    for name in emails[domain]:
        str = ''
        str = name + '@' + domain
        mail.append(str)
print(*(sorted(mail)), sep='\n')
```
### Минутка генетики
Напишите программу, переводящую цепь ДНК в цепь РНК.
```sh
d = {'A': 'U', 'C': 'G', 'G': 'C', 'T': 'A'}

dna = input()
for i in dna:
    print(d[i], end='')
```
### Порядковый номер
Напишите программу, определяющую для каждого слова порядковый номер его вхождения в текст именно в этой форме, с учетом регистра. Для первого вхождения слова программа выведет 1, для второго вхождения того же слова — 2 и т. д.
```sh
text = input().split()

d = {}
for i in text:
    d[i] = d.get(i, 0) + 1
    print(d[i], end=' ')
```
### Scrabble game
Напишите программу подсчета итоговой стоимости введенного слова.
```sh
d = {
    1: "AEILNORSTU",
    2: "DG",
    3: "BCMP",
    4: "FHVWY",
    5: "K",
    8: "JX",
    10: "QZ"
}

word = input()
summa = 0
for i in word:
    for key, val in d.items():
        if i in val:
            summa += key
print(summa)
```
### Строка запроса
Напишите функцию build_query_string(), которая принимает на вход словарь с параметрами и возвращает строку запроса, сформированную из этих параметров.
```sh
def build_query_string(params):
    out = []
    for key, val in params.items():
        query_string = str(key) + '=' + str(val)
        out.append(query_string)
    return '&'.join(sorted(out))
```
### Слияние словарей 🌶️
Напишите функцию merge(), объединяющую словари в один общий. Функция должна принимать список словарей и возвращать словарь, каждый ключ которого содержит множество (тип данных set) уникальных значений собранных из всех словарей переданного списка.
```sh
def merge(values):  # values - это список словарей
    d = {}
    for i in range(len(values)):
        for key, val in values[i].items():
            d.setdefault(key, set()).add(val)
    return d
```
### Опасный вирус 😈
В файловую систему компьютера, на котором развернута наша ❤️ платформа Stepik, проник опасный вирус и сломал контроль прав доступа к файлам. Говорят, вирус написал один из студентов курса Python для начинающих.

Для каждого файла известно, с какими действиями можно к нему обращаться:
- запись W (write, доступ на запись в файл);
- чтение R (read, доступ на чтение из файла);
- запуск X (execute, запуск на исполнение файла).

Напишите программу для восстановления контроля прав доступа к файлам. Ваша программа для каждого запроса должна будет возвращать OK если выполняется допустимая операция, и Access denied, если операция недопустима.
```sh
operation = {'execute': 'X', 'read': 'R', 'write': 'W'}

d = {}

for i in range(int(input())):
    programm = input().split()
    d.setdefault(programm[0], programm[1:])

for j in range(int(input())):
    code = input().split()
    print('OK' if operation[code[0]] in d[code[1]] else 'Access denied')
```
### Покупки в интернет-магазине 🌶️
Напишите программу для подсчета количества единиц каждого вида товара из приобретенных каждым покупателем интернет-магазина.
```sh
d = {}
for i in range(int(input())):
    s = input().split()
    d.setdefault(s[0], {})
    d[s[0]][s[1]] = d[s[0]].get(s[1], 0) + int(s[2])

for i in sorted(d):
    print(i+':')
    for key, val in sorted(d[i].items()):
        print(key, val)
```
