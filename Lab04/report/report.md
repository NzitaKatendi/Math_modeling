---
# Front matter
lang: ru-RU
title: "Отчет по Лабораторной Работе № 4"
subtitle: "Модель гармонических колебаний - Вариант 51"
author: "Нзита Диатезилуа Катенди"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the υalue makes tex try to haυe fewer lines in the paragraph.
  - \interlinepenalty=0 # υalue of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

---


# Цель работы

Постройте фвзоывй портрет гармонического осциллятора и решение уравнения гармонического осциллятора.

# Задание

Вариант № 51
Постройте фазовый портрет гармонического осциллятора и решение уравнения
гармонического осциллятора для следующих случаев

1. Колебания гармонического осциллятора без затуханий и без действий внешней
силы $$\dot{x} + 1.7x = 0 $$

2. Колебания гармонического осциллятора c затуханием и без действий внешней
силы   $$\ddot{x} + 1.7\dot{x} + 1.7x = 0 $$

3. Колебания гармонического осциллятора c затуханием и под действием внешней
силы $$\ddot{x} + 2\dot{x} + 1.7x = 0.7cos(2.7t) $$
 
 На интервале $ = (0, 59)$ (шаг 0.05) с начальными условиями $x0 = 1.7 и $y0 = -0.2

# Теоретическое введение

Движение грузика на пружинке, маятника, заряда в электрическом контуре, а
также эволюция во времени многих систем в физике, химии, биологии и других
науках при определенных предположениях можно описать одним и тем же
дифференциальным уравнением, которое в теории колебаний выступает в качестве
основной модели. Эта модель называется линейным гармоническим осциллятором.

Уравнение свободных колебаний гармонического осциллятора имеет следующий вид:

$$ddot{x} + 2\gamma\dot{x} + \omega^2{x} = 0$$

где $x$ – переменная, описывающая состояние системы (смещение грузика, заряд
конденсатора и т.д.), gamma – параметр, характеризующий потери энергии (трение в
механической системе, сопротивление в контуре), omega – собственная частота колебаний, $t – время.

При отсутствии потерь в системе вместо уравнения получаем уравнение консервативного осциллятора энергия колебания которого сохраняется во времени.
Для однозначной разрешимости уравнения второго порядка (2) необходимо задать два начальных условия.

Независимые переменные $x$, $y$ определяют пространство, в котором «движется» решение. Это фазовое пространство системы, поскольку оно двумерно будем называть его фазовой плоскостью.
Значение фазовых координат $x$, $y$ в любой момент времени полностью определяет состояние системы. Решению уравнения движения как функции времени отвечает гладкая кривая в фазовой плоскости. Она называется фазовой траекторией. Если множество различных решений (соответствующих различным
начальным условиям) изобразить на одной фазовой плоскости, возникает общая картина поведения системы. Такую картину, образованную набором фазовых траекторий, называют фазовым портретом.


# Выполнение лабораторной работы

##  Построение графиков колкбания гармогического осциллятора и фазовых портретов

Построим графики изменения численности войск. Далее приведён код на языке Julia, решающий задачу:

using Plots
using DifferentialEquations

#Параметры осциллятора
#x'' + g* x' + w^2* x = f(t)
#w - частота
#g - затухание

w = 1.7;
g = 0.00;

#Правая часть уравнения f(t)


#Правая часть уравнения f(t)

function f(t)
    f = 0;
    return f;
end
    
#Вектор-функция f(t, x)
#для решения системы дифференциальных уравнений
#x' = y(t, x)
#где x - искомый вектор

function y(du, u, p, t)
    du[1] = u[2];
    du[2] = -w.* w.* u[1] - g.* u[2] + f(t);
end

#Точка, в которой заданы
#начальные условия

#t0 = 0;

#Вектор начальных условий
#x(t0) = x0

v0 = [1.7; -0.2];

#Интервал на котором будет
#решаться задача

