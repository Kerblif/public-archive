---
title: Лекция 5. Структурное программирование. Статические методы.
description: 
published: true
date: 2023-11-17T20:56:04.894Z
tags: 
editor: markdown
dateCreated: 2023-11-17T20:56:04.193Z
---

# Лекция 5. Структурное программирование. Статические методы.

```cs
// Примеры:
static void MethId1()
{
}

static int MethId2()
{
	return 1;
}

static int MethId3(int x)
{
	return x++;
}

static void MethId4(int x)
{

}
```

## Локальные переменные

```cs
static void Main(string[] args)
{
  string str = "Default value"; // Лок. переменная с инициализацией.
  int x; // Лок. переменная без инициализации.
  
  Console.WriteLine(str); // Так можно.
  Console.WriteLine(x); // А так нельзя, переменная не инициализирована.
  Console.WriteLine(StrValConcat(str, x = 15)); // Так можно, но не нужно.
  Console.WriteLine(x);
}

static string StrValConcat(string s, int a)
{
  string str = "In method StrValConcat::";
  return str + s + a;
}
```

## Лямбда-операция в методе

```cs
static long AddValues(int a, int b)
{
	return a + b;
}
```

```cs
static long AddValues(int a, int b) => a + b;
```

## Параметры и аргументы

```cs
static double SumSquare(double l, double r)
{
	return (l + r) * (l + r);
}

double x = 1, y = 5;
double z = SumSquare(x, y);
Console.WriteLine(z);
Console.WriteLine(SumSquare(4, 2));
Console.WriteLine(SumSquare(Math.PI, 1));
```

## Именованные аргументы

При вызове метода допустимы именованные аргументы [named arguments], их использование освобождает программиста от соблюдения требования о порядке следования аргументов

```cs
string str = "123";
int val;
int.TryParse(result: out val, s: str);
Console.Write(val)
```

```cs
static int Sum(int a, int b, int c) => a + b + c;

Sum(b: 4, c: 1, a: 3); // Все аргументы именованные.
Sum(a: 4, b: 2, 0); // Аргументы именуются в корректном порядке.
Sum(a: 6, 4, c: 2); // Именованные аргументы идут не подряд, порядок корректный.
Sum(b: 2, a: 1, 5); // Ошибка компиляции, b не на своём месте.
```

## Повышение читаемости кода

```cs
class DemoProgramNamedArguments
{
  static double Volume(double radius, double height) => Math.PI * radius * radius * height;
  static void Main()
	{
 		// При чтении непонятны аргументы.
		Console.WriteLine($"Volume 1: {Volume(3.0, 4.0):F3}");
    
		// Из имён проще догадаться, что это какая-то фигура вращения.
		Console.WriteLine($"Volume 2 (named): " +	
		$"{Volume(radius: 4.0, height: 5.0):F3}");
	}
}
```

## Умалчиваемые значения параметров
```cs
static string StrForLabel(string output = "no values...")
{
	return "Here:: " + output;
}
```

## Необязательные параметры
> Если есть необязательные, то должны быть и обязательные аргументы...
> но компилироваться и запускаться будет. Просто такое соглашение.
{.is-warning}


```cs
static string StrForLabel(int t, string str = "no values...")
{
	string output = "";
	for (int i = 0; i < t; i++)
	{
		output += str;
	}
	return "Here:: " + output;
}

Console.WriteLine(StrForLabel(3));
Console.WriteLine(StrForLabel(2, "Something"));
```

## default

Оператор default возвращает значение по умолчанию, полученное по аргументу.
Литерал default используется в выражениях для формирования значения по умолчанию.

```cs
// здесь значение по умолчанию - null.
static string StrForLabel(int t, string? str = default)
{
  string output = "";
  for (int i = 0; i < t; i++)
  {
    output += str;
  }
  return "Here:: " + output;
}
```

# Передача параметров.

## Передача значений
```cs
static void Swap (int x, int y)
{
  x += y;
  y = x - y;
  x -= y;
}

int a = 6, b = 7;
Console.WriteLine($"a={a} b={b}");
Swap(a, b);
Console.WriteLine($"a={a} b={b}");
// Output:
// a=6 b=7
// a=6 b=7
```

## Передача ссылок

```cs
static void Swap (ref int x, ref int y)
{
  x += y;
  y = x - y;
  x -= y;
}


int a = 6, b = 7;
Console.WriteLine($"a={a} b={b}");
Swap(ref a, ref b);
Console.WriteLine($"a={a} b={b}");
// Output:
// a=6 b=7
// a=7 b=6
```

## Возврат значения по ссылке

```cs
static ref int DblInc(ref int a, int b)
{
  a = ++a + ++b;
  return ref a;
}
```

## Ссылочные переменные
```cs
int x = 0;
ref int b = ref x;
Console.WriteLine(x);
b++;
Console.WriteLine(x);
// Output:
// 0
// 1
```

