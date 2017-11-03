---
layout: default
title: Си. Память.
---

# Си. Память.

## Простое исправление

### Задача
Исправьте ошибку в приведенном ниже коде, используя `malloc()`. Не забудьте использовать `valgrind`, чтобы убедиться, что вся выделенная память освобождена!

### Distribution Code
```c
#include <stdio.h>
#include <cs50.h>

int main(void)
{
    int* y;
    *y = 14;
    printf("The value y is pointing at is %i\n", *y);
}
```

***

## Регистратор

### Задача
Вы хотите создать два массива, чтобы отслеживать идентификаторы ученика и средний балл, но хотите, чтобы они были динамичными, так что если больше студентов регистрируются в будущем, вы сможете добавить их тоже. Для этого распределите память для этих массивов размера `SIZE` динамически, используя `malloc()`. Не забывайте `free()` (освобождать) эту память.

Пример:
```
./registrar
please enter student id:
47367
please enter student gpa:
3.2
please enter student id:
73923
please enter student gpa:
3.4
please enter student id:
23984
please enter student gpa:
2.9
please enter student id:
72834
please enter student gpa:
3.77

student 1
id: 47367        gpa: 3.20
student 2
id: 73923        gpa: 3.40
student 3
id: 23984        gpa: 2.90
student 4
id: 72834        gpa: 3.77
```

### Distribution Code
```c
#include <stdio.h>
#include <cs50.h>

#define SIZE 4

int main(void)
{
    // TODO: выделить память для динамических массивов и «заполните» их оба
    int* id_array = // TODO
    float* gpa_array = // TODO

    // get input with student data
    for (int i = 0; i < SIZE; i++)
    {
        printf("please enter student id:\n");
        int x = get_int();
        id_array[i] = x;
        printf("please enter student gpa:\n");
        float y = get_float();
        gpa_array[i] = y;
    }

    // print ids and gpas
    for (int i = 0; i < SIZE; i++)
    {
        printf("student %i\nid: %i \t gpa: %.2f\n", i + 1, id_array[i], gpa_array[i]);
    }

    // TODO: Освободить выделенную память
}
```

***

## Регистратор

### Задача
Одна из приятных вещей в динамической памяти - динамика. Если динамически распределенный массив заполняется, например, вы можете выделить больше памяти и «расширить» его - это то, что вам будет предложено сделать в приведенном ниже коде. Память, используемая массивом, должна быть непрерывной, поэтому вам может понадобится функция `realloc()`, которая занимается не только выделением памяти, но и также можно задать адрес в памяти, с которого нужно начинать.

Пример:
```
./dynamic
please enter 4 ints below:
1
2
3
4
static: 1       dynamic, 0x142d010: 1
static: 2       dynamic, 0x142d014: 2
static: 3       dynamic, 0x142d018: 3
static: 4       dynamic, 0x142d01c: 4
please enter an additional 4 ints below:
5
6
7
8
dynamic, 0x142d100: 1
dynamic, 0x142d104: 2
dynamic, 0x142d108: 3
dynamic, 0x142d10c: 4
dynamic, 0x142d110: 5
dynamic, 0x142d114: 6
dynamic, 0x142d118: 7
dynamic, 0x142d11c: 8
```

### Distribution Code
```c
#include <stdio.h>
#include <cs50.h>

#define SIZE 4

int main(void)
{
    // выделяется память для динамических массивов и «заполняются» оба
    int array_static[SIZE];
    int *array_dynamic = malloc(SIZE * sizeof(int));
    printf("please enter %i ints below:\n", SIZE);
    for (int i = 0; i < SIZE; i++)
    {
        int x = get_int();
        array_static[i] = x;
        array_dynamic[i] = x;
    }
    for (int i = 0; i < SIZE; i++)
    {
        printf("static: %d\tdynamic, %p: %d\n", array_static[i], array_dynamic + i, array_dynamic[i]);
    }

    // TODO: выделите дополнительную память, используя realloc (), чтобы новый динамический массив был в два раза больше
    // убедитесь, что он начинается с того же адреса в памяти, поэтому вы можете легко освободить его потом!
    printf("please enter an additional %i ints below:\n", SIZE);


    // TODO: заполнить новые «слоты» в массиве с помощью ввода от пользователя


    // print new elements in array
    for (int i = 0; i < SIZE * 2; i++)
    {
        printf("dynamic, %p: %d\n", array_dynamic + i, array_dynamic[i]);
    }

    // TODO: освободить выделенную память
}
```

***

## Скользящие указатели

### Задача
В приведенном ниже коде вводится имя пользователя, char-by-char и распечатывается.

Пример:
```
./sliding
please enter a 6-letter username, char-by-char (hit enter after each character):
d
a
v
i
d
m
The username you entered is: davidm
```

К сожалению, кодер забыл освободить память, которую он выделил! Освободите всю память кучи, используемую в приведенной ниже программе - это может быть немного сложно.
Подсказка: используйте команду «valgrind -v», чтобы получить более подробный анализ памяти, выделенной и освобожденной программой.


### Distribution Code
```c
#include <stdio.h>
#include <cs50.h>

int main(void)
{
    char* ptr = malloc(sizeof(char) * 7);
    printf("please enter a 6-letter username, char-by-char (hit enter after each character):\n");
    for (int i = 0; i < 6; i++)
    {
        *(ptr + i) = get_char();
    }

    ptr[6] = '\0';
    printf("The username you entered is: ");
    while (*ptr != '\0')
    {
        printf("%c", *ptr);
        ptr++;
    }
    printf("\n");

    // TODO: освободите память кучи
}
```