t = (0; 59);

#Решаем дифференциальные уравнения
#с начальным условием x(t0) = x0
#на интервале t
#с правой частью, заданной y
#и записываем решение в матрицу x

prob = ODEProblem(y, v0, t);
sol = solve(prob, dt = 0.05);

#Переписываем отдельно
#x в y1, x' в y2

y1 = [];
y2 = [];

for value in sol.u
    push!(y1, value[1]);
    push!(y2, value[2]);
end
    
display(plot(y1, y2, legend=:topright, label = " Фазовый портрет"));
savefig("myplot.png")

# Второй случай

#Параметры осциллятора
#x'' + g* x' + w^2* x = f(t)
#w - частота
#g - затухание

w = 1.7;
g = 1.7;

#Правая часть уравнения f(t)


#Правая часть уравнения f(t)

function f(t)
    f = 0;
    return f;
end
    
#Вектор-функция f(t, x)
#для решения системы дифференциальных уравнений
#x' = y(t, x)
#где x - искомый вектор

function y(du, u, p, t)
    du[1] = u[2];
    du[2] = -w.* w.* u[1] - g.* u[2] + f(t);
end

#Точка, в которой заданы
#начальные условия

#t0 = 0;

#Вектор начальных условий
#x(t0) = x0

v0 = [1.7; -0.2];

#Интервал на котором будет
#решаться задача

t = (0; 59);

#Решаем дифференциальные уравнения
#с начальным условием x(t0) = x0
#на интервале t
#с правой частью, заданной y
#и записываем решение в матрицу x

prob = ODEProblem(y, v0, t);
sol = solve(prob, dt = 0.05);

#Переписываем отдельно
#x в y1, x' в y2

y1 = [];
y2 = [];

for value in sol.u
    push!(y1, value[1]);
    push!(y2, value[2]);
end
    
display(plot(y1, y2, legend=:topright, label = " Второй случай"));
savefig("myplot.png")

  #Трьетый случай

  #Параметры осциллятора
#x'' + g* x' + w^2* x = f(t)
#w - частота
#g - затухание

w = 1.7;
g = 2;

#Правая часть уравнения f(t)


#Правая часть уравнения f(t)

function f(t)
    f = 0.7*cos(2.7*t);
    return f;
end
    
#Вектор-функция f(t, x)
#для решения системы дифференциальных уравнений
#x' = y(t, x)
#где x - искомый вектор

function y(du, u, p, t)
    du[1] = u[2];
    du[2] = -w.* w.* u[1] - g.* u[2] + f(t);
end

#Точка, в которой заданы
#начальные условия

#t0 = 0;

#Вектор начальных условий
#x(t0) = x0

v0 = [1.7; -0.2];

#Интервал на котором будет
#решаться задача

t = (0; 59);

#Решаем дифференциальные уравнения
#с начальным условием x(t0) = x0
#на интервале t
#с правой частью, заданной y
#и записываем решение в матрицу x

prob = ODEProblem(y, v0, t);
sol = solve(prob, dt = 0.05);

#Переписываем отдельно
#x в y1, x' в y2

y1 = [];
y2 = [];

for value in sol.u
    push!(y1, value[1]);
    push!(y2, value[2]);
end
    
display(plot(y1, y2, legend=:topright, label = "  Трьетый случай"));
savefig("myplot.png")


```

##
В результаты получим следующие графики

![Колебания гармонического осцилятора случай 1](image/image1.png){ #fig:004 width=70%height=70% }

![Колебания гармонического осцилятора случай 2](image/image2.png){ #fig:004 width=70%height=70% }

![Колебания гармонического осцилятора случай 3](image/image3.png){ #fig:004 width=70%height=70% }

# Выводы

Мы научились строить фазовые  портреты а также изучили гармонические колебания осциллятора

# Список литературы
 [Модель гармонических колебаний](https://esystem.rudn.ru/mod/resource/view.php?id=1100260)



