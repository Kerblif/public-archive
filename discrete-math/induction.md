---
title: Индукция
description: 
published: true
date: 2023-10-22T15:17:53.434Z
tags: 
editor: markdown
dateCreated: 2023-10-21T21:23:02.484Z
---

# Индукция

## Принцип математической индукции (ПМИ)
$$
\forall \phi (\phi(0)\land\forall{n}(\phi(n) \Rightarrow \phi(n + 1))) \Rightarrow \forall{n}\ \phi(n)
$$
### Индуктивное "доказательство" ПМИ:
Дано: $\phi$ - предмет, $\phi(0)$, $\forall{n}\ (\phi(n) \Rightarrow \phi(n + 1))$
Доказать: $\phi(n)$ выполнено для всех $n$.
<очевидно>
## Принцип наименьшего числа (ПНЧ)
$$
\forall\phi\ (\exists{m}\ \phi(m) \Rightarrow \exists{n} (\phi(n) \land \forall{m < n}\ \rceil\phi(m)))
$$
<font color="#FF3333">Тут должны быть примеры</font>
## Принцип сильной индукции (ПСИ)
$$
\forall{\phi}(\forall{n}(\phi(0)\land...\land\phi(n-1)) \Rightarrow \forall{n}\ \phi(n)) \\
\forall{\phi}(\forall{n}(\forall{m < n}\ \phi(m))\Rightarrow \forall{n}\ \phi(n))
$$
<font color="#FF3333">Тут должны быть примеры</font>
## Равносильность
1) ПСИ
2) ПНЧ
3) ПМИ

Шаги решения: 1 -> 2, 2 -> 3, 3 -> 1

### 1 -> 2
Дано: ПСИ 
$$ \forall{\phi}(\forall{n}(\forall{m < n}\ \phi(m))\Rightarrow \forall{n}\ \phi(n)) $$
Хотим: ПНЧ
$$ \forall\psi\ (\exists{m}\ \psi(m) \Rightarrow \exists{n} (\psi(n) \land \forall{m < n}\ \rceil\psi(m))) $$
Доказательство:
$$
\forall{n}(\forall{m<n}\ \rceil\psi(m) \Rightarrow \rceil\psi(n)) \Rightarrow \forall{n}\ \rceil\psi(n) \equiv \\
\equiv \rceil \forall{n}\ \rceil\psi(n) \Rightarrow \rceil \forall{n} (\forall{m<n}\ \rceil\psi(m) \Rightarrow \rceil \psi(n)) \equiv \\
\equiv \exists{n}\ \rceil\rceil\psi(n) \Rightarrow \exists{n}\ \rceil(\forall{m<n}\ \rceil\psi(m) \Rightarrow \rceil\psi(n)) \equiv \\
\equiv \exists{n}\ \psi(n) \Rightarrow \exists{n}\ (\forall{m < n}\ \rceil\psi(m)\land\rceil\rceil\psi(n)) \equiv \\
\equiv \exists{m}\ \psi(m) \Rightarrow \exists{n} (\psi(n)\land\forall{m<n}\ \psi(m))
$$
### 2 -> 3
Дано:
$\forall\phi\ (\exists{m}\ \phi(m) \Rightarrow \exists{n} (\phi(n) \land \forall{m < n}\ \rceil\phi(m)))$
База: $\phi(0)$
Шаг: $\forall{n}\ \phi(n) \Rightarrow \phi(n + 1)$

Хотим:
$\forall \psi\ (\psi(0)\land\forall{n}(\psi(n) \Rightarrow \psi(n + 1))) \Rightarrow \forall{n}\ \psi(n)$
Доказательство:
$\exists{n_0} (\rceil\psi(n_0)\land\forall{m>n}\ \rceil\rceil\psi(m))$
1) $n_0 = 0$
Тогда: $\rceil\psi(0)$
По базе: $\psi(0)$
Противоречние! 
2) $\exists{k}\ n_0 = k + 1$
Тогда $k < n_0$. Значит, $\psi(k)$. По шагу: $\psi(k) \Rightarrow \psi(k + 1)$.
Значит, $\psi(k + 1) = \psi(n_0)$. Но $\rceil\psi(n_0)$. 
Противоречие!

### 3 -> 1
Дано:
$$
\forall \phi\ (\phi(0)\land\forall{n}(\phi(n) \Rightarrow \phi(n + 1))) \Rightarrow \forall{n}\ \phi(n)
$$
Хотим:
$$
\forall{\psi}(\forall{n}(\forall{m < n}\ \psi(m))\Rightarrow \forall{n}\ \psi(n))\\
Prog(\psi) = \forall{n}\ (\forall{m < n}\ \psi(m) \Rightarrow \psi(n))
$$
Доказательство:
$$
\phi(n) = \forall{m < n}\ \phi(m)\ (\equiv \psi(0)\land...\land\psi(n - 1)) \\
$$
Получим базу для $\phi: \phi(0)\equiv\forall{m < 0}\ \psi(m)\ \equiv \forall{m}\ (m < 0 \Rightarrow \psi(m))$
Получим шаг для $\phi$:
Дано: $n$, $\psi(n)$, $k$, $k < n + 1$
Хотим: $\psi(k)$

$k < n + 1 \Leftrightarrow k < n\ \vee\ k = n$
1) Случай: $k < n$
$\forall{m < n}\ \psi(m) \Rightarrow \psi(k)$
2) Cлучай: $k = n$
Имеем $\phi(n)$, т.е. $\forall{m < n}\ \phi(m)$
Так как $Prog(\psi)$, получаем $\psi(n)$, т.е. $\psi(k)$

По ПМК для $\phi$ получаем $\forall{n}\ \phi(n)$.
Итак, получаем $\forall{n}\ \phi(n)$, т.е. $\forall{n}\ \forall{m < n}\ \psi(m)$, т.е. $\forall{n}\ \forall{m}\ (m < n \Rightarrow \psi(m))$

