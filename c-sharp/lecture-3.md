---
title: Лекция 3. Операторы и операции.
description: 
published: true
date: 2023-10-25T16:48:49.096Z
tags: 
editor: markdown
dateCreated: 2023-10-24T14:14:26.052Z
---

# Лекция 3. Операторы и операции.

> Фраза [phrase] – любая последовательность символов, являющаяся правильной (валидной), то есть удовлетворяющая синтаксическим и семантическим правилам языка программирования
{.is-info}

```cs
// Фразы
string[] fileData;
Console.WriteLine("Hello, World!");

// Не фразы
string[] 3fileData;
Console.WriteLine("Hello, World!"));
```

## Группы операций

По кол-ву операндов:
* Унарные
* Бинарные
* Тернарная

По типам операндом и цели:
* Арифметические
* Логические 
* Битовые
* Сравнения
* Равенства

## Унарные операции

```cs
int x = +10; // x = 10
Console.Write(x); // Вывод: 10
```

```cs
int x = +10; // x = 10
Console.Write(-x); // Вывод: -10
```

> Для ulong не поддерживается + и -
{.is-warning}

---

```cs
// Префиксный декремент
// Значение переменной изменяется до участия в выражениях

int x = 0; // x = 0;
int y = --x; // x = -1 y = -1
Console.WriteLine(x + y); // x = -1 y = -1
```

```cs
// Постфиксный инкремент
// Значение переменной изменяется после участия в выражениях

int x = 0; // x = 0;
int y = x++; // x = 1 y = 0
Console.WriteLine(x + y); // x = 1 y = 0
```

---

```cs
int a = 1, b = 1, c = 1;
Console.WriteLine($"a+=1 = {a += 1}"); // a+=1 = 2
Console.WriteLine($"++b = {++b}"); // ++b = 2
Console.WriteLine($"c++ = {c++}"); // c++ = 1
```

---

```cs
byte foo = 16;
Console.WriteLine($"{Convert.ToString(foo, 2)}");
Console.WriteLine($"{Convert.ToString(~foo, 2)}");
// Output:
// 10000
// 11111111111111111111111111101111
```

> Поддерживается для int, uint, long, ulong
> Поддерживается (по неявно приводится к int) для sbyte, byte, short, ushort, char
{.is-warning}

---

```cs
bool logical = false;
Console.Write(!logical); // logical = false; output: True
Console.Write(logical); // logical = false; output: False
Console.Write(!true); // output: False
```

## Бинарные операции

### Сложение
```cs
int a = 5, b = 6;
int c = a + b;
```

### Вычитание
```cs
int a = 5, b = 6;
int c = a - b;
```

### Умножение
```cs
int a = 5, b = 6;
int c = a * b;
```

### Деление

> Если оба операнда целочисленные - результат целочисленный.
> Иначе - вещественный
{.is-warning}

### Остаток от деления

> Определен ТОЛЬКО для целочисленных
{.is-warning}

### Битовые операции

* & - Конъюнкция (И)
* | - Дизъюнкция (ИЛИ)
* ^ - Исключающее ИЛИ

```cs
int r = 11, d = 7;
int b = r & d;
Console.Write(b);

// Output: 3
```

```cs
uint a = 0b_1111_1001;
uint b = 0b_1001_1101;
uint c = a & b;
Console.Write(Convert.ToString(c, toBase: 2));

// Output: 10011001
```

* << - сдвиг влево
* \>> - сдвиг влево

> Поддерживается для int, uint, long, ulong
> Поддерживается (по неявно приводится к int) для sbyte, byte, short, ushort, char
{.is-warning}

```cs
uint a = 0b_1111_1001;
Console.WriteLine($"{Convert.ToString(a, 2)}");
uint lShiftA = a << 4;
Console.WriteLine($"{Convert.ToString(lShiftA, 2)}");
```

* Старшие биты за пределами диапазона типа будут отброшены
* Младшие биты заполняются нулями


```cs
int a = -249;
Console.WriteLine($"{Convert.ToString(a, 2)}");
int rShiftA = a >> 2;
Console.WriteLine($"{Convert.ToString(rShiftA, 2)}");
```

* Старшие разряды заполняются знаковым битом
* Младшие биты за пределами диапазон типа будут отброшены

### Логические операции

* && - "ленивое" И
* || - "ленивое" ИЛИ

> ```cs
> true || <хрень, вызывающая ошибку при исполнении>
> false && <хрень, вызывающая ошибку при исполнении>
> ```
> Все выполнится без ошибок.
{.is-warning}

### Операции сравнения
```cs
Console.WriteLine(double.NaN > 15);
Console.WriteLine(float.NaN < double.NaN);
```

> Любое сравнение с NaN выдает false
> <img src="/1694096852952.jpeg" height=300></img>
{.is-warning}

### Эпсилон

Эпсилон вещественного формата задаёт границу неразличимости двух вещественных значений

```cs
double eps = double.Epsilon;
double testval = 2.4;
Console.WriteLine(testval == testval + eps); // output: true!
```

## Приоритет операций

| --- | --- |
| +, -, !, ~, ++, --, ^ | Унарные |
| \*, /, % | Бинарные мультипликативные |
| +, - | Бинарные аддитивные |
| <<, >> | Битовые сдвиги |
| >, <, >=, <= | Отношений |
| ==, != | Равенства |
| & | И |
| ^ | Исключающее ИЛИ |
| \| | ИЛИ |
| && | Логическое И |
| \|\| | Логическое ИЛИ |
| ? : | Тернарная операция |
| = | Операции назначений |

> Ассоциативность [associativity] – это свойство операции, определяющее направление ее
> выполнения
> Слева направо – операция с левой ассоциативностью
> Справа налево – операция с правой ассоциативность
{.is-info}

> Левоассоциативные: все бинарные операции
> Правоассоциативные: присваивание, тернарная операция
{.is-warning}

![ассоциативность_пример.png](/ассоциативность_пример.png)