---
title: Арифметика целых чисел
description: 
published: true
date: 2023-11-18T20:19:30.480Z
tags: 
editor: markdown
dateCreated: 2023-10-21T20:57:55.371Z
---

# Арифметика целых чисел

> ***Определение.*** 
> $a | b \Leftrightarrow b \div a\ (\exists{k \in \Z}\ b = ak)$
{.is-info}


Примеры:
$$ 2 | 6,\ 5 | 0,\ 0 | 0 $$

> Лемма 1:
> 1) Любое число делит 0
> 2) Любое число делится на 1
> 3) $\forall{b}\ (0 | b \Rightarrow b = 0)$
> 4) $\forall{b}\ (b | 1 \Rightarrow b = \pm 1)$
{.is-info}

Доказательство:
1) $0 = a \cdot 0$
2) $a = a \cdot 1$
3) Пусть не так. Тогда: $\exists{k}\ b = 0 \cdot k \Rightarrow b = 0$
4) $1 = b \cdot k \\ Тогда\ 1 = |b \cdot k| = |b||k|=1 \Rightarrow b = \pm 1$

> Лемма 2:
> $\forall{a, b, c}$
> 1) $a | a$
> 2) $(a | b \land b | c) \Rightarrow a | c$
> 3) $(a | b \land b | a) \Rightarrow a \pm b$
{.is-info}

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

> Лемма 3:
> $\forall{a, b, c}$
> 1) $(a | b \land a | c) \Rightarrow (a | (b + c) \land a | (b - c))$
> 2) $(a | b \land a|(b + c)) \Rightarrow a | c$
> 3) $(a | b \land a | (b - c)) \Rightarrow a | c$
{.is-info}

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

## Целочисленное деление
### Теорема о делении натуральных чисел
> $\forall{a, b \in \N}\ (b \neq 0\Rightarrow \exists !\ (q, r)\in \N^2\ (a = b\cdot q + r \land r < b))$

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

### Теорема о делении целых
> $\forall{a, b \in \N}\ (b \neq 0\Rightarrow \exists !\ (q, r)\in \Z\times\N\ (a = b\cdot q + r \land 0 \leq r < b))$

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

## Сравнение по модулю

***Определение.***
Пусть $m > 1$. Тогда $a$ и $b$ сравнимы по модулю $m \Leftrightarrow m | (a - b)$.

***Обозначение:***
$$
a \equiv b\ (mod\ m), a \equiv b\ (m),\ a \equiv_m b
$$

> Лемма:
> $\forall{a, b}\ \forall{m > 1}\ a \equiv b\ (m) \Leftrightarrow a\ \%\ m = b\ \%\ m$

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

> Лемма:
> $\forall{a, b, c}\ \forall{m > 1}$
> 1) $a \equiv a\ (m)$
> 2) $a \equiv b\ (m) \Rightarrow b \equiv a\ (m)$
> 3) $(a \equiv b\ (m) \land b \equiv c\ (m)) \Rightarrow (a \equiv c\ (m))$
{.is-info}

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

> Следствие:
> $
> \forall{a}\ \forall{m > 1}\ a \equiv a\ \%\ m\ (m)
> $

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

> Следствие:
> 1) Среди чисел $0, ..., m - 1$ нет двух сравнимых по модулю $m$.
> 2) Любое число сравнимо по модулю $m$ c одним из $0, ..., m - 1$.

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

> Лемма:
> $\forall{a, b, c, d}\ \forall{m > 1}$ $a \equiv b\ (m)\ и\ c \equiv d\ (m)$, то
> 1) $a + b \equiv c + d\ (m)$
> 2) $a \cdot c \equiv b \cdot d\ (m)$
> 3) $\forall{n \in \N}\ a^n \equiv b^n\ (m)$

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

## Простые числа
> 
> ***Определение.*** 
> Число $p > 1$ называется простым $\Leftrightarrow \forall{d} (d | p \Rightarrow d = \pm 1 \vee p = \pm p)$.
> Число $n > 1$ называется составным $\Leftrightarrow n\ -\ не\ простое \Leftrightarrow \exists{k} (1 < k < n \land k | n)$.
{.is-info}

## Факторизация

