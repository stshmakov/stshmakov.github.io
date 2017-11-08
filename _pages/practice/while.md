---
layout: default
title: Си. Циклы while.
---

# Си. Циклы `while`.

## Сияние

### Задача
Джек сошел с ума, написав рукопись. Убедитесь, что он набирает «All work and no play makes Jack a dull boy.» ровно 10 раз, и не более! Вам разрешено редактировать только одну строку в коде, которая помечена комментарием «TODO»

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    string s = "All work and no play makes Jack a dull boy.";
    int i = 0;
    while(i < 120)
    {
        printf("%s\n", s);
        i += 1; // TODO: Это единственная строка, которую вы можете редактировать!
    }
    return 0;
}
```

***

## Умножение

### Задача
Представьте себе, что единственная доступная вам математическая операция - это сложение. Возьмите два целых числа: `x` и `y`, в качестве ввода - и используйте цикл `while` чтобы найти и распечатать их произведение.


### Distribution Code
Нет

***

## Секретное сообщение

### Задача
Напишите цикл, чтобы распечатать каждый третий символ в следующем коде, чтобы открыть скрытое сообщение. Если вы хотите, вы можете включить любые дополнительные библиотеки, кроме тех, которые предусмотрены в распространяемом коде.


### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    // скрытое сообщение для декодирования
    string s = "asTJhhJKikJswe hkij;sop /bCurSN;5PK0es";

    // TODO: напишите цикл while для печати каждого третьего символа в строке и откройте скрытое сообщение

    // все сделано!
    return 0;
}
```