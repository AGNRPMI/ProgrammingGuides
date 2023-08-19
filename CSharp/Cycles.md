## Циклы
допускаются вложенные циклы
* for ([действия_до_выполнения_цикла]; [условие]; [действия_после_выполнения])


```csharp
for (int i = 1; i < 4; i++)
{
    Console.WriteLine(i);
    Console.ReadKey(); // итерация цикла производится после нажатия любой клавиши
}
```
* foreach - для перебора набора или коллекции элементов

```csharp
foreach(char c in "Tom")
{
    Console.WriteLine(c);
    Console.ReadKey(); // итерация цикла производится после нажатия любой клавиши
}
```
* while - сначала условие, потом действие

```csharp
int i = 6;
while (i > 0)
{
    Console.WriteLine(i);
    i--;
    Console.ReadKey(); // итерация цикла производится после нажатия любой клавиши
}
```
* do...while - сначал набор действий, потом условие

```csharp
int i = 6;
do
{
    Console.WriteLine(i);
    i--;
    Console.ReadKey(); // итерация цикла производится после нажатия любой клавиши
}
while (i > 0);
```

---

## Операторы Continue и break

continue - пропускает итераию цикла при совпадении условий (в примере 5 не выводится)
```csharp
for (int i = 0; i < 9; i++)
{
    if (i == 5)
        continue;
    Console.WriteLine(i);
}
```


break - при совпадении условия цикл прерывается
```csharp
for (int i = 0; i < 9; i++)
{
    if (i == 5)
        break;
    Console.WriteLine(i);
}
```

Консольная программа в цикле
```csharp
class Program
{
    static void Main(string[] args)
    {
        for (int i=0; i<100; i++)
        {
            string msg = Console.ReadLine();
            if (msg == "exit")
            {
                break;
            }
            Console.WriteLine(i);
        }
        Console.ReadLine();
    }
}
```


