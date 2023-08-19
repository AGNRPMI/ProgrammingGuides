## Функции


```Python
def имя_функции ([параметры]):
    инструкции
```

```Python
def say_hello():
    print("Hello")
 
 
print("Bye")
```

передача нскольких параметров
```Python
def print_person(name = "Tom", age = 18):
    print(f"Name: {name}  Age: {age}")
 
 
print_person()              # Name: Tom  Age: 18
print_person("Bob")         # Name: Bob  Age: 18
print_person("Sam", 37)     # Name: Sam  Age: 37
```

## передача параметров по имени
все параметры после * можно передавать только с обозначением имени переменной
```Python
def print_person(name, *,  age, company):
    print(f"Name: {name}  Age: {age}  Company: {company}")
 
 
print_person("Bob", age = 41, company ="Microsoft")    # Name: Bob  Age: 41  company: Microsoft
```

## передача параметров по позиции
все параметры до / можно передавать только по порядку позиций
```Python
def print_person(name, /, age, company="Microsoft"):
    print(f"Name: {name}  Age: {age}  Company: {company}")
 
 
print_person("Tom", company="JetBrains", age = 24)     # Name: Tom  Age: 24  company: JetBrains
print_person("Bob", 41)                 # Name: Bob  Age: 41  company: Microsoft
```

## передача неопределенного количества значений

```Python
def sum(*numbers):
    result = 0
    for n in numbers:
        result += n
    print(f"sum = {result}")
 
 
sum(1, 2, 3, 4, 5)      # sum = 15
sum(3, 4, 5, 6)         # sum = 18
```


## функция с возвращаемым значением

```Python
def имя_функции ([параметры]):
    инструкции
    return возвращаемое_значение
```
```Python
def print_person(name, age):
    if age > 120 or age < 1:
        print("Invalid age")
        return
    print(f"Name: {name}  Age: {age}")
 
 
print_person("Tom", 22)
print_person("Bob", -102)
```

## функция как тип
переменной можно присвоить функцию
```Python
def say_hello(): print("Hello")
def say_goodbye(): print("Good Bye")
 
message = say_hello
message()       # Hello
message = say_goodbye
message()       # Good Bye
```

## функция как параметр функции

```Python
def do_operation(a, b, operation):
    result = operation(a, b)
    print(f"result = {result}")
 
def sum(a, b): return a + b
def multiply(a, b): return a * b
 
do_operation(5, 4, sum)         # result = 9
do_operation(5, 4, multiply)   # result = 20
```

## функция как результат функции

```Python
def sum(a, b): return a + b
def subtract(a, b): return a - b
def multiply(a, b): return a * b
 
 
def select_operation(choice):
    if choice == 1:
        return sum
    elif choice == 2:
        return subtract
    else:
        return multiply
 
 
operation = select_operation(1)     # operation = sum
print(operation(10, 6))             # 16
 
operation = select_operation(2)     # operation = subtract
print(operation(10, 6))             # 4
 
operation = select_operation(3)     # operation = multiply
print(operation(10, 6))             # 60
```

## лямбда выражения

```Python
lambda [параметры] : инструкция
```
```Python
square = lambda n: n * n
 
print(square(4))    # 16
print(square(5))    # 25
```

## замыкания (closure)
Замыкание (closure) представляет функцию, которая запоминает свое лексическое окружение даже в том случае, когда она выполняется вне своей области видимости.

Технически замыкание включает три компонента:
- внешняя функция, которая определяет некоторую область видимости и в которой определены некоторые переменные и параметры - лексическое окружение
- переменные и параметры (лексическое окружение), которые определены во внешней функции
- вложенная функция, которая использует переменные и параметры внешней функции

```Python
def outer():        # внешняя функция
    n = 5           # лексическое окружение - локальная переменная 
    def inner():      # локальная функция
        nonlocal n
        n += 1        # операции с лексическим окружением
        print(n) 
    return inner 
 
fn = outer()   # fn = inner, так как функция outer возвращает функцию inner
# вызываем внутреннюю функцию inner
fn()    # 6
fn()    # 7
fn()    # 8
```


## декораторы
Декораторы в Python представляют функцию, которая в качестве параметра получает функцию и в качестве результата также возвращает функцию. Декораторы позволяют модифицировать выполняемую функцию, значения ее параметров и ее результат без изменения исходного кода этой функции.

```Python
# определение функции декоратора
def select(input_func):    
    def output_func():      # определяем функцию, которая будет выполняться вместо оригинальной
        print("*****************")  # перед выводом оригинальной функции выводим всякую звездочки
        input_func()                # вызов оригинальной функции
        print("*****************")  # после вывода оригинальной функции выводим всякую звездочки
    return output_func     # возвращаем новую функцию
 
# определение оригинальной функции
@select         # применение декоратора select
def hello():
    print("Hello METANIT.COM")
 
# вызов оригинальной функции
hello()
```

