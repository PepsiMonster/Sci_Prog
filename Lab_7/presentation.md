```markdown
---
marp: true
title: "Лабораторная работа (Octave)"
author: "Имя Фамилия"
paginate: true
theme: default
---

# Лабораторная работа  
## Математические основы визуализации в Octave

**Тема**: Построение параметрических, полярных, неявно заданных функций, а также работа с комплексными числами и специальными функциями в Octave.

---

# Цель работы

Ознакомиться с функциональностью программного пакета Octave в области графической визуализации:

- Изучить построение параметрических кривых (на примере циклоиды).
- Освоить графики в полярных координатах.
- Научиться визуализировать неявно заданные функции.
- Исследовать графическое представление операций над комплексными числами.
- Рассмотреть применение специальных функций, в частности гамма-функции, и сравнить её со значениями факториала.

---

# Задание

1. Построить параметрический график, например, циклоиду, используя уравнения вида:
   \[
   x(t) = r(t - \sin t), \quad y(t) = r(1 - \cos t).
   \]
2. Выполнить построение графиков в полярных координатах для функций вида \( r = f(\theta) \).
3. Реализовать визуализацию неявно заданных функций \( F(x,y)=0 \).
4. Исследовать операции над комплексными числами и отобразить их геометрическую интерпретацию.
5. Рассмотреть гамма-функцию \( \Gamma(x) \) и сравнить её со значением факториала в целочисленных точках.

---

# Теоретическое введение (1/3)

**Параметрические графики:**  
- Параметрические уравнения задают кривые через параметр \( t \).
- Пример циклоиды:
  \[
  x(t) = r(t - \sin t), \quad y(t) = r(1 - \cos t).
  \]
- Позволяют визуализировать траектории движущихся объектов или сложные кривые, не задаваемые явно через \( y=f(x) \).

---

# Теоретическое введение (2/3)

**Полярные координаты:**  
- Каждая точка задается радиусом \( r \) и углом \(\theta\):
  \[
  r = f(\theta).
  \]
- Удобны для исследования фигур, более естественных в полярной форме, например лимасоны, розовые кривые.

**Неявные функции:**  
- Неявная функция: \[
  F(x,y)=0,
\]
когда невозможно (или неудобно) записать \( y \) явно через \( x \).
- Построение требует численных методов или специальных функций (`ezplot` в Octave).

---

# Теоретическое введение (3/3)

**Графики комплексных чисел:**  
- Комплексное число \( z = x + yi \) соответствует точке \((x,y)\) на комплексной плоскости.
- Визуализация операций (сложение, умножение) помогает понять их геометрический смысл.
- Функция `compass` в Octave отображает векторы, соответствующие комплексным числам.

**Гамма-функция:**  
- Обобщение факториала:
  \[
  \Gamma(n+1) = n! \text{ для } n \in \mathbb{N}.
  \]
- Определена для нецелых и даже комплексных аргументов.
- Анализ графика \(\Gamma(x)\) показывает поведение функции в широком диапазоне аргументов.

---

# Выполнение лабораторной работы (Код: Часть 1)

```octave
% Параметрические графики (циклоида)
t = linspace(0,6*pi,50);
r = 2;
x = r*(t - sin(t));
y = r*(1 - cos(t));
plot(x,y);
axis('equal');
axis([0 12*pi 0 4])
print -dpng cycloid.png
```

*(Здесь мы строим циклоиду и сохраняем результат.)*

---

# Выполнение лабораторной работы (Код: Часть 2)

```octave
% Полярные координаты
theta = linspace(0,2*pi,100);
r = 1-2*sin(theta);
polar(theta,r)
print -dpng limacon-polar.png
```

*(Построение лимасона в полярных координатах.)*

---

# Выполнение лабораторной работы (Код: Часть 3)

```octave
% Неявно заданная функция
f = @(x,y) -x.^2 - x.*y + x + y.^2 - y - 1;
ezplot(f)
print -dpng impl1.png
```

*(График неявно заданной функции F(x,y)=0 с помощью ezplot.)*

---

# Выполнение лабораторной работы (Код: Часть 4)

```octave
% Комплексные числа
z1 = 1+2*i;
z2 = 2-3*i;
clf
compass(z1,'b')
hold on
compass(z2,'r')
compass(z1+z2,'k--')
legend('z_1','z_2','z_1+z_2')
print -dpng complex.png
```

*(Графическое представление комплексных чисел и их суммы.)*

---

# Выполнение лабораторной работы (Код: Часть 5)

```octave
% Гамма-функция и факториал
n = 0:5;
x = linspace(-5,5,500);
plot(n,factorial(n),'*', x,gamma(x+1))
grid on;
legend('n!','gamma(n+1)')
print -dpng gamma.png
```

*(Сравнение факториала и гамма-функции на целочисленных точках.)*

---

# Примеры полученных графиков

**Циклоида:**
![Циклоида](./cycloid.png)

**Лимасон в полярных координатах:**
![Лимасон](./limacon-polar.png)

---

# Примеры полученных графиков (продолжение)

**Неявно заданная функция:**
![Неявная функция](./impl1.png)

**Комплексные числа:**
![Комплексные числа](./complex.png)

**Гамма-функция:**
![Гамма-функция](./gamma.png)

---

# Выводы

- Освоены методы построения параметрических графиков, позволяющих анализировать сложные кривые.
- Продемонстрированы возможности работы в полярных координатах для исследования естественно заданных кривых.
- Изучено построение графиков неявно заданных функций, что расширяет возможности анализа уравнений.
- Визуализация комплексных чисел упрощает понимание операций над ними.
- Сравнение факториала и гамма-функции даёт представление о расширении факториала на нецелые аргументы.

---

# Список литературы

1. Eaton, J. W., Bateman, D., Hauberg, S., & Wehbring, R. (2017). *GNU Octave Manual Version 4*. Free Software Foundation.  
2. Official GNU Octave documentation: [https://docs.octave.org](https://docs.octave.org)  
3. Weisstein, Eric W. "Gamma Function." *MathWorld* — A Wolfram Web Resource: [https://mathworld.wolfram.com/GammaFunction.html](https://mathworld.wolfram.com/GammaFunction.html)  
4. Higham, N. J. (2002). *Accuracy and Stability of Numerical Algorithms*. SIAM.  
5. Press, W. H., Teukolsky, S. A., Vetterling, W. T., & Flannery, B. P. (2007). *Numerical Recipes: The Art of Scientific Computing*. Cambridge University Press.

---

# Спасибо за внимание!
```