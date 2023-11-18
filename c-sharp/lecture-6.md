---
title: Лекция 6. Перегрузка методов.
description: 
published: true
date: 2023-11-17T20:56:05.918Z
tags: 
editor: markdown
dateCreated: 2023-11-17T20:56:05.208Z
---

# Лекция 6. Перегрузка методов.

## Модификатор ref

Параметр, отмеченный ref, указывает, что операции в выполняются непосредственно с аргументом (не с его копией).
Значение аргумента может **(но не обязано)** быть изменено в теле метода.

Передача неинициализированной переменной вызывает ошибку компиляции.

## Модификатор in

Параметр, отмеченный in, указывает, что в операциях участвует непосредственно аргумент (не его копия), но изменить значение аргумента в методе **нельзя**.

Для констант и вызовов методов in не указывают.
Передача неинициализированной переменной вызывает ошибку компиляции.

## Модификатор out

Параметр, отмеченный out, указывает, что в операциях участвует непосредственно аргумент (не его копия), и аргумент в методе **должен получить значение (обязательно!)**

При вызове у аргумента out нет обязательств по инициализированности.

## Модификатор params

params – модификатор параметров метода, позволяющий передать переменное число аргументов

```cs
static string MultStr(int n = 0, params string[] str)
{
	string output = "";

	for(int i = 0; i < n; i++)
	{
		output += str[i];
	}
  return output;
}

string[] test = { "Bar", "Foo", "13" };
Console.WriteLine(MultStr(2, test));
Console.WriteLine(MultStr(3, "a", "bc", "def", "ghij", "klmno"));
Console.WriteLine(MultStr());
```

![порядок_параметров.png](/порядок_параметров.png)

| Модификатор | Нужен при вызове? | Что может быть аргументом | Особенности |
| --- | --- | --- | --- |
| <пусто> | – | Всё кроме неинициализированных переменных. | Передача по значению. |
| ref | да | Поля и инициализированные локальные переменные. | Передача по ссылке, допустимы изменения. |
| out | да | Поля и любые локальные переменные. | Передача по ссылке, требуется инициализация.
| in | не всегда, иногда недопустим | Всё кроме неинициализированных переменных. | Передача по ссылке (для инициализированных переменных и полей) и по значению для всего остального, изменения запрещены. |
| params | нет | Одномерный массив или последовательность значений, приводимых к указанному типу. | Передача по значению. Позволяет явно передать массив или сформировать его из набора аргументов, перечисленных через запятую. |

## Ошибочные заголовки

```cs
// DateTime.Now - значение этапа выполнения.
static void Meth1(DateTime dt = DateTime.Now) { }
// MyClass - не struct или enum.
static void Meth2(MyClass mc = new MyClass()) { }
// params не может иметь значения по умолчанию.
static void Meth3(params int[] data = null) { }
// Параметры c модификаторами ref и out не могут быть опциональными.
static void Meth4(ref string result = "Источник") { }
// Аргументам по умолчанию нельзя передавать значения при создании.
static void Meth5(DateTime dt = new DateTime(2021, 9, 19)) { }
```

## Перегрузка методов
```cs
static void Swap(ref double x, ref double y)
{
	double tmp;
  
	tmp = x;
	x = y;
	y = tmp;
}
static void Swap(ref int x, ref int y)
{
	int tmp;
  
	tmp = x;
	x = y;
	y = tmp;
}
```

```cs
// Возникает ошибка

static void Swap (out double x, ref double y)
{
  double tmp;
  tmp = x;
  x = y;
  y = tmp;
}

static void Swap (ref double x, ref double y)
{
  double tmp;
  tmp = x;
  x = y;
  y = tmp;
}

```

```cs
// А тут все ок

static void Swap (ref double x, ref double y)
{
  double tmp;
  tmp = x;
  x = y;
  y = tmp;
}

static void Swap (double x, double y)
{
  double tmp;
  tmp = x;
  x = y;
  y = tmp;
}

```

 ## Локальные функции
 
 ```cs
 static void Main(string[] args)
{
  string str = "Default value"; // Лок. переменная с инициализацией.
  int x; // Лок. переменная без инициализации.
  Console.WriteLine(str); // Так можно.
  // Console.WriteLine(x); // А так нельзя, переменная не инициализирована.
  Console.WriteLine(StrValConcat(str, x = 15));
  Console.WriteLine(x);
  
  static string StrValConcat(string s, int a)
  {
    string str = "In method StrValConcat::";
    // StrValConcat() – имеет доступ к локальным переменным Main()
    return str + s + a + x;
  }
}
 ```
 
 ## Статические классы
* Нельзя создавать экземпляры статического класса
* Содержит только статические методы
* Позволяет обращаться к своим членам через имя класса
* Не содержит экземплярных конструкторов
* Не может быть унаследован

## Константы
```cs
class Program
{
	// Константы доступны по имени типа.
	const int ten = 10;
	static void Main()
	{
		const double PI = 3.1415; // локальная константа.
		System.Console.WriteLine($"PI * ten = {PI * ten}");
	}
}
```

## Статический конструктор
> 
> Статический конструктор – специальный функциональный член класса, вызывающийся автоматически при первом обращении к типу сразу после инициализации всех статических полей.
{.is-info}

```cs
using System;
class MyClass {
	// num инициализируется перед вызовом статического конструктора.
	static int num = 42;
	static MyClass() { // Статический конструктор: static <Имя Типа>.
    Console.WriteLine($"The answer is... {num}!");	
    Console.WriteLine($"Starting time: {DateTime.Now}");
  }
}
```

## Модификаторы доступа
* private – закрытый (доступ только внутри типа)
* public – открытый (доступ без ограничений)
* protected – защищенный (доступ только для наследников)
* internal – внутренний (доступ внутри той же сборки)
* protected internal – внутри сборки ИЛИ для всех наследников
* private protected – только для наследников внутри той же сборки (C# 7.2)

## Статические поля
```cs
class MyClass {
  // По умолчанию private
  static long num = 13;
  public static void Print(int u) {
    long prod = u * num;
    System.Console.WriteLine("u * numb = " + prod);
  }
}
class Program {
  static void Main() {
  	MyClass.Print(3); // Обращение к Print по имени типа.
  }
}
```