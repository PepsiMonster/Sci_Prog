---
## Front matter
title: "Отчет по Лабораторной работе №3 по предмету Научное программирование"
author: "Лобов Михаил Сергеевич"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
    - spelling=modern
    - babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Изучить основы работы с Octave, включая работу с векторами, матрицами, простроение графиков, выполениение простейших вычислений и использование циклов для научных вычислений.

# Задание

Программно реализовать основные действия в Octave:
  1. Простейшие вычисления
  2. Вычисления скалярного произведения векторов, векторного произведеня векторов, нормы вектора, проекции
  3. Операции с матрицами (произведение, транспонирование, собственные числа)
  4. Построение и улучшение графиков 
  5. Сравнение циклов и операций с векторами
  6. Формирование отчета и создание презентации
  7. Публикация результатов

# Теоретическое введение

GNU Octave — это свободная программная среда для выполнения численных вычислений, аналогичная MATLAB. Она широко используется для решения задач линейной алгебры, работы с массивами данных, построения графиков и визуализации данных, а также для символьных вычислений.

**Основные особенности Octave:**
- **Интерфейс командной строки**: позволяет выполнять математические вычисления через консоль, как калькулятор.
- **Поддержка скриптов и функций**: позволяет создавать сценарии (файлы `.m`) для автоматизации расчетов.
- **Широкий набор встроенных функций**: поддерживает матричные операции, функции оптимизации, интегралы, решатели дифференциальных уравнений и многое другое.
- **Визуализация данных**: Octave поддерживает функции для создания 2D и 3D графиков.

Octave является кросс-платформенной программой и может использоваться в Windows, macOS и Linux.

# Выполнение лабораторной работы

  1. **Скачивание и установка OCtave**
  2. **Запуск программы и выполнение команд**
        ```octave
        diary on
        ```
  3. **Создание векторов и матриц, выполнение вычислений. Пример:**
        ```octave
        u = [1 -4 6];
        v = [2; 1; -1];
        result = 2*v + 3*u;
        ans =
        7
        -10
        16
        A = [1 2 -3; 2 4 0; 1 1 1];
        A =

        1   2  -3
        2   4   0
        1   1   1
        ```
  4. **Построение графиков**
        ```octave
        x = linspace(0, 2*pi, 50);
        y = sin(x);
        plot(x, y);
        ```
  5. **Выполение циклов**
        ```octave
        clear
        tic
        s = 0;
        for n = 1:100000
            s = s + 1/n^2;
        end
        toc
        ```

![Начало работы](pictures/Снимок1.png){#fig:001 width=70%}

![Операции с вектрами](pictures/Снимок2.png){#fig:001 width=70%}

![Операции с матрицами](pictures/Снимок3.png){#fig:001 width=70%}

![Начало работы с графиками](pictures/Снимок4.png){#fig:001 width=70%}

![Улучшение графиков](pictures/Снимок5.png){#fig:001 width=70%}

![Построение графика двух графиков на одном чертеже](pictures/Снимок6.png){#fig:001 width=70%}

![Построение более сложных графиков](pictures/Снимок7.png){#fig:001 width=70%}

![Цикл for](pictures/Снимок8.png){#fig:001 width=70%}

![Цикл векторный](pictures/Снимок9.png){#fig:001 width=70%}

![Скорость обоих циклов](pictures/Снимок10.png){#fig:001 width=70%}


# Формирование отчета

   - Создание скриншотов всех выполненных команд и графиков.
   - Офрмление отчета, с добавлением описания к выполненным операциям.
   - Конвертация в docx и pdf


# Выводы

 Программный комплекс Octave представляет очень удобную среду для выполения различных математических операций (матричные и векторыне рассчеты), а также для визуализации полученных результатов на графика. Помимо этого в программе удобно выполнять некоторые циклы и сравнивать их производительность в зависимости от времени выполнения.

# Список литературы{.unnumbered}

::: {#[Лабораторная_работа_3](https://esystem.rudn.ru/mod/folder/view.php?id=1150970)}
:::