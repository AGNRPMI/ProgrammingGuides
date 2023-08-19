## Коллекции

```csharp
using System.Collection.Generic;
public List<Person> Children = new List<Person>();
```

List<T> - дженерики - сильно типизированная коллекция


если тип-дженерик имеет один определяемый тип, то он должен называться T, например List<T>, где Т - тип, хранящийся в списке
если несколько типов, то Т используется как префикс, например Dictionary<TKey, TValue>

дженерик коллекция поиска
```Csharp
Dictionary<int, string> lookupIntString = new();
lookupIntString.Add(key: 1, value: "Alpha");
lookupIntString.Add(key: 2, value: "Beta");
key = 2;
WriteLine(format: "Key {0} has value: {1}",
arg0: key,
arg1: lookupIntString[key]);
```


