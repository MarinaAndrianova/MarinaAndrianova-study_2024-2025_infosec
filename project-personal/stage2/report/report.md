---
## Front matter
title: "Отчёт по 2 этапу индивидуального проекта"
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

Установить DVWA на дистрибутив Kali Linux.

# Выполнение 2-го этапа индивидуального проекта

Переходим в каталог html, введя команду "cd /var/www/html". Клонируем репозиторий git командой "sudo git clone https://github.com/digininja/DVWA" (рис.1).

![Рис.1:Переход в каталог и клонирование репозитория](image/1.png){#fig:001 width=70%}

Проверяем, что файлы склонировались правильно и изменяем права доступа к папке установки(рис.2).

![Рис.2:Изменение прав доступа](image/2.png){#fig:002 width=70%}

Переходим к файлу конфигурации в каталоге установки: /dvwa/config. Проверяем содержимое каталога (рис.3).

![Рис.3:Переход к файлу конфигурации](image/3.png){#fig:003 width=70%}

Копируем файл конфигурации (config.inc.php.dist) и переименовываем его на config.inc.php (рис.4).

![Рис.4:Копирование и переименование файла](image/4.png){#fig:004 width=70%}

Открываем файл настроек (рис.5) и изменяем пароль на что-то более простое для ввода (я изменю пароль на toor20) (рис.6).

![Рис.5:Открытие файла настроек](image/5.png){#fig:005 width=70%}

![Рис.6:Редактирование файла](image/6.png){#fig:006 width=70%}

Запускаем базу данных mysql и проверяем, запущен ли процесс (рис.7).

![Рис.7:Запуск mysql](image/7.png){#fig:007 width=70%}

Входим в базу данных от имени пользователя root; (пароля нет, поэтому просто нажимаем Enter при появлении запроса ввода пароля). Появляется командная строка с приглашением "MariaDB"(рис.8).

![Рис.8:Вход в базу данных](image/8.png){#fig:008 width=70%}

Далее создаём в ней нового пользователя, используя учётные данные из файла config.inc.php. Также предоставляем пользователю привилегии для работы с этой базой данных (рис.9).

![Рис.9:MariaDB](image/9.png){#fig:009 width=70%}

Для настройки сервера apache2 переходим в соответствующую директорию (рис.10).

![Рис.10:Переход в каталог apache2](image/10.png){#fig:010 width=70%}

Открываем для редактирования файл php.ini (с помощью команды "sudo nano php.ini") (рис.11), чтобы включить следующие параметры: allow_url_fopen и allow_url_include.

![Рис.11:Редактирование файла](image/11.png){#fig:011 width=70%}

Файл большой, поэтому нам потребовалось прокрутить до середины файла, чтобы добраться до fopen и изменить значения "off" на 'on'(рис.12).

![Рис.12:Fopen wrappers](image/12.png){#fig:012 width=70%}

Запускаем сервер Apache и проверяем, запущена ли служба(рис.13).

![Рис.13:Запуск сервера Apache](image/13.png){#fig:013 width=70%}

Пробуем открыть DVWA в браузере, введя в адресной строке следующее: "127.0.0.1/DVWA/". Перед нами открылась страница настройки, это означает, что мы успешно установили DVWA на Kali Linux(рис.14).

![Рис.14:Запуск DVWA в браузере](image/14.png){#fig:014 width=70%}

Прокручиваем вниз и нажимаем "Create / Reset Database" (Создать / сбросить базу данных) (рис.15).

![Рис.15:Создание базы данных](image/15.png){#fig:015 width=70%}

И через несколько секунд нас перенаправили на страницу входа в DVWA. Авторизуемся с помощью предложенных по умолчанию данных (рис.16).

![Рис.16:Авторизация](image/16.png){#fig:016 width=70%}

Оказываемся на домашней странице веб-приложения. Можем заметить, что существует множество интересных уязвимостей, которые мы можем протестировать, например, брутфорс, SQL-инъекция и другие (рис.17). На этом установка окончена.

![Рис.17:Домашняя страница DVWA](image/17.png){#fig:017 width=70%}

# Выводы

Установила веб-приложение DVWA на дистрибутив Kali Linux.
