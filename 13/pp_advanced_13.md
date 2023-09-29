# "Поколение Python": курс для продвинутых
## 13 Модули decimal, fraction и complex
### Decimal 1
Decimal числа, разделенные символом пробела, хранятся в строковой переменной s. Дополните приведенный код, чтобы он вывел сумму наибольшего и наименьшего Decimal числа.
```sh
from decimal import *

s = '0.77 4.03 9.06 3.80 7.08 5.88 0.23 4.65 2.79 0.90 4.23 2.15 3.24 8.57 ' \
    '0.10 8.57 1.49 5.64 3.63 8.36 1.56 6.67 1.46 5.26 4.83 7.23 1.22 1.02 7.82 ' \
    '9.97 5.40 9.79 9.82 2.78 2.96 0.07 1.72 7.24 7.84 9.23 1.71 6.24 5.78 5.37' \
    ' 0.03 9.60 8.86 2.73 5.83 6.50'

a = s.split(' ')
numbers = []

for i in range(len(a)):
    numbers.append(Decimal(a[i]))
print(max(numbers) + min(numbers))
```
### Decimal 2
Decimal числа, разделенные символом пробела, хранятся в строковой переменной s. Дополните приведенный код, чтобы он вывел на первой строке сумму всех чисел, а на второй строке
5 самых больших чисел в порядке убывания, разделенных символом пробела.
```sh
from decimal import *

s = '9.73 8.84 8.92 9.60 9.32 8.97 8.53 1.26 6.62 9.85 1.85 1.80 0.83 6.75' \
    ' 9.74 9.11 9.14 5.03 5.03 1.34 3.52 8.09 7.89 8.24 8.23 5.22 0.30 2.59 ' \
    '1.25 6.24 2.14 7.54 5.72 2.75 2.32 2.69 9.32 8.11 4.53 0.80 0.08 9.36 5.22 ' \
    '4.08 3.86 5.56 1.43 8.36 6.29 5.13'

a = s.split(' ')
numbers = []
for i in range(len(a)):
    numbers.append(Decimal(a[i]))

print(sum(numbers))
print(*sorted(numbers)[::-1][0:5])
```
### Decimal 3
Дополните приведенный код, чтобы он вывел сумму наибольшей и наименьшей цифры Decimal числа.
```sh
from decimal import *

num = abs(Decimal(input()))

first = num//1

if first == 0:
    print(sorted(num.as_tuple()[1])[0] + sorted(num.as_tuple()[1])[-1] - 1)
else:
    print(sorted(num.as_tuple()[1])[0] + sorted(num.as_tuple()[1])[-1])
```
### Математическое выражение
На вход программе подается Decimal число d. Напишите программу, которая вычисляет значение выражения.
```sh
from decimal import *
from math import *

d = Decimal(input())

print(d.exp() + d.ln() + d.log10() + d.sqrt() )
```
### Fraction 1
Десятичные числа хранятся в списке numbers в виде строк. Дополните приведенный код, чтобы он для каждого десятичного числа вывел его представление в виде обыкновенной дроби.
```sh
from fractions import Fraction

numbers = ['6.34', '4.08', '3.04', '7.49', '4.45', '5.39', '7.82', '2.76', '0.71', '1.97',
           '2.54', '3.67', '0.14', '4.29', '1.84', '4.07', '7.26', '9.37', '8.11', '4.30',
           '7.16', '2.46', '1.27', '0.29', '5.12', '4.02', '6.95', '1.62', '2.26', '0.45',
           '6.91', '7.39', '0.52', '1.88', '8.38', '0.75', '0.32', '4.81', '3.31', '4.63',
           '7.84', '2.25', '1.10', '3.35', '2.05', '7.87', '2.40', '1.20', '2.58', '2.46']

for i in range(len(numbers)):
    print(numbers[i], '=', Fraction(numbers[i]))
```
### Fraction 2
Десятичные числа, разделенные символом пробела, хранятся в строковой переменной s. Дополните приведенный код, чтобы он вывел сумму наибольшего и наименьшего числа в виде обыкновенной дроби.
```sh
from fractions import Fraction

s = ('0.78 4.3 9.6 3.88 7.08 5.88 0.23 4.65 2.79 0.90 4.23 2.15'
     ' 3.24 8.57 0.10 8.57 1.49 5.64 3.63 8.36 1.56 6.67 1.46 5.26'
     ' 4.83 7.13 1.22 1.02 7.82 9.97 5.40 9.79 9.82 2.78 2.96 0.07 '
     '1.72 7.24 7.84 9.23 1.71 6.24 5.78 5.37 0.03 9.60 8.86 2.73 5.83 6.50 0.123 0.00021').split()

numbers = [Fraction(s[i]) for i in range(len(s))]

print(max(numbers) + min(numbers))
```
### Сократите дробь
Даны два натуральных числа m и n. Напишите программу, которая сокращает дробь и выводит ее.
```sh
from fractions import Fraction

n, d = int(input()), int(input())

number = Fraction(n, d)

print(number)
```
### Операции над дробями
Даны две дроби в формате a/b. Напишите программу, которая вычисляет и выводит их сумму, разность, произведение и частное.
```sh
from fractions import Fraction

n1, n2 = input(), input()

print(n1,'+',n2,'=',Fraction(n1) + Fraction(n2))
print(n1,'-',n2,'=',Fraction(n1) - Fraction(n2))
print(n1,'*',n2,'=',Fraction(n1) * Fraction(n2))
print(n1,'/',n2,'=',Fraction(n1) / Fraction(n2))
```
### Сумма дробей 1
На вход программе подается натуральное число n. Напишите программу, которая вычисляет и выводит рациональное число.
```sh
from fractions import Fraction

n = int(input())
sum = 0
for i in range(1, n + 1):
    sum += Fraction(1, i ** 2)
print(sum)
```
### Сумма дробей 2
На вход программе подается натуральное число n. Напишите программу, которая вычисляет и выводит рациональное число.
```sh
from fractions import Fraction
from math import factorial

n = int(input())
sum = 0
for i in range(1, n + 1):
    sum += Fraction(1, factorial(i))
print(sum)
```
### Юный математик 🌶️
На вход программе подается натуральное число n. Напишите программу, которая находит наибольшую правильную несократимую дробь с суммой числителя и знаменателя равной n.
```sh
from fractions import Fraction

n = int(input())

numbers = []
for i in range(1, n):
    number = Fraction(int(i), int(n - i))
    if number.numerator < number.denominator and number.numerator + number.denominator == n:
        numbers.append(number)

print(numbers[-1])
```
### Упорядоченные дроби
На вход программе подается натуральное число n. Напишите программу, которая выводит в порядке возрастания все несократимые дроби, заключённые между 0 и 1, знаменатель которых не превосходит n.
```sh
from fractions import Fraction

n = int(input())
numbers = sorted(set([Fraction(i, j) for i in range(1, n + 1) for j in range(1, n + 1) if i < j]))
[print(numbers[i]) for i in range(len(numbers))]

```
### Операции над комплексными числами
Даны два комплексных числа. Напишите программу, которая вычисляет и выводит их сумму, разность и произведение.
```sh
n1,n2 = complex(input()), complex(input())

print(n1,'+',n2,'=', n1 + n2)
print(n1,'-',n2,'=', n1 - n2)
print(n1,'*',n2,'=', n1 * n2)
```
### Модуль комплексного числа
Комплексные числа хранятся в списке numbers. Дополните приведенный код так, чтобы он вывел комплексное число с наибольшим модулем и сам модуль числа на отдельных строках.
```sh
numbers = [3 + 4j, 3 + 1j, -7 + 3j, 4 + 8j, -8 + 10j, -3 + 2j,
           3 - 2j, -9 + 9j, -1 - 1j, -1 - 10j, -20 + 15j,
           -21 + 1j, 1j, -3 + 8j, 4 - 6j, 8 + 2j, 2 + 3j]
max_abs_num = 0
for i in range(len(numbers)):
    abs_num = abs(numbers[i])

    if abs_num > max_abs_num:
        max_abs_num = abs_num
        number = i

print(numbers[number])
print(max_abs_num)
```
### Сопряженные числа
Дано натуральное число n и два комплексных числа z1 и z2. Напишите программу, которая вычисляет и выводит значение выражения
```sh
n = int(input())
z1,z2 = complex(input()), complex(input())

print(z1**n + z2**n + z1.conjugate()**n + z2.conjugate()**(n+1))
```