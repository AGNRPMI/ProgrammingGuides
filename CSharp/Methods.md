# DRY - Do not Repeat Yourself!

## Методы
общее определение: 
* метод - это именованный блок кода, который выполняет некоторые действия. имеет вид:
* [модификаторы] тип_возвращаемого_значения название_метода ([параметры])

типы: 
* void - ничего не возвращает, просто выполняет какие то действия

```csharp
void SayHello()
{
    Console.WriteLine("Hello"); // инструкции
}

сокращенная запись

void SayHello() => Console.WriteLine("Hello");
```

Параметры позволяют передать в метод некоторые входные данные. Параметры определяются через запятую в скобках после названия метода в виде:

```csharp
тип_метода имя_метода (тип_параметра1 параметр1, тип_параметра2 параметр2, ...)
{
    // действия метода
}
```
> значения которые передатся параметрам называются **аргументами**

соответствие параметров и аргументов по типу данных
```csharp
void PrintPerson(string name, int age)
{
    Console.WriteLine($"Name: {name}  Age: {age}");
} 
PrintPerson("Tom", 24); // Name: Tom  Age: 24
```

необязательные параметры
```csharp
void PrintPerson(string name, int age = 1, string company = "Undefined") // age и company - необязательный параметр, задан по умолчанию
{
    Console.WriteLine($"Name: {name}  Age: {age}  Company: {company}");
}
PrintPerson("Tom");                   // Name: Tom  Age: 1   Company: Undefined
```

передача поименнованых параметров - по умолчанию параметры необходимо вводить по порядку, установленном в определении метода, но можно этого избежать через именнование вводимых параметров
```csharp
PrintPerson("Tom", company:"Microsoft", age: 37);  // Name: Tom  Age: 37  Company: Microsoft
PrintPerson(age:41, name: "Bob");          // Name: Bob  Age: 41  Company: Undefined
PrintPerson(company:"Google", name:"Sam"); // Name: Sam  Age: 1   Company: Google
```


## Методы с возвращаемым значением

объявляется тип метода, если тип объявлен то нужен return
```csharp
string GetMessage()
{
    return "Hello";
}
```
пример
```csharp
int Sum(int x, int y)
{
    return x + y;
} 
int result = Sum(10, 15);   // 25
Console.WriteLine(result);   // 25
 
Console.WriteLine(Sum(5, 6));   // 11
```


передача параметров по значению - переменна и параметр независимые дру от друга
```csharp
void Increment(int n)
{
    n++;
    Console.WriteLine($"Число в методе Increment: {n}");
}
 
int number = 5;
Console.WriteLine($"Число до метода Increment: {number}");
Increment(number);
Console.WriteLine($"Число после метода Increment: {number}");// вывод 5 6 5
```

передача параметров по ссылке - если параметр в методе меняется то меняется и ссыльная переменная
```csharp
void Increment(ref int n)
{
    n++;
    Console.WriteLine($"Число в методе Increment: {n}");
}
 
int number = 5;
Console.WriteLine($"Число до метода Increment: {number}");
Increment(ref number);
Console.WriteLine($"Число после метода Increment: {number}");// вывод 5 6 6
```

выходные параметры - параметр out - при использовании метода возвращаемым значением будет параметр с out
```csharp
void Sum(int x, int y, out int result)
{
    result = x + y;
}
```

входные параметры - параметр in - означает что входной параметр нельзя будет изменить в методе
```csharp
void GetRectangleData(in int width, in int height, out int rectArea, out int rectPerimetr)
{
    //width = 25; // нельзя изменить, так как width - входной параметр
    rectArea = width * height;      
    rectPerimetr = (width + height) * 2;
}
 
int w = 10;
int h = 20;
GetRectangleData(w, h, out var area, out var perimetr);
 
Console.WriteLine($"Площадь прямоугольника: {area}");       // 200
Console.WriteLine($"Периметр прямоугольника: {perimetr}");   // 60
```


## передача неопределенного количества параметров

```csharp
void Sum(params int[]  numbers)
{
    int result = 0;
    foreach (var n in numbers)
    {
        result += n;
    }
    Console.WriteLine(result);
}
 
int[] nums = { 1, 2, 3, 4, 5};
Sum(nums);
Sum(1, 2, 3, 4);
Sum(1, 2, 3);
Sum();
```

Сначала передается обязательные параметры, потом неопределенные
```csharp
void Sum(int initialValue, params int[]  numbers)
{
    int result = initialValue;
    foreach (var n in numbers)
    {
        result += n;
    }
    Console.WriteLine(result);
}

//Так НЕ работает
void Sum(params int[] numbers, int initialValue)
{}
```


## рекурсивные функции - функция ссылающаяся на саму себя

```csharp
int Factorial(int n)
{
    if (n == 1) return 1;
 
    return n * Factorial(n - 1);
}

int Fibonachi(int n)
{
    if (n == 0 || n == 1) return n;
     
    return Fibonachi(n - 1) + Fibonachi(n - 2);
}
```

## локальная функция - функция внутри функции

```csharp
void Compare(int[] numbers1, int[] numbers2)
{
    int numbers1Sum = Sum(numbers1);
    int numbers2Sum = Sum(numbers2);
 
    if (numbers1Sum > numbers2Sum)
        Console.WriteLine("сумма чисел из массива numbers1 больше");
    else if (numbers1Sum < numbers2Sum)
        Console.WriteLine("сумма чисел из массива numbers2 больше");
    else
        Console.WriteLine("суммы чисел обоих массивов равны");
 
    int Sum(int[] numbers)
    {
        int result = 0;
        foreach (int number in numbers)
            result += number;
        return result;
    }
}
```

## Кортеж
возвращает несколько значений
```Csharp
public (string, int) GetFruit()
{
    return ("apples", 5);
}
(string, int) fruit = bob.GetFruit();
WriteLine($"{fruit.Item1}, {fruit.Item2} there are.");

```
или

```Csharp
public (string Name, int Number) GetNamedFruit()
{
    return (Name: "apples", Number: 5);
}
```

```Csharp
var things1 = ("Neville", 4);
```

Деконструкция кортежа
```Csharp
(string fruitName, int fruitNumber) = bob.GetFruit();
WriteLine($"{fruitName}, {fruitNumber} there are.");

```

## Деконструкторы

```Csharp
public void Deconstruct(out string name, out DateTime dob)
{
    name = Name;
    dob = DateOfBirth;
}
```


## переопределение операторов

```Csharp
public static Person operator *(Person p1, Person p2)
{
    return Person.Procreate(p1,p2)
}
Person baby2 = Person.Procreate(harry, jill);
Person baby3 = harry * mary;
```


## Делегаты

делегаты используются для косвенного вызова метода
* делегаты можно использовать для создания очереди вызова методов
* паралельное выполнение нескольких действий
* делегаты позволяют реализовать события для отправки сообщений между различными объектами, которые не должны знать друг о друге

методы добавляются и удаляются из делегата с помощью += или -=
Определение
```csharp
public delegate void EventHandler(object? sender, EventArgs e);
public delegate void EventHandler<TEventArgs>(object? sender, TEventArgs e);
```

## события

определение
```Csharp
public event EventHandler? Shout;
```