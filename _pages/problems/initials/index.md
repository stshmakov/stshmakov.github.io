---
layout: default
title: Набор проблем 2. Crypto. Initials (Инициалы).
---

# Initials (Инициалы)

## Коротко

Создайте программу, которая при вводе полного имени будет выводить на экран инициалы.
```
$ ./initials
Regulus Arcturus Black
RAB
```

## Описание

Разработайте и реализуйте программу `initials`, которая выведет на экран инициалы человека, получив его фамилию и имя.

Начните писать вашу программу в файле `initials.c`, который будет находиться в папке `initials`.

Она должна просить пользователя ввести его полное имя (фамилия и имя на латинском) используя `get_string`, чтобы получить данные в виде `string` (строки).

Представляйте, что пользователь при вводе своего имени и фамилии будет использовать только буквы (заглавные и/или строчные) и пробел между словами. Вам не нужно имплементировать (создавать) программу таким образом, чтобы она могла работать с именем `Joseph Gordon-Levitt`, `Conan O’Brien` или `David J. Malan`!

Ваша программа должна выводить на экран инициалы (т.е. первую букву имени и фамилии) без пробелов или точек, завершаясь новой строкой (`\n`).

## Использование

Ваша программа должна проделывать тоже самое, что показано в примере ниже.
```
$ ./initials
Zamyla Chan
ZC
```
```
$ ./initials
robert thomas bowden
RTB
```
## Проверка
```
check50 cs50/2017/x/initials/less
```
Вас потребуют ввести логин (**GitHub username**) и пароль (**GitHub password**) от вашей учетной записи на Github'е, которую вы можете завести, пройдя по данной ссылке [https://github.com/join](https://github.com/join).

Зайдите на сайт [cs50.me](https://cs50.me/), используя всё ту же учетную запись GitHub'а и нажмите на зеленую кнопку **authorize submit50** (Это действие производится только один раз).