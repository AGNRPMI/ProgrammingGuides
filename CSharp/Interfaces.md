## универсальные интерфейсы

|Интерфейс|Методы|Описание|
|----|----|-----|
|IComparable|CompareTo(other)|опередялет метод сравнеинчя, который тип реализует для упорядочивания ли сортирвоки элементов|
|IComparer|Compare(first, second)|определяет метод сравнения, котоырй вторичный тип реализует для упорядочивания или сортировки экземпляров вторичного типа|
|IDisposable|Dispose()|определяет метод, позволяющий освобождать неууправляемые ресурсы более эффективно, чем ожидание финализатора|
|IFormattable|ToString(formate, culture)|определяет методы поддерживающие региональные параметры, ля форматирвоания значения обхекта в стркоовое представление|
|IFormatter|Serialize(stream, object) и Deserialize(stream)|определяет методы преобразования объекта в поток байтов и из него для хранения или передачи|
|IFormatProvider|GetFormat(type)|определяет метод для форматирвоания ввода на основе настроек языка и региона|


```Csharp
public interface IGamePlayer
{
    void Lose();
}
public interface IKeyHolder
{
    void Lose();
}
public class Person : IGamePlayer, IKeyHolder
{
    public void Lose() //неявная реализация
    {
        //реализация потери ключа
    }
    void IGamePlayer.Lose()//явная реализация
    {
        //реализаця потери игры
    }
}
Person p = new();
p.Lose();
((IGamePlayer)p).Lose();
IgamePlayer player = p as IGamePlayer;
player.Lose();

```