> ***Определение.***
> Выражения ${p_1}^{a_1} \cdot {p_2}^{a_2} \cdot ... \cdot {p_n}^{a_n}$ называется факторизацией числа $n$, если:
> 1. $n = {p_1}^{a_1} \cdot {p_2}^{a_2} \cdot ... \cdot {p_n}^{a_n}$
> 2. все $p_i$ - попарно различные простые числа
> 3. $a_i \in \N$
> {.is-info}

> ***Определение.***
> Факторизации $Ф_1$, $Ф_2$ называются различными $\Leftrightarrow$ есть простое число, которое входит в $Ф_1$ и $Ф_2$ в разных степенях.
{.is-info}


> ***Определение.***
> Простое $p$ входит в степени $b$ в факторизацию ${p_1}^{a_1} \cdot ... \cdot {p_n}^{a_n} \Leftrightarrow \exists{i}\ (p=p_i \land b=a_i)\vee(\forall{i}\ p = p_i \land b = 0)$
{.is-info}

> ***Теорема.*** Основная теорема арифметики:
> $\forall{n > 1}$ (у $n$ есть факторизация, никакие две факторизации не являются различными)

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

> ***Теорема.*** 
> Существует бесконечно много простых чисел.


Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

> ***Теорема.*** Критерий делимости.
> $a = \epsilon \cdot {p_1}^{\alpha_1} \cdot ... \cdot {p_n}^{\alpha_n}, где\ \epsilon = \pm 1$
> $b = \delta \cdot {p_1}^{\beta_1} \cdot ... \cdot {p_n}^{\beta_n}, где\ \delta = \pm 1$
> $a | b \Leftrightarrow \forall{i}\ \alpha_i \leq \beta_i$

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

> ***Определение.***
> Число $d$ называется наибольшим общим делителем чисел $a$ и $b$:
> 1) $d \in \N$
> 2) $d|a \land d|b$
> 3) $\forall{d' \in \N}\ d' | a \land d'|b \Rightarrow d'|d$
{.is-info}

> ***Теорема.***
> $\forall{a}\ \forall{b}\ \exists!{d}$ ($d$ - НОД чисел $a$, $b$)
Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

> ***Следствие.***
> $НОД(a;b) = НОД(b;a)$

> ***Лемма.***
> $\forall{a,b,q}\ НОД(a + bq;b) = НОД(a;b)$

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

> ***Следствие.***
> $\forall{a}\ \forall{b \neq 0}\ НОД(a \% b;b) = НОД(a;b)$

Доказательство:
<font color="#FF6666"> Тут должно быть доказательство </font>

> ***Определение.***
> Числа $a$ и $b$ взаимнопростые $\Leftrightarrow$ $НОД(a;b)$ = 1.
{.is-info}

> ***Лемма.***
> $\forall{a, b}$ следующие утверждения равносильны:
> 1) $НОД(a;b)=1$
> 2) $\forall{d\in\N}\ (d|a\land d|b\Rightarrow d=1)$
> 3) $\rceil \exists{p}$ ($p$ - простое $\land\ p | a \land\ p | b$)
> 4) Если $a, b \neq 0$: $\forall{i}\ min(\alpha_i; \beta_1) = 0$, где $\\a={p_1}^{\alpha_1}\cdot ...\cdot {p_n}^{\alpha_n}\\b={p_1}^{\beta_1}\cdot ...\cdot {p_n}^{\beta_n}$ 

## Функция Эйлера
$\phi(n)$ - функция Эйлера ($totient\ function$)
$\phi(n)$ - кол-во чисел из $1, ..., n - 1$ взаимно простых с $n$.

$\sphericalangle p, p_i$ - простые числа
$\phi(p^n) = p^n - p^{n - 1}$
$\phi({p_1}^{n_1}\cdot ... \cdot {p_k}^{n_k}) = {p_1}^{n_1-1}\cdot(p_1 - 1)\cdot ... \cdot {p_k}^{n_k-1}\cdot(p_k - 1) = n \cdot \prod\limits_{i = 1}^k{1 - \frac{1}{p_i}}$

## Теорема Эйлера
Пусть $m\geq2, a \bot m$. Тогда $a^{\phi(m)}\equiv1(mod\ m)$.

## Малая теорема Ферма
Пусть $p$ - простое. Тогда $a^{p - 1}\equiv(mod\ p)$