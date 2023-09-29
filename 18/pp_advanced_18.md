# "Поколение Python": курс для продвинутых
## 18 Итоговая работа на файлы
### Количество строк в файле
На вход программе подается строка текста с именем текстового файла. Напишите программу для вывода на экран количества строк данного файла.
```sh
count = 0
with open(input(), 'r') as file:
    for line in file:
        count += 1
print(count)
```
## Суммарная стоимость
Напишите программу для подсчета суммарной месячной выручки фирмы. 


```sh
amount = 0
with open('ledger.txt', 'r') as file:
    for line in file:
        amount += int(line.strip()[1:])
print(f'${amount}')
```
## Goooood students
Напишите программу для подсчета количества студентов, сдавших все три теста. Тест считается сданным, если количество баллов по нему не меньше 65.
```sh
count = 0
with open('grades.txt', 'r') as file:
    for line in file:
        info = line.strip().split()
        if int(info[1]) >= 65 and int(info[2]) >= 65 and int(info[3]) >= 65:
            count += 1
print(count)
```
## Самое длинное слово в файле
Программа должна вывести самые длинные слова файла words.txt, каждое с новой строки, не меняя их порядка следования.

```sh
with open('words.txt', 'r') as file:
    for line in file:
        in_data = line.strip().split()
        info = set(line.strip().split())
        data = sorted(info, key=len, reverse=True)
        word_len = len(data[0])

        answer = [word for word in data if len(word) == word_len]

        for word in in_data:
            if word in answer:
                print(word)
```
## Tail of a File
На вход программе подается строка текста с именем текстового файла. Напишите программу, выводящую на экран последние 10 строк данного файла.
```sh
with open(input(), 'r', encoding='utf-8') as file:
    print(*[line.strip() for line in file.readlines()][-10:], sep='\n')
```
## Forbidden words 🌶️
На вход программе подается строка текста с именем текстового файла. Напишите программу, выводящую на экран содержимое этого файла, но с заменой всех запрещенных слов звездочками * (количество звездочек равно количеству букв в слове).
```sh
with open(input().strip(), encoding='utf-8') as in_file, open('forbidden_words.txt', encoding='utf-8') as forbidden:
    s = in_file.read()
    word = list(forbidden.read().strip().split())
    s_lower = s.lower()
    for w in word:
        s_lower = s_lower.replace(w, '*' * len(w))
    out = ''
    for i in range(len(s_lower)):
        if s_lower[i] != '*':
            out += s[i]
        else:
            out += '*'
    print(out)
```
## Транслитерация 🌶️
Вам доступен текстовый файл cyrillic.txt, содержащий текст. Напишите программу для транслитерации этого файла, то есть замены кириллических символов на латинские в соответствии с предложенной таблицей. Все остальные символы надо оставить без изменений. Результат транслитерации требуется записать в файл transliteration.txt.
```sh
d = {'а': 'a', 'б': 'b', 'в': 'v', 'г': 'g', 'д': 'd', 'е': 'e', 'ё': 'jo', 'ж': 'zh', 'з': 'z', 'и': 'i',
     'й': 'j', 'к': 'k', 'л': 'l', 'м': 'm', 'н': 'n', 'о': 'o', 'п': 'p', 'р': 'r', 'с': 's', 'т': 't',
     'у': 'u', 'ф': 'f', 'х': 'h', 'ц': 'c', 'ч': 'ch', 'ш': 'sh', 'щ': 'shh', 'ъ': '*', 'ы': 'y', 'ь': '\'',
     'э': 'je', 'ю': 'ju', 'я': 'ya', 'А': 'A', 'Б': 'B', 'В': 'V', 'Г': 'G', 'Д': 'D', 'Е': 'E', 'Ё': 'Jo',
     'Ж': 'Zh', 'З': 'Z', 'И': 'I', 'Й': 'J', 'К': 'K', 'Л': 'L', 'М': 'M', 'Н': 'N', 'О': 'O', 'П': 'P',
     'Р': 'R', 'С': 'S', 'Т': 'T', 'У': 'U', 'Ф': 'F', 'Х': 'H', 'Ц': 'C', 'Ч': 'Ch', 'Ш': 'Sh',
     'Щ': 'Shh', 'Ъ': '*', 'Ы': 'y', 'Ь': '\'', 'Э': 'Je', 'Ю': 'Ju', 'Я': 'Ya'}

with open('cyrillic.txt', 'r') as in_file, open('transliteration.txt', 'w') as out_file:
    for line in in_file:
        stroka = ''
        info = list(line)
        for i in info:
            if i in d:
                stroka += d[i]
            else:
                stroka += i
        print(stroka.strip(), file=out_file)
```
## Пропущенные комменты 🌶️
На вход программе подается строка текста с именем текстового файла, в котором написан код на языке Python. Напишите программу, выводящую на экран имена всех функций, для которых отсутствует поясняющий комментарий. Будем считать, что любая строка, начинающаяся со слова def и пробела, является началом определения функции. Функция содержит комментарий, если первый символ предыдущей строки - #.
```sh
with open(input(), 'rt', encoding='utf-8') as file_in:
    code = list(file_in)
    line_1, line_2 = ' ', ' '
    out = []
    for line in code:
        line_2 = line_1
        line_1 = line
        if (line_1.startswith('def ')) and ('#' != line_2[0]):
            temp = line_1.split()
            out.append(temp[1].split('(')[0])
    if not 0 == len(out):
        print(*out, sep='\n')
    else:
        print('Best Programming Team')
```
