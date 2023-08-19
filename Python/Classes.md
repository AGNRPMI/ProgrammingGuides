## Классы и объекты

```Python
class название_класса:
    атрибуты_класса
    методы_класса
```


оператор pass - пропуск описания класса

```Python
class Person:
    pass
```

После определения класса Person создаются два объекта класса Person - tom и bob. Для создания объекта применяется специальная функция - конструктор, которая называется по имени класса и которая возвращает объект класса. То есть в данном случае вызов Person() представляет вызов конструктора. Каждый класс по умолчанию имеет конструктор без параметров:
```Python
class Person:
    pass
 
tom = Person()      # определение объекта tom
bob = Person()      # определение объекта bob
```

## методы класс

```Python
class Person:       # определение класса Person
     def say_hello(self):   # self - указание, что метод должен принимать в качестве первого параметра ссылку на текущий объект
        print("Hello")
 
tom = Person()
tom.say_hello()    # Hello
```

```Python
class Person:
 
    def say(self, message):
        print(message)
 
    def say_hello(self):
        self.say("Hello work")  # обращаемся к выше определенному методу say
 
 
tom = Person()
tom.say_hello()     # Hello work
```

## конструктор

```Python
class Person:
    
    def __init__(self): # конструктор
        print("Создание объекта Person")
 
    def say_hello(self):
        print("Hello")
         
         
tom = Person()      # Создание объекта Person
tom.say_hello()     # Hello
```

## инкапсуляция
исходник
```Python
class Person:
    def __init__(self, name):
        self.name = name    # устанавливаем имя
        self.age = 1        # устанавливаем возраст
                 
    def display_info(self):
        print(f"Имя: {self.name}\tВозраст: {self.age}")
         
 
tom = Person("Tom")
tom.name = "Человек-паук"       # изменяем атрибут name
tom.age = -129                  # изменяем атрибут age
tom.display_info()              # Имя: Человек-паук     Возраст: -129
```
инкпсуляция
```Python
class Person:
    def __init__(self, name):
        self.__name = name  # устанавливаем имя
        self.__age = 1  # устанавливаем возраст
 
    def set_age(self, age):
        if 1 < age < 110:
            self.__age = age
        else:
            print("Недопустимый возраст")
 
    def get_age(self):
        return self.__age
 
    def get_name(self):
        return self.__name
 
    def display_info(self):
        print(f"Имя: {self.__name}\tВозраст: {self.__age}")
 
 
tom = Person("Tom")
tom.display_info()  # Имя: Tom  Возраст: 1
tom.set_age(-3486)  # Недопустимый возраст
tom.set_age(25)
tom.display_info()  # Имя: Tom  Возраст: 25
```

## аннотации
Для создания свойства-геттера над свойством ставится аннотация @property.

Для создания свойства-сеттера над свойством устанавливается аннотация имя_свойства_геттера.setter.
```Python
class Person:
    def __init__(self, name):
        self.__name = name  # устанавливаем имя
        self.__age = 1  # устанавливаем возраст
 
    @property
    def age(self):
        return self.__age
 
    @age.setter
    def age(self, age):
        if 1 < age < 110:
            self.__age = age
        else:
            print("Недопустимый возраст")
 
    @property
    def name(self):
        return self.__name
 
    def display_info(self):
        print(f"Имя: {self.__name}\tВозраст: {self.__age}")
 
 
tom = Person("Tom")
 
tom.display_info()  # Имя: Tom  Возраст: 1
tom.age = -3486  # Недопустимый возраст
print(tom.age)  # 1
tom.age = 36
tom.display_info()  # Имя: Tom  Возраст: 36
```

## наследование
Наследование позволяет создавать новый класс на основе уже существующего класса. Наряду с инкапсуляцией наследование является одним из краеугольных камней объектно-ориентированного программирования.

Ключевыми понятиями наследования являются подкласс и суперкласс. Подкласс наследует от суперкласса все публичные атрибуты и методы. Суперкласс еще называется базовым (base class) или родительским (parent class), а подкласс - производным (derived class) или дочерним (child class).
```Python
class подкласс (суперкласс):
    методы_подкласса
```
```Python
class Person:
 
    def __init__(self, name):
        self.__name = name   # имя человека
 
    @property
    def name(self):
        return self.__name
 
    def display_info(self):
        print(f"Name: {self.__name} ")
 
 
class Employee(Person):
 
    def work(self):
        print(f"{self.name} works")
 
 
tom = Employee("Tom")
print(tom.name)     # Tom
tom.display_info()  # Name: Tom 
tom.work()          # Tom works
```

множественное наследование
```Python
#  класс работника
class Employee:
    def work(self):
        print("Employee works")
 
 
#  класс студента
class Student:
    def study(self):
        print("Student studies")
 
 
class WorkingStudent(Employee, Student):        # Наследование от классов Employee и Student
    pass
 
 
# класс работающего студента
tom = WorkingStudent()
tom.work()      # Employee works
tom.study()     # Student studies
```

## полиморфизм

```Python
class Person:
 
    def __init__(self, name):
        self.__name = name   # имя человека
 
    @property
    def name(self):
        return self.__name
 
    def display_info(self):
        print(f"Name: {self.__name}")
 
 
class Employee(Person):
 
    def __init__(self, name, company):
        super().__init__(name)
        self.company = company
 
    def display_info(self):
        super().display_info()
        print(f"Company: {self.company}")
 
    def work(self):
        print(f"{self.name} works")
 
 
tom = Employee("Tom", "Microsoft")
tom.display_info()  # Name: Tom
                    # Company: Microsoft
```

## проверка типа объекта
isinstance(object, type)
```Python
class Person:
 
    def __init__(self, name):
        self.__name = name   # имя человека
 
    @property
    def name(self):
        return self.__name
 
    def do_nothing(self):
        print(f"{self.name} does nothing")
 
 
#  класс работника
class Employee(Person):
 
    def work(self):
        print(f"{self.name} works")
 
 
#  класс студента
class Student(Person):
 
    def study(self):
        print(f"{self.name} studies")
 
 
def act(person):
    if isinstance(person, Student):
        person.study()
    elif isinstance(person, Employee):
        person.work()
    elif isinstance(person, Person):
        person.do_nothing()
 
 
tom = Employee("Tom")
bob = Student("Bob")
sam = Person("Sam")
 
act(tom)    # Tom works
act(bob)    # Bob studies
act(sam)    # Sam does nothing
```



## Атрибуты класса
- это переменная определенная на уровне класса
```Python
class Person:
     type = "Person"
     description = "Describes a person"
 
 
print(Person.type)          # Person
print(Person.description)   # Describes a person
 
Person.type = "Class Person"
print(Person.type)          # Class Person
```

## статические методы
- это методы, поведение которых не зависит от конкретного объекта
@staticmethod
```Python
class Person:
    __type = "Person"
 
    @staticmethod
    def print_type():
        print(Person.__type)
 
 
Person.print_type()     # Person - обращение к статическому методу через имя класса
 
tom = Person()
tom.print_type()     # Person - обращение к статическому методу через имя объекта
```






































