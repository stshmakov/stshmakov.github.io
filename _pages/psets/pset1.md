---
layout: default
title: Набор проблем 1. C.
---
# Набор проблем 1: C

## С чего начать

CS50 IDE или "integrated development environment" - это среда разработки, которая позволяет программировать "в облаке," без установки каких-либо программ на вашей локальной машине (компьютере). Под капотом находится популярная операционная система, Ubuntu Linux (с пингвинчиком), которая помещается в "контейнер" при помощи программы с открытым исходным кодом Docker. Она позволяет нескольким пользователям (таким как вы!) делиться "ядром" операционной системы (его зародышем, так сказать) и файлами, при этом еще обладает и своими отдельными файлами. Просто невообразимо, CS50 IDE предоставляет вам ваше собственное "рабочее место" (т.е. память на удаленном компьютере), в котором вы можете сохранять свои файлы и папки (ака директории).

## Вход в систему

Зарегистрируйтесь на [edX](https://edx.org/) и обязательно подтвердите свой аккаунт через письмо, которое вам вышлют на почту. Далее сюда [запись на курс CS50](https://www.edx.org/course/introduction-computer-science-harvardx-cs50x), нажмите на зеленую кнопку "Enroll Now".

Также вам необходимо завести учетную запись на Github'е, пройдите по данной ссылке [https://github.com/join](https://github.com/join).

Зайдите на сайт [cs50.me](https://cs50.me/), используя всё ту же учетную запись GitHub'а и нажмите на зеленую кнопку **authorize submit50** (Это действие производится только один раз).

Теперь вы можете пользоваться средой разработки CS50.

Перейдите по ссылке [cs50.io](https://cs50.io/), выберите edX и зайдите в CS50 IDE. Вас, возможно, попросят (повторно) ввести email и пароль от учетной записи edX.

## Подготовка

В нижней части CS50 IDE есть "terminal" или терминальное окно (светло-синее, по умолчанию), или интерфейс командной строки (command-line interface - CLI), который позволяет управлять папкой workspace, ее файлами и папками, компилировать код, запускать программы и даже устанавливать новые программы. В окне терминала вы увидите следующее
```
~/workspace/ $
```
Кликните по окошку терминала и напечатайте
```
update50
```
нажмите кнопку <kbd>Enter</kbd>. Это для того, чтобы ваше рабочее пространство загрузило все необходимые обновления. Процесс обновления может занять несколько минут. (Ни в коем случае не закрывайте окно CS50 IDE в вашем браузере, пока все не закончится!)

Далее, выполните
```
mkdir ~/workspace/pset1/
```
чтобы создать папку `pset1` в вашей директории `workspace`. Не пропустите пробел между `mkdir` и `~/workspace/pset1` или какой-либо другой символ! Помните, что `~` представляет вашу основную папку, первую. `~/workspace` представляет папку под названием `workspace` и `~/workspace/pset1` представляет другую папку `pset1`, которая находится в `~/workspace`.

Теперь выполните
```
cd ~/workspace/pset1/
```
чтобы перейти (т.е. открыть) в эту папку. В вашем терминале должно быть следующее.
```
~/workspace/pset1/ $
```
Если это не так, тогда вернитесь обратно и посмотрите, где вы допустили ошибку. Вы можете выполнить команду
```
history
```
в терминале, чтобы увидеть последние выполненные вами команды. Вы также можете использовать стрелки вашей клавиатуры вверх и вниз, чтобы пройтись по истории использованных команд.

# Требования

* Реализовать [Hello]({{ "/problems/hello/" | relative_url }})
* Реализовать [Water]({{ "/problems/water/" | relative_url }})
* Реализовать [Mario]({{ "/problems/mario/" | relative_url }})
* Реализовать [Cash]({{ "/problems/greedy/" | relative_url }})
