## Условная конструкция

```Python
if логическое_выражение:
    инструкции
[elif логическое выражение:
    инструкции]
[else: 
    инструкции]
```

## вложенные конструкции

```Python
language = "english"
daytime == "morning"
if language == "english":
    print("English")
    if daytime == "morning":
        print("Good morning")
    else:
        print("Good evening")
```


## цикл while

```Python
number = 1
 
while number < 5:
    print(f"number = {number}")
    number += 1
print("Работа программы завершена")
```

дполнительный блок else, если условие false
```Python
number = 1
 
while number < 5:
    print(f"number = {number}")
    number += 1
else:
    print(f"number = {number}. Работа цикла завершена")
print("Работа программы завершена")
```

## Цикл for


```Python
for переменная in набор_значений:
    инструкции
```

```Python
message = "Hello"
 
for c in message:
    print(c)
```
дополнительный блок else, когда выполнится цикл for
```Python
message = "Hello"
for c in message:
    print(c)
else:
    print(f"Последний символ: {c}. Цикл завершен");
print("Работа программы завершена")  # инструкция не имеет отступа, поэтому не относится к else
```


## вложенные циклы


```Python
i = 1
j = 1
while i < 10:
    while j < 10:
        print(i * j, end="\t")
        j += 1
    print("\n")
    j = 1
    i += 1
```

## break continue


```Python
number = 0
while number < 5:
    number += 1
    if number == 3 :    # если number = 3, выходим из цикла
        break
    print(f"number = {number}")
# 1, 2
```

```Python
number = 0
while number < 5:
    number += 1
    if number == 3 :    # если number = 3, переходим к новой итерации цикла
        continue
    print(f"number = {number}")
#1, 2, 4, 5
```

## функуия range()

* range выдает значение из диапазона с шагом 1
* если указано только одно число, то выдает от 0 до заданного числа
* если нужен другой шаг, то 3й аргумент задает приращение

range(начальное, конечное не включая, шаг)
```Python
r = range(5)            #0 1 2 3 4 
r = range(2, 5)         #2 3 4
r = range(1, 10, 2)     #1 3 5 7 9
r = range(100, 0, -20)  #100 80 60 40 20
```