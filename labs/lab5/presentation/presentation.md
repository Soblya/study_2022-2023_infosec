---
## Front matter
lang: ru-RU
title: Дискреционное разграничение прав в Linux. Исследование влияния дополнительных атрибутов
subtitle:
author:
  - Соболев М. С.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 6 октября 2022

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

- Продолжаем изучать дискреционное разграничение прав в Linux.

## Объект и предмет исследования

- Объектом исследования являются: исследование влияния дополнительных атрибутов
- Закрепление теоретических основ

## Цель

- Получение практических навыков работы с дополнительными атрибутами

## Материал

- Отчет по ранее выполненной работе

# Выполнение лабораторной работы часть 1

## 1

Входим в систему от имени пользователя guest.

![1](image/1.png){ #fig:001 width=70% }

## 2

Создаем программу

![2](image/2.png){ #fig:002 width=70% }

## 3

Комплилируем программу и убеждаемся, что файл программы создан: gcc simpleid.c -o simpleid

![3](image/3.png){ #fig:003 width=70% }

## 4

Выполняем программу simpleid:./simpleid

![4](image/4.png){ #fig:004 width=70% }
## 5

Выполняем системную программу id: id и сравниваем полученный результат с данными предыдущего пункта задания.

![5](image/5.png){ #fig:005 width=70% }

## 6

Усложняем программу, добавив вывод действительных идентификаторов

![6](image/6.png){ #fig:006 width=70% }

Получившуюся программу называем simpleid2.c.

## 7

Компилируем и запускаем simpleid2.c: gcc simpleid2.c -o simpleid2 
./simpleid2

![7](image/7.png){ #fig:007 width=70% }

## 8

От имени суперпользователя выполняем команды:
chown root:guest /home/guest/simpleid2
chmod u+s /home/guest/simpleid2

![8](image/8.png){ #fig:008 width=70% }

## 9

Повысьте временно свои права с помощью su. sudo позволяет выполнить команду от имени суперпользователя. su позволяет войти от имени другого пользователя, в том числе root.

## 10

Выполняем проверку правильности установки новых атрибутов и смены владельца файла simpleid2: ls -l simpleid2

![10](image/10.png){ #fig:010 width=70% }

## 11

Запускаем simpleid2 и id:./simpleid2 id и сравниваем результаты

![11](image/11.png){ #fig:011 width=70% }

## 12

Проделываем тоже самое относительно SetGID-бита

![12.1](image/12.1.png){ #fig:012.1 width=70% }

![12.2](image/12.2.png){ #fig:012.2 width=70% }

## 13

Создаем программу readfile.c:

![13](image/13.png){ #fig:013 width=70% }

## 14

Компилируем её.
gcc readfile.c -o readfile

![14](image/14.png){ #fig:014 width=70% }

## 15

Сменяем владельца у файла readfile.c и изменяем права так, чтобы только суперпользователь мог прочитать его, a guest не мог

![15](image/15.png){ #fig:015 width=70% }

## 16

Проверяем, что пользователь guest не может прочитать файл readfile.c.

![16](image/16.png){ #fig:016 width=70% }

Получившуюся программу называем simpleid2.c.

## 17

Меняем у программы readfile владельца и устанавливаем SetU’D-бит.

![17](image/17.png){ #fig:017 width=70% }

## 18

Проверяем, может ли программа readfile прочитать файл readfile.c?

![18](image/18.png){ #fig:018 width=70% }

Чтение файла невозможно, программа выдаёт segfault при попытке чтения файлов

## 19

Проверяем, может ли программа readfile прочитать файл /etc/shadow?

![19](image/19.png){ #fig:019 width=70% }

Чтение файла невозможно, программа выдаёт segfault при попытке чтения файлов.
При этом попытка чтения файла без атрибута +s, принадлежащего пользователю guest происходит без проблем 
***
# Выполнение лабораторной работы часть 2

## 1

Выясняем, установлен ли атрибут Sticky на директории /tmp, для чего выполняем команду
ls -l / | grep tmp

![2.1](image/2.1.png){ #fig:02.1 width=70% }

## 2

От имени пользователя guest создаем файл file01.txt в директории /tmp
со словом test:
echo "test" > /tmp/file01.txt

![2.2](image/2.2.png){ #fig:02.2 width=70% }

## 3

Просматриваем атрибуты у только что созданного файла и разрешаем чтение и запись для категории пользователей «все остальные»:
ls -l /tmp/file01.txt
chmod o+rw /tmp/file01.txt
ls -l /tmp/file01.txt

![2.3](image/2.3.png){ #fig:02.3 width=70% }

## 4

От пользователя guest2 попробуем прочитать файл /tmp/file01.txt:
cat /tmp/file01.txt

![2.4](image/2.4.png){ #fig:02.4 width=70% }
## 5

От пользователя guest2 попробуем дозаписать в файл
/tmp/file01.txt слово test2 командой echo "test2" > /tmp/file01.txt

![2.5](image/2.5.png){ #fig:02.5 width=70% }

## 6

Проверьте содержимое файла командой
cat /tmp/file01.txt

![2.6](image/2.6.png){ #fig:02.6 width=70% }

## 7

От пользователя guest2 попробуем записать в файл /tmp/file01.txt
слово test3, стерев при этом всю имеющуюся в файле информацию командой
echo "test3" > /tmp/file01.txt

![2.7](image/2.7.png){ #fig:02.7 width=70% }

## 8

Проверяем содержимое файла командой
cat /tmp/file01.txt

![2.8](image/2.8.png){ #fig:02.8 width=70% }

## 9

От пользователя guest2 попробуем удалить файл /tmp/file01.txt командой
rm /tmp/fileOl.txt

![2.9](image/2.9.png){ #fig:02.9 width=70% }

## 10

Повышаем свои права до суперпользователя следующей командой su -
и выполняем после этого команду, снимающую атрибут t (Sticky-бит) с директории /tmp: chmod -t /tmp

![2.10](image/2.10.png){ #fig:02.10 width=70% }

## 11

Покидаем режим суперпользователя командой exit


![2.11](image/2.11.png){ #fig:02.11 width=70% }

## 12

От пользователя guest2 проверяем, что атрибуты t у директории /tmp нет:
ls -l / | grep tmp

## 13

Запись и дозапись работают без изменений, удаление файла стало доступно

![2.13](image/2.13.png){ #fig:02.13 width=70% }

## 14

Да удалось

![2.14](image/2.14.png){ #fig:02.14 width=70% }

## 15

Повышаем свои права до суперпользователя и возвращаем атрибут t на директорию /tmp:
su -
chmod +t /tmp
exit


![2.15](image/2.15.png){ #fig:02.15 width=70% }

# Выводы

Мы изучили механизмы изменения идентификаторов, применение SetUID- и Sticky-битов. Получили практические навыки работы в консоли с дополнительными атрибутами. Рассмотрели работу механизма смены идентификатора процессов пользователей, а также влияние бита Sticky на запись и удаление файлов.