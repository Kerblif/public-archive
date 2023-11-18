---
title: Лекция 10. Строки.
description: 
published: true
date: 2023-11-18T20:18:59.112Z
tags: 
editor: markdown
dateCreated: 2023-10-25T11:53:23.134Z
---

# Лекция 10. Строки.

> Строки в C# хранятся в UTF-16
{.is-info}

> Максимальный размер строки в C# – 2Гб или в около миллиарда символов
{.is-warning}


* Строки в C# являются ссылочными типами
* В конце строки нет терминального символа ‘\0’
* Строка может содержать внутри себя произвольное количество символов ‘\0’
* Свойство Length возвращает общее количество объектов Char в строке
* Индексы начинаются с 0
* Доступ для чтения к отдельным символам строки (т.е. может быть только r-value)
* В итерировании по строке, опять же с доступом для чтения

```cs
// Память, выделенная под это будет
// доступна для сборщика мусора
// после выполнения назначения
// ссылки в следующей строке
string str = "Let eat";

// В этой строке неявно создан новый
// экземпляр для хранения строки
// после конкатенации
str += " bee!";
Console.Write(str);
```

```cs
// Описание без инициализации
string message1;
// Инициализация значением null
string message2 = null;
// Инициализация пустой строкой
string message3 = System.String.Empty;
// Инициализация строковым литералом
string oldPath = "c:\\Program Files\\Microsoft Visual Studio 8.0";
// Инициализация буквальным строковым литералом
string newPath = @"c:\Program Files\Microsoft Visual Studio 9.0";
// Использование анонимного типа, внутри методов
var temp = "I'm still a strongly-typed System.String!";
// Константная строка
const string message4 = "You can't get rid of me!";
// Явное использование конструктора String()
// для создание строки из char*, char[] или sbyte*
char[] letters = { 'A', 'B', 'C' };
string alphabet = new string(letters);
```

```cs
string line1 = "Это строка 1";
char[] chars = { 'M', 'a', 'c', 'c',
'и', 'в' };
string line2 = new string(chars); // "Массив"
string line3 = new string('W', 1); // "W"
string line4 = new string('7', 3); // "777"
string line5 = 242.ToString(); // "242"

// Такой код некорректен:
string line;
line += "asdfg"; // Ошибка компиляции – line не инициализирована.
```

* Методы работы со строками можно вызывать для пустых строк, так как они допустимы System.String
* Строка NULL не ссылается на экземпляр System.String объекта, и любая попытка вызова метода в строке NULL вызывает исключение NullReferenceException.
* Допустимо использовать строки NULL в операциях объединения и сравнения с другими строками

```cs
string str = "hello";
string nullStr = null;
string emptyStr = String.Empty;

string tempStr = str + nullStr; // Output of the following line: hello
bool b = (emptyStr == nullStr); // Output of the following line: False
// The following line creates a new empty string.
string newStr = emptyStr + nullStr;
// Null strings and empty strings behave differently. The following
// two lines display 0.
Console.WriteLine(emptyStr.Length);
Console.WriteLine(newStr.Length);
// The following line raises a NullReferenceException.
//Console.WriteLine(nullStr.Length);
```

```cs
// The null character can be displayed and counted, like other chars.
string s1 = "\x0" + "abc";
string s2 = "abc" + "\x0";
// Output of the following line: * abc*
Console.WriteLine("*" + s1 + "*");
// Output of the following line: *abc *
Console.WriteLine("*" + s2 + "*");
// Output of the following line: 4
Console.WriteLine(s2.Length);
```

## Индексация строк
```cs
using System;
string indexingDemo = "Yet another string...";
Console.WriteLine(indexingDemo[4]);
Console.WriteLine(indexingDemo[^4]);
Console.WriteLine(indexingDemo[4..]);
Console.WriteLine(indexingDemo[..^18]);
Console.WriteLine(indexingDemo[4..11]);

// Вывод:
// a
// g
// another string...
// Yet
// another
```

## Конкатенация строк

```cs
string strConcat = "Hello";
strConcat = strConcat + " Software";
strConcat += " Engineering!";
Console.WriteLine(strConcat);

// Вывод: Hello Software Engineering!
```

