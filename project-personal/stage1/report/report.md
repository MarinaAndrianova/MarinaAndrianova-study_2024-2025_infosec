---
## Front matter
title: "Отчёт по 1 этапу индивидуального проекта"
subtitle: "Дисциплина: Информационная безопасность"
author: "Андрианова Марина Георгиевна"

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

Установить дистрибутив Kali Linux в виртуальную машину.

# Выполнение 1-го этапа индивидуального проекта

Скачиваю дистрибутив Kali Linux с официального сайта: https://www.kali.org/ (рис.1)

![Рис.1:Дистрибутив Kali Linux](image/1.png){#fig:001 width=70%}

В VB нажала на кнопку «Создать». В поле «Имя» вписывала «Kali Linux». Программа распознала дистрибутив, и поля «Тип», «Версия» заполнила самостоятельно(рис.2).

![Рис.2:Имя и тип ОС](image/2.png){#fig:002 width=70%}

Выбираем оборудование (рис.3) и виртуальный жесткий диск (рис.4). Этап создания виртуальной машины закончился (рис.5)

![Рис.3:Оборудование](image/3.png){#fig:003 width=70%}

![Рис.4:Виртуальный жесткий диск](image/4.png){#fig:004 width=70%}

![Рис.5:Итог создания виртуальной машины](image/5.png){#fig:005 width=70%}

В настройках добавляем скачанный образ Kali Linux (рис.6 и рис.7). Изменяем параметры системы (рис.8)

![Рис.6:Добавление скачанного образа Kali Linux](image/6.png){#fig:006 width=70%}

![Рис.7:Добавление скачанного образа Kali Linux](image/7.png){#fig:007 width=70%}

![Рис.8:Параметры системы](image/8.png){#fig:008 width=70%}

После выбора образа попала в загрузочное меню Kali. Выбрала тип установки: основной вариант без дополнительных настроек и тонкостей — это «Graphical install» (рис.9).

![Рис.9:Тип установки](image/9.png){#fig:009 width=70%}

Выбрала язык, который будет использоваться для установки и в дальнейшем в самой операционной системе (рис.10).

![Рис.10:Выбор языка](image/10.png){#fig:010 width=70%}

Указала своё местонахождение (страну), чтобы система смогла настроить часовой пояс (рис.11).

![Рис.11:Местонахождение](image/11.png){#fig:011 width=70%}

Выбрала раскладку клавиатуры, которой пользуюсь на постоянной основе (рис.12) и указала предпочтительный способ переключения языков на клавиатуре (рис.13).

![Рис.12:Раскладка клавиатуры](image/12.png){#fig:012 width=70%}

![Рис.13:Способ переключения языков](image/13.png){#fig:013 width=70%}

После начнется автоматическая настройка параметров операционной системы (рис.14).

![Рис.14:Настройка параметров ОС](image/14.png){#fig:014 width=70%}

Установщик предложил создать учетную запись суперпользователя. Создала безопасный пароль и ввела его в оба поля (рис.15).

![Рис.15:Создание безопасного пароля](image/15.png){#fig:015 width=70%}

Продолжится автоматическая настройка параметров системы - разметка дисков (рис.16-20).

![Рис.16:Настройка параметров системы](image/16.png){#fig:016 width=70%}

![Рис.17:Настройка параметров системы](image/17.png){#fig:017 width=70%}

![Рис.18:Разметка дисков](image/18.png){#fig:018 width=70%}

![Рис.19:Разметка дисков](image/19.png){#fig:019 width=70%}

![Рис.20:Разметка дисков](image/20.png){#fig:020 width=70%}

Устанавливаем менеджер пакетов (рис.21).

![Рис.21:Установка менеджера пакетов](image/21.png){#fig:021 width=70%}

Разрешила установку системного загрузчика GRUB (рис.22).

![Рис.22:Установка GRUB](image/22.png){#fig:022 width=70%}

Дождалась завершения установки (рис.23-25).

![Рис.23:Завершение установки](image/23.png){#fig:023 width=70%}

![Рис.24:Завершение установки](image/24.png){#fig:024 width=70%}

![Рис.25:Завершение установки](image/25.png){#fig:025 width=70%}

Система попросила ввести имя пользователя, т. е. слово «root» (рис.26).

![Рис.26:Имя пользователя](image/26.png){#fig:026 width=70%}

После успешного входа я попала на рабочий стол Kali. Теперь могу начинать знакомиться с этой операционной системой и настраивать ее (рис.27).

![Рис.27:Рабочий стол Kali](image/27.png){#fig:027 width=70%}

# Выводы

Установила дистрибутив Kali Linux в виртуальную машину.
