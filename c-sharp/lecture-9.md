---
title: Лекция 9. Форматы представления данных. Кодировки.
description: 
published: true
date: 2023-11-18T20:19:21.752Z
tags: 
editor: markdown
dateCreated: 2023-10-25T09:35:51.714Z
---

# Лекция 9. Форматы представления данных. Кодировки.

```cs
// Вывод первых 128 символов
char ch = '\u0000';
while(ch++ <= '\u007F')
{
	Console.Write(ch);
}

// Так тоже можно, но не нужно
char ch = (char)0;
while (ch++ <= 127)
{
	Console.Write(ch);
}
```

<много информации на понимание. посмотрите в презентации>

```cs
char[] test = { 'A', 'b', '3', 'ё' };

Encoding enUTF8 = Encoding.UTF8;
PrintArray(test);

byte[] cTest = enUTF8.GetBytes(test);
PrintArray(cTest);
```

```cs
string coding = "UTF-8";
byte[] codes = new byte[test.Length];
foreach (char c in test)
{
	Console.Write($"{c} ");
}

codes = Encoding.GetEncoding(coding).GetBytes(test);
Console.WriteLine();
Console.Write($"{BitConverter.ToString(codes)} ");
```

## Региональные настройки

Группы настроек региональных стандартов:
* Invariant - не зависит от регионов
* Neutral - определяют только язык ("ru", "en")
* Specific - определяют язык и страну/регион (“en-CA”, “en-GB”)

Текущие региональные настройки определяются значениями двух свойств выполняемого потока:
* Thread.CurrentCulture – получает и задает язык и региональные параметры для текущего потока 
* Thread.CurrentUICulture – получает или задает текущие язык и региональные параметры

```cs
using System;
using System.Globalization;

// CultureInfo для английского языка в USA.
Console.WriteLine(100.ToString("c", new CultureInfo("en-US")));

// CultureInfo для России, форматы по умолчанию.
Console.WriteLine(100.ToString("c", new CultureInfo("ru-RU", false)));

// CultureInfo для России, форматы из установок пользователя.
Console.WriteLine(100.ToString("c", new CultureInfo("ru-RU", true)));
```

```cs
Console.WriteLine(Thread.CurrentThread.CurrentUICulture);
Thread.CurrentThread.CurrentUICulture = new CultureInfo("ja-JP");
Console.WriteLine(Thread.CurrentThread.CurrentUICulture);
```

