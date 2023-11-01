---
title: Лекция 7. Массивы.
description: 
published: true
date: 2023-10-23T21:51:41.501Z
tags: 
editor: markdown
dateCreated: 2023-10-23T20:32:44.058Z
---

# Лекция 7. Массивы.

> ***Массив*** [array] – последовательность однотипных элементов, к каждому
> из которых можно получить доступ по его индексу за константное время
> (примерно одинаковое время, не зависящее от значения индекса).
{.is-info}

> ***Индекс*** [index] – порядковый номер элемента. Индекс сам по себе не
> является информационным элементом!
{.is-info}

Нужно знать о массивах:
1. базовая структура данных с индексацией
2. представляет собой непрерывный участок памяти
3. идентифицируется адресом первого элемента

```c#
// Описание ссылки на массив.
int[] ar = new int[2]; // Инициализация массива.

ar[0] = 15; // Присваивание значения.
ar[1] = 22;

Console.Write(ar[1]); // Получение значения по индексу.
```

Массивы бывают:
* одномерными
* многомерными
* массивом массивов

## Одномерные массивы

> ***Одномерный массив*** – набор однотипных элементов, доступ к которым
> осуществляется с помощью выражения с операцией индексирования
{.is-info}


> ***Элементы массива*** [Elements, items] – отдельные единицы данных
> массива
{.is-info}

### Создание одномерного массива

```cs
// Создание массива длинной 25 типа double.
new double[25];

// Создание массива длинной 5 типа int.
new int[5];
```

```cs
// Описание ссылки ar на одномерный массив элементов int.
int[] ar;

// Создание одномерного массива из пяти элементов типа int и назначение ссылки.
ar = new int[5];

for (int i = 0; i < ar.Length; i++)
{
  // Обращение к элементу массива через ссылку ar по индексу i.
	Console.Write($"{ar[i]} ");
}
```

### Размещение массива в памяти
```cs
int[] ar = new int[5];
int[] ar2 = ar;
// ar и ar2 содержат один и тот же указатель.

for (int i = 0; i < ar.Length; i++)
{
	Console.WriteLine($"ar[{i}] = {ar[i]}:: ar[{i}] = {ar2[i]}");
}
```

```cs
int[] ar = new int[5];
int[] ar2 = ar;
// ar и ar2 содержат один и тот же указатель.

for (int i = 0; i < ar.Length; i++)
{
  // Изменение значений элементов массива.
 
	if (i % 2 == 0)
	{
		ar[i] = i;
	}
	else
	{
		ar2[i] = i * i;
	}
}

```

## Инициализация элементов массива

```cs
// Описание с созданием.
int[] ar = new int[5];

// Описание с инициализацией списком (c new).
int[] ar2 = new int[] { -5, 0, 4, 3, 2 };
int[] ar3 = new int [3] {1, 2, 3};
int[] ar4 = new []{1, 2, 3};

// Описание с инициализацией списком (c new и выводом типа).
var ar5 = new[] { 8, 9, 10 };

// Описание с инициализацией списком (без new).
string[] test = { "t1", "t2" }; 
int[] ar6 = { -5, 0, 4, 3, 2 };
int[] ar7 = { (int)Math.Round(3.14), 20 + 5 };
```

```cs
// Можно:
int[] ar2;
ar2 = new int[] { -5, 0, 4, 3, 2 };

int[] ar3 = new[] { 1, 2, 3 };

int[] ar3 = { };

int[] ar3 = new int[]{ };

// Нельзя:
int[] ar2;
ar2 = { -5, 0, 4, 3, 2 };

int[] ar2;
int[] ar3 = new int [3] { 1, 2 };

int[] ar3 = new[] { };

var ar3 = new { 1,2 };
```

### Размеры массива

> ***Размерность*** (Rank) – число измерений массива
{.is-info}


> ***Длина измерения*** (Dimension Length) – число элементов в данном
> измерении массива
{.is-info}


> ***Размер массива*** (Array Length) – общее количество элементов,
> содержащееся во всех измерениях массива
{.is-info}

### Члены класса Array

