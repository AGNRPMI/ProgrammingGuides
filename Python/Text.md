## Вывод на консоль

```Python
print("Hello world")
print("Hello world")
print("Hello world")    #выведутся три отдельные строки

print("Hello World", end=" ")
print("Hello METANIT.COM", end=" ")
print("Hello Python")   # вывод в одну строку

a = 1
b = 5.5
c = "dsfs"
print("{} - {} - {}".format(a,b,c)) #интерполяция
print(a+b+c)                        #конкатенация


```


## Консольный ввод
```Python
name = input("Your name: ")
age = input("Your age: ")
print(f"Name: {name}  Age: {age}")
```

## команды
```Python
text = 'fff'
print(text.lower())     #перевод текста в нижний регистр
print(text.upper())     #перевод текста в вехний регистр
print(text.replace('fff','aaa'))     #замена символов


print(text[0])          #вывод символа по порядковому номеру
print(text[len(text)-1])          #вывод символа через длину сообщения (индексация начинается с номера 0)
print(text[-5])          #вывод символа по порядку с конца
print(text[:])          #вывод всего текста
print(text[0:5])          #вывод символов в диапазоне по порядковому номеру
print(text[:10])          #вывод символов по порядковому номеру с начала до индекса 10
print(text[10:])          #вывод символов по порядковому номеру с индекса 10 до конца
print(text[0:len(text)-1:6])          #вывод символов по порядковому номеру с индекса 0 до конца с шагом 6
print(text[::6])          #вывод символов по порядковому номеру с индекса 0 до конца с шагом 6


```

















