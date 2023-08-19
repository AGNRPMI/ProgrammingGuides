## Массивы

тип_переменной[] название_массива;
```csharp
int[] numbers; // обявление массива

int[] nums = new int[4]; // 4 - колво элементов массива

int[] nums3 = new int[] { 1, 2, 3, 5 }; // присвоение значений элементам массива
```
```csharp
int[] nums1 = new int[] { 0, 1, 2, 3, 4, 5 }; // одномерный массив
 
int[,] nums2 = { { 0, 1, 2 }, { 3, 4, 5 } };// двумерный массив

int[][] numbers = { 
    new int[] { 1, 2 }, 
    new int[] { 1, 2, 3 }, 
    new int[] { 1, 2, 3, 4, 5 } 
}; // зубчатый массив
```
Свойства:
* Ранг (rank): количество измерений массива
* Длина измерения (dimension length): длина отдельного измерения массива
* Длина массива (array length): количество всех элементов массива


индексы и получение элементов массива
```csharp
int[] numbers = { 1, 2, 3, 5 };
numbers[1] = 505; // изменим второй элемент массива
Console.WriteLine(numbers[1]);  // 505
```
Длина массива
```csharp
int[] numbers = { 1, 2, 3, 5 };
Console.WriteLine(numbers.Length);  // 4
```

перебор массива
```csharp
int[] numbers = { 1, 2, 3, 4, 5 };
foreach (int i in numbers) // перебор по порядку
{
    Console.WriteLine(i);
}

или

int[] numbers = { 1, 2, 3, 4, 5 };
for (int i = 0; i < numbers.Length; i++) // перебор по приращению счетчика
{
    Console.WriteLine(numbers[i]);
}
```



Инверсия массива
```csharp
int[] numbers = { -4, -3, -2, -1,0, 1, 2, 3, 4 };
             
int n = numbers.Length; // длина массива
int k = n / 2;          // середина массива
int temp;               // вспомогательный элемент для обмена значениями
for(int i=0; i < k; i++)
{
    temp = numbers[i];
    numbers[i] = numbers[n - i - 1];
    numbers[n - i - 1] = temp;
}
foreach(int i in numbers)
{
    Console.Write($"{i} \t");
}
```

сортировка массива
```csharp
int[] nums = { 54, 7, -41, 2, 4, 2, 89, 33, -5, 12 };
 
// сортировка
int temp;
for (int i = 0; i < nums.Length - 1; i++)
{
    for (int j = i + 1; j < nums.Length; j++)
    {
        if (nums[i] > nums[j])
        {
            temp = nums[i];
            nums[i] = nums[j];
            nums[j] = temp;
        }
    }
}
 
// вывод
Console.WriteLine("Вывод отсортированного массива");
for (int i = 0; i < nums.Length; i++)
{
    Console.WriteLine(nums[i]);
}
```

поиск в массиве
```csharp
int[] nums = { 54, 7, -41, 2, 4, 2, 89, 33, -5, 12 };
int n = nums.Length;
int find = -5;
while (index < n)
{
    if (nums[index]==find) Console.WriteLine ($"{index} = {find}") 
    index++; 
}
```