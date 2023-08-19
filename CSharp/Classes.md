## Классы

```csharp
class название_класса
{
    // содержимое класса
}
```

Класс может хранить некоторые данные. Для хранения данных в классе применяются поля. По сути поля класса - это переменные, определенные на уровне класса.
Кроме того, класс может определять некоторое поведение или выполняемые действия. Для определения поведения в классе применяются методы.
```csharp
class Person 
{
    public string name = "Undefined";   // поле имя
    public int age;                     // поле возраст
 
    public void Print() // метод класса
    {
        Console.WriteLine($"Имя: {name}  Возраст: {age}");
    }
}
```


## обращение к функционалу класса

```csharp
объект.поле_класса
объект.метод_класса(параметры_метода)
```

Обычно классы помещаются в отдельные файлы. Нередко для одного класса предназначен один файл. Если мы работаем над проектом вне среды Visual Studio, используя .NET CLI, то нам достаточно добавить новый файл класса в папку проекта.


## создание конструкторов

```csharp
Person tom = new Person();          // вызов 1-ого конструктора без параметров
Person bob = new Person("Bob");     //вызов 2-ого конструктора с одним параметром
Person sam = new Person("Sam", 25); // вызов 3-его конструктора с двумя параметрами
 
tom.Print();          // Имя: Неизвестно  Возраст: 18
bob.Print();          // Имя: Bob  Возраст: 18
sam.Print();          // Имя: Sam  Возраст: 25
 
class Person 
{
    public string name;
    public int age;
    public Person() { name = "Неизвестно"; age = 18; }      // 1 конструктор
    public Person(string n) { name = n; age = 18; }         // 2 конструктор
    public Person(string n, int a) { name = n; age = a; }   // 3 конструктор
 
    public void Print()
    {
        Console.WriteLine($"Имя: {name}  Возраст: {age}");
    }
}
```


## Ключевое слово this

Ключевое слово this представляет ссылку на текущий экземпляр/объект класса. 

```csharp
Person sam = new("Sam", 25); 
sam.Print();          // Имя: Sam  Возраст: 25
 
class Person 
{
    public string name;
    public int age;
    public Person() { name = "Неизвестно"; age = 18; }
    public Person(string name) { this.name = name; age = 18; }
    public Person(string name, int age) 
    { 
        this.name = name; 
        this.age = age; 
    }
    public void Print() => Console.WriteLine($"Имя: {name}  Возраст: {age}");
}
```


## Инициализаторы

- С помощью инициализатора мы можем установить значения только доступных из вне класса полей и свойств объекта. Например, в примере выше поля name и age имеют модификатор доступа public, поэтому они доступны из любой части программы.
- Инициализатор выполняется после конструктора, поэтому если и в конструкторе, и в инициализаторе устанавливаются значения одних и тех же полей и свойств, то значения, устанавливаемые в конструкторе, заменяются значениями из инициализатора.

```csharp
Person tom = new Person{ name = "Tom", company = { title = "Microsoft"} }; // Инициализатор
tom.Print();          // Имя: Tom  Компания: Microsoft
 
class Person
{
    public string name;
    public Company company;
    public Person() 
    { 
        name = "Undefined";
        company = new Company();
    }
    public void Print() => Console.WriteLine($"Имя: {name}  Компания: {company.title}");
}
 
class Company
{
    public string title = "Unknown";
}
```

## Структуры
Наряду с классами структуры представляют еще один способ создания собственных типов данных в C#. Более того многие примитивные типы, например, int, double и т.д., по сути являются структурами.
```csharp
struct имя_структуры
{
    // элементы структуры
}
```
```csharp
struct Person
{
    public string name;
    public int age;
 
    public void Print()
    {
        Console.WriteLine($"Имя: {name}  Возраст: {age}");
    }
}
```
Если нам необходимо скопировать в один объект структуры значения из другого с небольшими изменениями, то мы можем использовать оператор with:
```csharp
Person tom = new Person { name = "Tom", age = 22 };
Person bob = tom with { name = "Bob" };
bob.Print();    // Имя: Bob  Возраст: 22
```



## записи

ключевое слово record вместо class
это делает весь объект неизменным, пожтому он работает как значение при сравнении. записи не должны содеражать состояние (свойства и поля), которое изменяется после того как экземпляр создан. вместо этотго создаются новые записи из существующих с любым измененным состоянием, используя ключевое слово with
```Csharp
public record ImmutableVehicle
{
    public int Wheels {get; init;}
    public string? Color {get; init;}
}
ImmutabelVehiclr repainedCar = car
    with {Color = "dark grey"};
```

## наследование

```Csharp
public class Employee : Person {}
```

## переопределение
с помощью ключевого слова virtual, означает, что метод с тем же названием будет работать по другому
```Csharp

```

ключевое слово abstract означает, что класс не может быть создан, класс не реализован

ключевое слово sealed означает запрет наследования


## полиморфизм

new - неполиморфное наследование
переопределение - полиморфное наследование
ключевое слово base - вызов базового класса или суперкласса

## Обработка исключений приведения
явное приведение is
as - вернет null если не удасться привести
```Csharp
if (aliceInPerson is Employee explicitAlice)
{}
Emloyee? aliceAsEmployee = aliceInPerson as Employee;
if (aliceAsEmployee != null) {}
```
