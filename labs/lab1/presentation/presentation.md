---
## Front matter
lang: ru-RU
title: Работа с Oracle VM VirtualBox и системой контроля версий git
subtitle:
author:
  - Соболев М. С.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 08 снетября 2022

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'

## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase

---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Соболев Максим Сергеевич
  * Студент 4 курса, 1032192035
  * Направление: Бизнес-информатика
  * Российский университет дружбы народов
  * [sobolek322lorek@gmail.com](sobolek322lorek@gmail.com)

:::
::: {.column width="30%"}

:::
::::::::::::::

# Вводная часть

## Актуальность

- Владение git/MarkDown/Oracle VM VirtualBox и Linux жизненно необходимо для дальнейшего выполнения лабораторных работ.

## Объект и предмет исследования

- Объектом исследования является: git, Linux, Oracle VM VirtualBox, MarkDown
- Программное обеспечение для создания презентаций
- Входные и выходные форматы презентаций

## Цель

- Создать презентацию в Markdown
- Пройдемся по самым основным пунктам лабораторной работы без лишней воды

## Материал

- Отчет по ранее выполненной работе

# Выполнение работы

## Создание виртуальной машины

Указываем название, директорию установки и тип гостевой ОС. 

![1](image/1.png){ #fig:001 width=70% }


## Настраиваем диск

 Указываем объем виртуального жесткого диска, место его хранения.

![2](image/2.png){ #fig:002 width=70% }

## Настройка виртуального ЦП

Добавляем виртуальные ядра.

![3](image/3.png){ #fig:003 width=70% }

## Запускаем ВМ

Нажимаем кнопку “Start”

![4](image/4.png){ #fig:004 width=70% }


## Окно с общими сведениями о параметрах будущей установки

Перед установкой мы можем увидеть общие сведения о параметрах
будущей установки и настроить их. После настройки наблюдаем за установкой. Конец.

![5](image/5.png){ #fig:005 width=70% }



# Мы получили - установленную ОС

# Работа с GitHub

## Установка gh

gh – это утилита командной строки для управления репозиториями на GitHub.

![6](image/6.png){ #fig:006 width=70% }

## Базовая настройка git

Вводим свои данные. Настраиваем в соответствие с заданием.

![7](image/7.png){ #fig:007 width=70% }

## Настройка автоматических подписей коммитов git

Логинимся в GitHub с использованием утилиты командной строки gh.

![8](image/8.png){ #fig:008 width=70% }

## Создание репозитория курса на основе шаблона

В соответствии с заданием подготавливаем папки и создаем репозиторий
курса на основе шаблона

![9](image/9.png){ #fig:009 width=70% }

##  Настраиваем каталог курса, создаем необходимые каталоги, отправляем результат на сервер

![10](image/10.png){ #fig:010 width=70% }

## Результаты

Настроили и научились работать с git

## Итоговый слайд

- По итогу работы мы научились работать с Oracle VM VirtualBox, git, Linux, MarkDown


