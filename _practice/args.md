---
layout: default
title: Си. Аргументы.
---

# Си. Аргументы.

## Bye Bye Birdie (https://www.youtube.com/watch?v=1t3cBTb3xPc)

### Задача
Вспомнили привет мир? Время прощаться! Напишите короткую программу, которая принимает имя в качестве аргумента командной строки и напечатает «bye bye [name]»
Совет. Не забудьте проверить ошибку для правильного количества аргументов командной строки!

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(int argc, string argv[])
{
    // TODO
}
```

***

## echo

### Задача
`echo` - это команда Unix, которая, согласно странице руководства, «отображает `[s] `строку текста».

Например:
```
echo This is CS50
This is CS50
```

Реализуйте свою собственную версию команды `echo`. Вы захотите перебрать аргументы пользователя и распечатать их один за другим, добавив промежуток между ними. Сначала вы можете попробовать выполнить команду `echo` на своем устройстве, чтобы получить представление о том, как это работает. Совет. Не забудьте проверить ошибку для правильного количества аргументов командной строки!

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(int argc, string argv[])
{
    // TODO

    return 0;
}
```

***

## Сигма

### Задача
Напишите код, который принимает аргументы командной строки как `int`’ы (функция `atoi()` может пригодиться) и распечатывает их сумму.

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(int argc, string argv[])
{
    // TODO

    return 0;
}
```

***

## Число

### Задача
Напишите программу, которая выводит общее количество символов в аргументах командной строки, заданных программе. Игнорировать пробелы (например, пробелы, символы новой строки и символы табуляции) и игнорировать имя программы. Например:
`./a.out foo` должен указывать, что были указаны 3 символа. `./a.out foo bar baz` должен указывать, что были указаны 9 символов. `./a.out` должен указывать, что были указаны 0 символов.

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(int argc, string argv[])
{
    // TODO

    return 0;
}
```

***

## Trieste

### Задача
Прочтите приведенный ниже код. Не меняя код, запустите программу с правильными аргументами командной строки, чтобы она печатала слово «Trieste» (https://www.becasinternacionales.net/webapp/img/imgpro/50c754_triestre-italia_w600.jpg) порт города на побережье Адриатического моря).

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(int argc, string argv[])
{
	// input verification
    if (argc < 5)
    {
        printf("You're gonna need more words for this to work!\n");
        return 1;
    }

    printf("%c", argv[1][0]);
    printf("%c", argv[4][3]);
    printf("%c", argv[2][2]);
    printf("%c", argv[3][5]);
    printf("%c", argv[4][0]);
    printf("%c", argv[2][0]);
    printf("%c", argv[1][6]);
    printf("\n");

    return 0;
}
```