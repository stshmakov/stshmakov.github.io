---
layout: default
title: Си. ASCII
---

# Си. ASCII.

## Проверщик

### Задача
Вспомните верификатор из задач по функциям, который принимает три целых числа и проверяет, является ли третье число суммой первых двух. Студент, который пытался решить эту задачу, случайно прочитал что необходимо ввести символы, а не целые числа. Чтобы исправить этот верификатор, напишите функцию, которая принимает символ между `0-9` и возвращает эквивалентный `int`! Вы также должны внести некоторые изменения в функцию `main`.

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>

// прототипы функций TODO: добавить функцию char_to_int
bool verifier(int a, int b, int c);

int main(void)
{
    printf("Enter the first int you are adding (between 0-9): ");
    char x_1 = get_char();
    printf("Enter the second int you are adding (between 0-9): ");
    char y_1 = get_char();
    printf("Enter the result: ");
    char z_1 = get_char();

    // TODO: поменяйте, то что пользователь ввел на целые числа (использовать функцию char_to_int), и используйте их для проверки результата, напечатайте 'correct!' или 'incorrect!'

}

// Реализация функций
bool verifier(int a, int b, int c)
{
	if (a + b == c)
    		return true;
	return false;
}
// TODO: Добавить реализацию функции char_to_int
```

***

## Простой шифр

### Задача
В приведенном ниже коде есть скрытое сообщение, зашифрованное простым сдвигом букв: кодировка это сдвиг 5 символов от обычного стандарта ascii (например, «A» печатается как «F»). Измените одну строку кода, чтобы исправить это и открыть скрытое сообщение. Вы можете игнорировать остальную часть кода, которая содержит строку и массив - понятия, которые, возможно, еще не охвачены.

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    char message[] = "[tnqf&";

    printf("The hidden message is: ");
    for (int i = 0, n = strlen(message); i < n; i++)
    {
    	// TODO: сдвиньте значение символа на 5 в строке ниже!
    	message[i] =
    	printf("%c", message[i]);
    }
    printf("\n");
}
```
[Решение]({{ "/practice/solutions/simplecipher.html" | relative_url }})

***

## toupper

### Задача
Реализуйте функцию `toupper` самостоятельно! Функция должна принимать в качестве параметра символ в нижнем регистре и переводить его в верхний регистр.

Пример:
```
./toupper
Please enter a lowercase character: l
The capitalized letter is: L
```

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>

// TODO: написать прототип функции

int main(void)
{
    char c;
    do
    {
        printf("Please enter a lowercase alphabetical character: ");
        c = get_char();
    }
    // TODO: напишите условие, чтобы проверить, что ввод действительно является строчным символом
    while();

    c = toupper(c);
    printf("The capitalized letter is: %c\n", c);
}

// TODO: write the function definition

```

***

## Строчная или заглавная

### Задача
Реализуйте следующую программу, которая предложит пользователю ввести алфавитный символ и определит, имеет ли символ верхний или нижний регистр.

Пример:
```
./upperlower
Please enter an alphabetical character: Z
You printed an uppercase letter!
```

### Distribution Code
Нет

[Решение]({{ "/practice/solutions/upperlower.html" | relative_url }})