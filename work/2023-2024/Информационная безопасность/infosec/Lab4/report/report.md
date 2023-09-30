---
## Front matter
title: "Отчёт по лабораторной работе 4"
sub-title: "Дискреционное разграничение прав в Linux. Расширенные атрибуты"
author: "Ду нашсименту Висенте Феликс"

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

## 4.1. Цель работы

Получение практических навыков работы в консоли с расширенными
атрибутами файлов1.

## 4.2. Порядок выполнения работы

От имени пользователя guest определите расширенные атрибуты файла /home/guest/dir1/file1 командой
lsattr /home/guest/dir1/file1 Установите командой chmod 600 file1 на файл file1 права, разрешающие чтение и запись для владельца файла.
![рисунка 1.1](image/1.png)
![рисунка 1.2](image/2.png)
Попробуйте установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest:
  chattr +a /home/guest/dir1/file1
![рисунка 1.3](image/4.png)
![рисунка 1.6](image/5.png)
В ответ вы должны получить отказ от выполнения операции.
Зайдите на третью консоль с правами администратора либо повысьте свои права с помощью команды su. Попробуйте установить расширенный атрибут a на файл /home/guest/dir1/file1 от имени суперпользователя:
  chattr +a /home/guest/dir1/file1
От пользователя guest проверьте правильность установления атрибута: 
  lsattr /home/guest/dir1/file1
Выполните дозапись в файл file1 слова «test» командой echo "test" /home/guest/dir1/file1
После этого выполните чтение файла file1 командой cat /home/guest/dir1/file1У бедитесь, что слово test было успешно записано в file1.
Попробуйте удалить файл file1 либо стереть имеющуюся в нём информацию командой
echo "abcd" > /home/guest/dirl/file1 Попробуйте переименовать файл.
Попробуйте с помощью команды
![рисунка 1.6](image/6.png)
chmod 000 file1
![рисунка 1.7](image/7.png)
установить на файл file1 права, например запрещающие чтение и запись для владельца файла. Удалось ли вам успешно выполнить указанные команды?
Снимите расширенный атрибут a с файла /home/guest/dirl/file1 от имени суперпользователя командой chattr -a /home/guest/dir1/file1
Повторите операции, которые вам ранее не удавалось выполнить. Ваши наблюдения занесите в отчёт.
Повторите ваши действия по шагам, заменив атрибут «a» атрибутом «i».
Удалось ли вам дозаписать информацию в файл? Ваши наблюдения занесите в отчёт.
В результате выполнения работы вы повысили свои навыки использования интерфейса командой строки (CLI), познакомились на примерах с тем, как используются основные и расширенные атрибуты при разграничении доступа. Имели возможность связать теорию дискреционного разделения доступа (дискреционная политика безопасности) с её реализацией на практике в ОС Linux. Составили наглядные таблицы, поясняющие какие операции возможны при тех или иных установленных правах. Опробовали действие на практике расширенных атрибутов «а» и «i».

![рисунка 1.6](image/8.png)
![рисунка 1.6](image/9.png)

## Выводы

Без разрешений администратора вы не сможете создавать, редактировать, удалять или открывать файл, и это может быть эффективным способом защиты ваших данных