| Член | Тип члена | static | Краткое описание |
| ---- | -------- | ------ | ---------------- |
| [Length](https://docs.microsoft.com/en-us/dotnet/api/system.array.length?view=net-5.0) | свойство | нет | Количество элементов во всех измерениях массива. |
| [Rank](https://docs.microsoft.com/en-us/dotnet/api/system.array.rank?view=net-5.0) | свойство | нет | Количество измерений массива. |
| [GetLength](https://docs.microsoft.com/en-us/dotnet/api/system.array.getlength?view=net-5.0) | метод | нет | Длина указанного измерения массива. |
| [Clear](https://docs.microsoft.com/en-us/dotnet/api/system.array.clear?view=net-5.0) | метод | да | Заменяет диапазон значений массива значениями типа элемента по умолчанию. |
| [Sort](https://docs.microsoft.com/en-us/dotnet/api/system.array.sort?view=net-5.0) | метод | да | Выполняет сортировку одномерного массива. |
| [BinarySearch](https://docs.microsoft.com/en-us/dotnet/api/system.array.binarysearch?view=net-5.0) | метод | да | Выполняет поиск значения в одномерном массиве. |
| [Clone](https://docs.microsoft.com/en-us/dotnet/api/system.array.clone?view=net-5.0) | метод | нет | Выполняет поверхностное копирование массива – копирует только лежащие в массиве значения/ссылки. |

### Методы класса Array

| Член | static | Краткое описание |
| --- | --- | --- |
| [Reverse](https://docs.microsoft.com/en-us/dotnet/api/system.array.resize?view=net-5.0) | да | Разворачивает диапазон элементов массива. |
| [Resize](https://docs.microsoft.com/en-us/dotnet/api/system.array.resize?view=net-5.0) | да | Пересоздаёт массив большего/меньшего размера, содержащий элементы исходного. |
| [IndexOf](https://docs.microsoft.com/en-us/dotnet/api/system.array.indexof?view=net-5.0) | да | Возвращает индекс первого вхождения элемента в массиве или -1 при его отсутствии. |
| [LastIndexOf](https://docs.microsoft.com/en-us/dotnet/api/system.array.lastindexof?view=net-5.0) | да | Возвращает индекс последнего вхождения элемента в массиве или -1 при его отсутствии. |
| [GetLowerBound](https://docs.microsoft.com/en-us/dotnet/api/system.array.getlowerbound?view=net-5.0) | нет | Возвращает индекс первого элемента данного измерения массива. |
| [GetUpperBound](https://docs.microsoft.com/en-us/dotnet/api/system.array.getupperbound?view=net-5.0) | нет | Возвращает индекс последнего элемента данного измерения массива. |
| [CreateInstance](https://docs.microsoft.com/en-us/dotnet/api/system.array.createinstance?view=net-5.0) | да | По указанному типу создаёт массив с заданной нижней границей и размерами. |

### Перебор элементов массива

```cs
int[] ar = new int[5];

// Свойство Length возвращает Int32
// общее количество элементов во
// всех измерениях массива.
for (int i = 0; i < ar.Length; i++)
{
	// Обращаемся по индексу к элементам ar[i].
}

// Метод GetLength() возвращает
// Int32 общее количество
// элементов в указанном в
// параметре измерении массива
for (int i = 0; i < ar.GetLength(0); i++)
{
	// Обращаемcя по индексу к элементам ar[i].
}

// Метод GetUpperBound()возвращает
// Int32 индекс последнего элемента
// заданного в параметре измерения
for (int i = 0; i <= ar.GetUpperBound(0); i++)
{
 // Обращаемcя по индексу к элементам ar[i].
}
```

### Вывод на экран
```cs
int[] ar = new int[5];

// Выполняет действие action с
// каждым элементом
// массива array
Array.ForEach(array: ar, action: Console.Write);

// Блок операторов в теле
// foreach выполнится для всех
// элементов коллекции 
foreach(int i in ar)
{
  // Элемент массива
  // доступен по значению, то
	// есть скопирован в i
	Console.Write(i);
}

// Аналогично предыдущему, но
// используется анонимный тип для cur
foreach (var cur in ar)
{
	Console.Write(cur);
}
```

### Ссылочные типы

* Переменные ссылочных типов содержат ссылки на данные
* Две переменные ссылочного типа могут ссылаться на одни и те же данные

```cs
int[] ar = new int[5];
int[] ar2; // Эта ссылка не проиниализирована.
Console.Write(ar is null ? null : ar); // Можно.
Console.Write(ar2 is null ? null : ar2); // Нельзя.
```

### Операции объединения с null
| Операция | Результат выполнения |
| ---- | ---- |
| $x ?? y$ | Возвращает значение x, если он не null или вычисляет значение y и возвращает его |
| $x ??= y$ | Вычисляет значение y и присваивает его x только в случае, когда x оказался равен null |

```cs
int[] ar = { 1, 2, 3 };
int[] ar2 = null;
int[] ar3 = { 5, 6, 7 };

Console.WriteLine($"ar::");
Array.ForEach(ar, Console.Write);
Console.WriteLine($"{Environment.NewLine}ar3::");
Array.ForEach(ar3, Console.Write);

// Ссылке будет назначено значение, т.к. она null
ar2 ??= ar;
// Ссылка уже связана с массивом (не null), ей не будет назначено значение
ar3 ??= ar;

Console.WriteLine($"{Environment.NewLine}ar2::");
Array.ForEach(ar2, Console.Write);
Console.WriteLine($"{Environment.NewLine}ar3::");
Array.ForEach(ar3, Console.Write);
```

### Возврат массива из метода

```cs
public static class Methods
{
	static Random rnd = new Random();
  
	public static int[] GetIntArray(int n)
	{
		int[] array = n < 0 ? null : new int[n];
		for(int i = 0;i < array?.Length; i++)
		{
			array[i] = rnd.Next();
		}
		return array;
	}
}
```

```cs
int n = -15;
int[] ar = Methods.GetIntArray(n);
Console.Write(ar is null);
```

### Передача массивов в методы
#### Ссылка по значению

```cs
public static class Methods
{
	public static double Mean(double[] ar)
	{
		double mean = 0;
		
    foreach (double d in ar)
    { 
    	mean += d;
    }
    
		return mean / ar.Length;
	}
}
```

```cs
double[] ar = { 1.9, 0.75, 2.55, 15, -8 };
Console.WriteLine(Methods.Mean(ar));
```

#### Ссылка по ссылке

```cs
public static class Methods
{
	static Random rnd = new Random();
	public static void GetIntArray(int n, ref int[] ar = null)
	{
		if (n > 0)
		{
			ar = new int[n];
			for (int i = 0; i < ar?.Length; i++)
			{
				ar[i] = rnd.Next();
			}
		}
	}
}
```

```cs
int[] ar = { 1, 2 };
Methods.GetIntArray(5, ref ar);
for (int i = 0;i < ar.Length;i++)
{
	Console.Write(ar[i]);
}
```

#### Модификатор params
```cs
static int Sum(params int[] elems)
{
	int sum = 0;
	foreach (int elem in elems) {
		sum += elem;
	}
	return sum;
}
```
```cs
int[] arr = { 1, 2, 3, 4, 5 };
int sum3 = Sum(3, 4, 5); // Массив формируется неявно.
int sum5 = Sum(arr); // Массив явно передаётся в метод.
Console.WriteLine($"sum3 = {sum3}; sum5 = {sum5}");
```

