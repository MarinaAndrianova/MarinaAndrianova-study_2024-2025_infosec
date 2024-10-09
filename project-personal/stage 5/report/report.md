---
## Front matter
title: "Отчёт по 5 этапу индивидуального проекта"
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

Научиться использовать Burp Suite в Kali Linux.

# Задание

Использование Burp Suite.

# Выполнение 5-го этапа индивидуального проекта

Запускаю локальный сервер, на котором открываю веб-приложение DVWA для тестирования инструмента Burp Suite (рис. [-@fig:001]).

![Запуск локального сервера](image/1.png){#fig:001 width=70%}

Запускаю инструмент Burp Suite (рис. [-@fig:002]).

![Запуск приложения](image/2.png){#fig:002 width=70%}

Открываю сетевые настройки браузера, для подготовке к работе (рис. [-@fig:003]).

![Сетевые настройки браузера](image/3.png){#fig:003 width=70%}

Изменение настроек сервера для работы с proxy и захватом данных с помощью Burp Suite (рис. [-@fig:004]).

![Настройки сервера](image/4.png){#fig:004 width=70%}

Изменяю настройки Proxy инструмента Burp Suite для дальнейшей работы (рис. [-@fig:005]).

![Настройки Burp Suite](image/5.png){#fig:005 width=70%}

Во вкладке Proxy меняю "Intercept is off" на "Intercept is on" (рис. [-@fig:006] и [-@fig:007]).

![Настройки Proxy](image/6.png){#fig:006 width=70%}

![Настройки Proxy](image/7.png){#fig:007 width=70%}

Чтобы Burp Suite исправно работал с локальным сервером, наобходимо установить параметр `network_allow_hijacking_loacalhost` на `true` (рис. [-@fig:008] и [-@fig:009]).

![Настройки параметров](image/8.png){#fig:008 width=70%}

![Настройки параметров](image/9.png){#fig:009 width=70%}

Пытаюсь зайти в браузере на DVWA, тут же во вкладки Proxy появляется захваченный запрос. Нажимаем "Forward", чтобы загрузить страницу (рис. [-@fig:010]).

![Получаемые запросы сервера](image/10.png){#fig:010 width=70%}

Загрузилась страница авторизации, текст запроса поменялся (рис. [-@fig:011] и [-@fig:012]).

![Страница авторизации](image/11.png){#fig:011 width=70%}

![Изменение запроса](image/12.png){#fig:012 width=70%}

История запросов хранится во вкладке Target (рис. [-@fig:013]).

![История запросов](image/13.png){#fig:013 width=70%}

Попробуем ввести неправильные, случайные данные в веб-приложении и нажмем `Login`. В запросе увидим строку, в которой отображаются введенные нами данные, то есть поле для ввода (рис. [-@fig:014]).

![Ввод случайных данных](image/14.png){#fig:014 width=70%}

Этот запрос так же можно найти во вкладке Target, там же жмем правой кнопкой мыши на хост нужного запроса, и далее нажимаем "Send to Intruder" (рис. [-@fig:015]).

![POST-запрос с вводом пароля и логина](image/15.png){#fig:015 width=70%}

Попадаем на вкладку Intruder, видим значения по умолчанию у типа атаки и наш запрос (рис. [-@fig:016]).

![Вкладка Intruder](image/16.png){#fig:016 width=70%}

Изменяем значение типа атаки на Cluster bomb и проставляем специальные символы у тех данных в форме для ввода, которые будем пробивать, то есть у имени пользователя и пароля (рис. [-@fig:017]).

![Изменение типа атаки](image/17.png){#fig:017 width=70%}

Так как мы отметили два параметра для подбора, то нам нужно два списка со значениями для подбора. Заполняем первый список в `Payload setting` (рис. [-@fig:018]).

![Первый Simple list](image/18.png){#fig:018 width=70%}

Переключаемся на второй список и добавляем значения в него. В строке request count видим нужное количество запросов, чтобы проверить все возможные пары пользователь-пароль (рис. [-@fig:019]).

![Второй Simple list](image/19.png){#fig:019 width=70%}

Запускаю атаку (рис. [-@fig:020]) и начинаю подбор (рис. [-@fig:021]).

![Запуск атаки](image/20.png){#fig:020 width=70%}

![Подбор логина и пароля](image/21.png){#fig:021 width=70%}

При открытии результата каждого post-запроса можно увидеть полученный get-запрос, в нем видно, куда нас перенаправило после выполнения ввода пары пользователь-пароль. В представленном случае с подбором пары admin-admin нас перенаправило на login.php, это значит, что пара не подходит (рис. [-@fig:022]).

![Результат запроса](image/22.png){#fig:022 width=70%}

Проверим результат пары admin-password во вкладке Response, теперь нас перенаправляет на страницу index.php, значит пара должна быть верной (рис. [-@fig:023]).

![Результат запроса](image/23.png){#fig:023 width=70%}

Дополнительная проверка с использованием Repeater, нажимаем на нужный нам запрос правой кнопкой мыши и жмем "Send to Repeater". Переходим во вкладку "Repeater" (рис. [-@fig:024]).

![Вкладка Repeater после доп. проверки результата](image/24.png){#fig:024 width=70%}

Нажимаем "send", получаем в Response в результат перенаправление на index.php (рис. [-@fig:025]).

![Окно Response](image/25.png){#fig:025 width=70%}

После нажатия на `Follow redirection`, получим нескомпилированный html код в окне Response (рис. [-@fig:026]).

![Изменение в окне Response](image/26.png){#fig:026 width=70%}

Далее в подокне Render получим то, как выглядит полученная страница (рис. [-@fig:027]).

![Полученная страница](image/27.png){#fig:027 width=70%}

# Выводы

При выполнении 5-го этапа индивидуального проекта научилась использовать инструмент Burp Suite в Kali Linux.

# Список литературы{.unnumbered}

1. Парасрам, Ш. Kali Linux: Тестирование на проникновение и безопасность : Для профессионалов. Kali Linux / Ш. Парасрам, А. Замм, Т. Хериянто, и др. – Санкт-Петербург : Питер, 2022. – 448 сс.