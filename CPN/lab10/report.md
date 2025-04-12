---
## Front matter
title: "Лабораторная работа №10"
subtitle: "Задание для самостоятельного выполнения"
author: "Игнатенкова Варвара Николаевна"

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
lot: false # List of tables
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
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
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

Выполнить задание для самостоятельного выполнения.

# Задание

1. Построить модели с помощью CPNTools задачи об обедающих мудрецах.
2. Вычислитепространство состояний. Сформируйте отчёт о пространстве состояний и проанализируйте его. Постройте граф пространства состояний.

# Выполнение лабораторной работы

Пять мудрецов сидят за круглым столом и могут пребывать в двух состояниях —
думать и есть. Между соседями лежит одна палочка для еды. Для приёма пищи
необходимы две палочки. Палочки — пересекающийся ресурс. Необходимо синхро
низировать процесс еды так, чтобы мудрецы не умерли с голода.

 1. Рисуем граф сети. Для этого с помощью контекстного меню создаём новую сеть,
 добавляем позиции, переходы и дуги (рис. 1).

 Начальные данные:
 
 – позиции: мудрец размышляет (philosopher thinks), мудрец ест (philosopher eats),
 палочки находятся на столе (sticks on the table)
 
 – переходы: взять палочки (take sticks), положить палочки (put sticks)


![ Рис. 1. Граф сети задачи об обедающих мудрецах](image/1.png){#fig:001 width=70%}


 2. В меню задаём новые декларации модели: типы фишек, начальные значения
 позиций, выражения для дуг:– n—числомудрецов ипалочек (n = 5);– p—фишки,обозначающие мудрецов, имеют перечисляемый тип PH от 1 до n;– s—фишки,обозначающие палочки, имеют перечисляемый тип ST от 1 до n;– функция ChangeS(p) ставит в соответствие мудрецам палочки (возвращает но
 мера палочек, используемых мудрецами); по условию задачи мудрецы сидят по
 кругу и мудрец p(i) может взять i и i+1 палочки, поэтому функция ChangeS(p) определяется следующим образом:
 fun ChangeS (ph(i))=
 1`st(i)++st(if = n then 1 else i+1)

![ Рис. 2. Задание деклараций задачи об обедающих мудрецах](image/2.png){#fig:002 width=70%}


Врезультате получаем работающую моделью

![ Рис. 3. Модель задачи об обедающих мудрецах](image/3.png){#fig:003 width=70%}


После запуска модели наблюдаем, что одновременно палочками могут воспользо
ваться только два из пяти мудрецов (рис. 4).

![ Рис. 4. Запуск модели задачи об обедающих мудрецах](image/4.png){#fig:004 width=70%}

Упражнение. Вычислите пространство состояний. Сформируйте отчёт о пространстве состояний и проанализируйте его. Постройте граф пространства состояний.

![ Рис. 5. Граф пространства состояний](image/5.png){#fig:005 width=70%}

Отчет:

CPN Tools state space report for:
/home/openmodelica/Desktop.cpn
Report generated: Sat Apr 12 20:05:41 2025


 Statistics
------------------------------------------------------------------------

  State Space
     Nodes:  11
     Arcs:   30
     Secs:   0
     Status: Full

  Scc Graph
     Nodes:  1
     Arcs:   0
     Secs:   0


 Boundedness Properties
------------------------------------------------------------------------

  Best Integer Bounds
                             Upper      Lower
     philosopher'philosopher_eats 1
                             2          0
     philosopher'philosopher_thinks 1
                             5          3
     philosopher'stiks_on_the_table 1
                             5          1

  Best Upper Multi-set Bounds
     philosopher'philosopher_eats 1
                         1`ph(1)++
1`ph(2)++
1`ph(3)++
1`ph(4)++
1`ph(5)
     philosopher'philosopher_thinks 1
                         1`ph(1)++
1`ph(2)++
1`ph(3)++
1`ph(4)++
1`ph(5)
     philosopher'stiks_on_the_table 1
                         1`st(1)++
1`st(2)++
1`st(3)++
1`st(4)++
1`st(5)

  Best Lower Multi-set Bounds
     philosopher'philosopher_eats 1
                         empty
     philosopher'philosopher_thinks 1
                         empty
     philosopher'stiks_on_the_table 1
                         empty


 Home Properties
------------------------------------------------------------------------

  Home Markings
     All


 Liveness Properties
------------------------------------------------------------------------

  Dead Markings
     None

  Dead Transition Instances
     None

  Live Transition Instances
     All


 Fairness Properties
------------------------------------------------------------------------
       philosopher'put_stiks 1
                         Impartial
       philosopher'take_stiks 1
                         Impartial



# Выводы

Мы построили модель задачи о мудрецах с помощью CPNTools и проанализировали результат.