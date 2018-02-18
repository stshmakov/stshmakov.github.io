---
layout: default
title: Набор проблем 6. Sentimental. Сентиментальный.
---
# Набор проблем 6. Sentimental. Сентиментальный.

# Коротко
Портируйте (перепишите) некоторые программы с Си на Python.

Проанализируйте кое-какие настроения.

## С чего начать
```
update50
mkdir ~/workspace/pset6/
cd ~/workspace/pset6/
```

## Проблемы
Весь ваш код должен соответствовать [Общепринятому Стилю Написания Кода](http://defpython.ru/pep8) на Python, по-другому известный как PEP 8.

1. Имплементируйте программы, используя Python:

    * Напишите код [Mario]({{ "/problems/mario/" | relative_url }}) в файле `mario.py`, который будет находиться в папке `pset6/`.

    * Напишите код [Cash]({{ "/problems/greedy/" | relative_url }}) в файле `cash.py`, который будет находиться в папке `pset6/`.

2. Имплементируйте любую (одну) программу, используя Python:

    * Напишите код [Caesar]({{ "/problems/caesar/" | relative_url }}) в файле `caesar.py`, который будет находиться в папке `pset6/`.

    * Напишите код [Vigenère]({{ "/problems/vigenere/" | relative_url }}) в файле `vigenere.py`, который будет находиться в папке `pset6/`.

Имплементируйте Sentiments (Настроения) в папке `pset6/sentiments/`.

## Проверка
```
check50 cs50/2018/x/sentimental/hello
check50 cs50/2018/x/sentimental/mario/less
check50 cs50/2018/x/sentimental/cash
check50 cs50/2018/x/sentimental/caesar
check50 cs50/2018/x/sentimental/vigenere
```

## Стиль
```
style50 hello.py
style50 mario.py
style50 cash.py
style50 caesar.py
style50 vigenere.py
```

## Закачать
```
submit50 cs50/2018/x/sentimental/hello
submit50 cs50/2018/x/sentimental/mario/less
submit50 cs50/2018/x/sentimental/cash
submit50 cs50/2018/x/sentimental/caesar
submit50 cs50/2018/x/sentimental/vigenere
```

## Подсказки
Обязательно используйте Python 3, а не Python 2.

Если программа находится в, к примеру, `foo.py`, вы можете запустить ее с помощью команды `python foo.py`.

Для реализации программ Mario, Greedy, Caesar и Vigenère, с вашей стороны будет **разумнее** брать в качестве примера свою собственную имплементацию данных проблем на языке Си и имплементацию других разработчиков, опять же на Си. **Не разумно** будет смотреть на чужой код этих имплементаций, если они написаны на Python. Также **не разумно** смотреть на чужую имплементацию программы Sentiments.

Рассматривайте этот набор проблем как возможность не только портировать (перенести) свои предыдущие работы с Си на Python, но и возможность улучшить ваш прежний дизайн кода, используя приобретенные вами навыками!

Вам возможно захочется разделить рабочую среду CS50 IDE на две части, чтобы легче было портировать код с Си на Python. Выберите в меню **View > Layout > Horizontal Split** для отображения двух окон редактирования кода.

Вам дозволяется пользоваться "Питоновской" библиотекой CS50, которая включает функции `get_float`, `get_int` и `get_string`. Просто не забудьте добавить в верхней части вашего кода
```
import cs50
```
Или вы можете воспользоваться функцией [`input`](https://docs.python.org/3/library/functions.html#input) и самостоятельно реализовать проверку вводимых пользователем данных.

Вы возможно найдете для себя полезным использовать функции [`chr`](https://docs.python.org/3/library/functions.html#chr) и [`ord`](https://docs.python.org/3/library/functions.html#ord).
