---
layout: default
title: Си. Указатели.
---

# Си. Указатели.

## ASCII Puzzle

### Задача
Передайте семь символов в `printf()`, чтобы ваш код печатал слово «POINTER». Подсказка: каждый символ можно использовать только один раз.

Пример:
```
./puzzle
POINTER
```

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
   int s = 65;
   int *t = &s;

   char C = 'I';
   char N = s + 'P' - 'A';
   char B = *t - s + N + 2;
   char E = &s - t + 78;
   char J = *t + 19;
   char I = N + 'A' - s - 1;
   char O = 347/5;

   // TODO: Выведи "POINTER" используя вышеуказанные символы
}
```

***

## Привязка

### Задача
В приведенном ниже коде измените только одну строку (помеченную), чтобы напечатать `final value` 6.0.

Пример:
```
./referencing
x is 4.00, y is 3.00.
The final value is: 6.00
```

Подсказка: напомним, что `a[i]` обрабатывается компилятором точно так же, как этот `*(a + i)`.

### Distribution Code
```c
#include <stdio.h>
#include <cs50.h>

int main(void)
{
    float x = 4.0;
    printf("x is %.2f, ", x);
    float y = 3.0;
    printf("y is %.2f.\n", y);
    float *xp = &x; // TODO: отредактируйте эту строку, и только правую часть уравнения
    float *yp = &y;
    printf("The final value is: %.2f\n", *xp + *yp);
}
```

***

## strchr

### Задача
Реализуйте `strchr()`, стандартную функцию, которая возвращает подстроку строки C, которая начинается с заданного символа. Если символ не находится в строке, функция должна вернуть NULL.

Пример:
```
./strchr
String: happy cat
Character: a
Looking for substring...
Substring: appy cat
```

Подсказка: напомним, что `a[i]` обрабатывается компилятором точно так же, как этот `*(a + i)`.

### Distribution Code
```c
#include <stdio.h>
#include <cs50.h>
#include <string.h>

char* my_strchr(char* str, char c)
{
   // TODO
}

int main(void)
{
    printf("String: ");
    char* str = get_string();
    printf("Character: ");
    char c = get_char();
    printf("Looking for substring...\n");
    char* result = my_strchr(str, c);
    if (result == NULL)
    {
        printf("Couldn't find %c.\n", c);
    }
    else
    {
        printf("Substring: %s \n", result);
    }
}
```

***

## Перестановка

### Задача
Внедрить функцию перестановки с прототипом `void swap (int * a, int * b)`, который меняет значения с помощью указателей.

Пример:
```
./swap
x is 1
y is 2
Swapping...
Swapped!
x is 2
y is 1
```

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>

void swap(int* a, int* b);

int main(void)
{
    int x = get_int("please enter value of x: ");
    int y = get_int("please enter value of y: ");

    // swap and print
    printf("x is %i\n", x);
    printf("y is %i\n", y);
    printf("Swapping...\n");
    swap(&x, &y);
    printf("Swapped!\n");
    printf("x is %i\n", x);
    printf("y is %i\n", y);

}

void swap(int* a, int* b)
{
    // TODO
}
```