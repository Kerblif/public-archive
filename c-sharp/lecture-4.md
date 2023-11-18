---
title: Лекция 4. Алгоритмические структуры.
description: 
published: true
date: 2023-11-17T20:56:03.879Z
tags: 
editor: markdown
dateCreated: 2023-11-17T20:56:03.186Z
---

# Лекция 4. Алгоритмические структуры.

## Линейный алгоритм

```cs
Console.Write("Enter a number: ");
double x = double.Parse(Console.ReadLine());
Console.WriteLine($"{x:f3}");
```
```cs
Console.Write("Enter first number: ");
int x = int.Parse(Console.ReadLine());

Console.Write("Enter second number: ");
int y = int.Parse(Console.ReadLine());

Console.WriteLine();
Console.Write(x > y ? "First is greater": "Second is greater") ;
```

## Разветляющийся алгоритм

```cs
// Полная форма ветвления
if (логическое_выражение)
{
	// блок операторов 1
}
else
{
	// блок операторов 2
}
// блок операторов после
```

```cs
// Неполная форма ветвления
if (логическое_выражение)
{
	// блок операторов 1
}
```

## Вложенные операторы ветвления

```cs
int x, y;
Console.Write("Enter first number: ");

if (!int.TryParse(Console.ReadLine(), out x))
{
	Console.Write("Invalid first number!");
	return;
}
else
{
	Console.Write("Enter second number: ");
	if (!int.TryParse(Console.ReadLine(), out y))
	{
		Console.Write("Invalid second number!");
		return;
	}	
	else
	{
		Console.WriteLine();
		Console.Write(x > y ? "First is greater" : "Second is greater");
	}
}
```

## Культура кодирования

```cs
// Неправильно
int a = 10, b = 22;

if (a > 5)
	Console.WriteLine(b / 2);
Console.Write(b % 2);
```

```cs
// Правильно
int a = 10, b = 22;

if (a > 5)
{
	Console.WriteLine(b / 2);
}
Console.Write(b % 2);
```

---
Сравнение c true/false в if

```cs
// Неправильно
int op;

if(int.TryParse(Console.ReadLine(), out op)==true)
{
	Console.Write(++op);
}
else
{
	Console.Write("Not a number!");
}
```

```cs
// Правильно
int op;

if(int.TryParse(Console.ReadLine(),out op))
{
	Console.Write(++op);
}
else
{
	Console.Write("Not a number!");
}
```

## Множественный выбор

```cs
switch (Выражение)
{
 case label1: /* блок операторов 1 */ break;
 case label2: /* блок операторов 2 */ break;
 case label3: /* блок операторов 3 */ break;
…
 default: break;
}
```

```cs
<выражение> switch {
  шаблон1 [охранное условие] => выражение1,
  шаблон2 [охранное условие] => выражение2,
  …
  шаблонN [охранное условие] => выражениеN,
  _ => выражение
};
```

```cs
string output = day switch
{
	<= 5 => "Workday",
	6 or 7 => "Weekend",
	_ => "Invalid number of a day"
}
```

```cs
switch(formNumber)
{
  case 1:
  case 2:
  case 3: Console.WriteLine("Less or equal to 3"); break;
  case 4:
  case 5:
  case 6: Console.WriteLine("More then 3 but less or equal to 7"); break;
}
```

## Цикл с постусловием

```cs
do
{
	// Тело цикла
}
while (Выражение);
```

## Цикл с предусловием
```cs
while (Выражение)
{
	// тело цикла
}
```

## Цикл for
```cs
for (инициатор счётчика; условие продолжения; изменение счётчика)
{
	// Блок операторов
	// тела цикла
}
```

## Оператор break
Завершает (полностью) выполнение ближайшего оператора цикла и передаёт управление оператору, расположенному после цикла
```cs
for (int i = 0; i < 10; i++)
{
	if (i > 5)
	{
		break;
	}
	Console.Write($"{i} ");
}
Console.WriteLine("Hello outside the for!!!");
```

## Оператор continue
Начинает новую итерацию ближайшего оператора цикла и передаёт управление оператору, расположенному после цикла

```cs
for (int i = 0; i < 10; i++)
{
	if (i % 2 == 0)
	{
		continue;
	}
	Console.Write($"{i} ");
}
Console.WriteLine("Hello outside the for!!!");
```