## Связь строк и ссылок

```cs
string first = "Foo";
string second = first;
first += "Bar";
Console.Write($"first:: {first} second:: {second}");

// Вывод: first:: FooBar second:: Foo
```

## switch
```cs
static string TranslateDay (string day) => day.ToLower() switch
{
  "monday" => "понедельник",
  "tuesday" => "вторник",
  "wednesday" => "среда",
  "thursday" => "четверг",
  "friday" => "пятница",
  "saturday" => "суббота",
  "sunday" => "воскресенье",
  _ => throw new ArgumentException("This is not a valid day.");
};
```

## Спецификация формата строк

{ index[,alignment][:formatString[precisionSpecifier]] }, где
* index – номер аргумента;
* alignment – ширина поля;
* formatString – спецификатор формата;
* precisionSpecifier – спецификатор точности.

| Спецификатор | Формат | Роль спецификатора точности |
| --- | --- | --- |
| C или с | Валютный | Количество десятичных разрядов. |
| D или d | Целочисленный | Минимальное число цифр. |
| E или e | Экспоненциальный | Число разрядов после точки. |
| F или f | С фиксированной точкой | Число разрядов после точки. |
| G или g | Наиболее короткий между E и F | Аналогично E и F |
| N или n | Численный c отступами | Минимальное число цифр. |
| P или p | Процентный | Количество десятичных разрядов. |
| R или r | Строка, посимвольно равная такому же числу | Игнорируется. |
| X или x | Шестнадцатеричный | Минимальное число цифр. |

```cs
double dou = 1234.567;
string form = "Спецификация Е4: {0:E4}, спецификация F4: {0:F4}";
string result = string.Format(form, dou);
System.Console.WriteLine(result);
// Вывод: Спецификация Е4: 1,2346E+003, спецификация F4: 1234,5670
```

```cs
int num = 23;
string form = "Основание 10: {0,-4:D}\r\nОснование 16: {0,4:X}";
System.Console.WriteLine(form, num);
// Вывод:
// Основание 10: 23
// Основание 16: 17
```

```cs
int num = 23;
string form = "Основание 10: {0,-4:D3}\r\nОснование 16: {0,4:X3}";
System.Console.WriteLine(form, num);
// Вывод:
// Основание 10: 023
// Основание 16: 017
```

```cs
double completion = 0.57;
string form = "Процесс загрузки: {0:P4}";
System.Console.WriteLine(form, completion);
// Вывод:
// Процесс загрузки: 57,0000 %
```

```cs
decimal currency = 2365700000;
string form = "На Вашем счету: {0,3:C2}";
System.Console.WriteLine(form, currency);

// Вывод:
// На Вашем счету: 2 365 700 000,00 ₽
```

```cs
string example = "5 great men attacks of 1997 happened over 20 years ago.";
Console.WriteLine(CountIntsInSplitString(example, " "));

static int CountIntsInSplitString(string s, params string[] delimiters) {
  int count = 0;
  if (delimiters.Length == 0) {
    delimiters = new[] { " " };
  }
  // Пустые вхождения строки будут удаляться в результате разделения.
  string[] splitString = s.Split(delimiters, StringSplitOptions.RemoveEmptyEntries);
  foreach (string word in splitString) {
  	// Если не нужно сохранять результат в outпеременную, то можно проигнорировать его
    if (int.TryParse(word, out _)) {
      ++count;
    }
  }
  return count;
}
```

```cs
using System;
string sent = "De gustibus non est disputandum"; // О вкусах не спорят.
string[] words = sent.Split(' ');
Console.WriteLine("word.Length = " + words.Length);
foreach (string word in words)
{
  Console.Write("{0}\t", word);
}
sent = string.Join("-:-", words);
Console.WriteLine("\n" + sent);

// Вывод:
// word.Length = 5
// De gustibus non est
// disputandum
// De-:-gustibus-:-non-:-est-:-disputandum
```

## Работа как с char[]
```cs
string row = "0123456789";
char[] reversed;
reversed = row.ToCharArray();

Array.Reverse(reversed);

row = new string(reversed);
Console.WriteLine(row);

// Вывод:
// 9876543210
```

