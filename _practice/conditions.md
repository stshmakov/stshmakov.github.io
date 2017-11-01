---
layout: default
title: Си. Условия.
---

# Си. Условия.

## Дети

### Задача
Напишите программу, которая побуждает пользователя задуматься о среднем числе детей на семью в России. Сообщите пользователю, правильно ли он дал ответ!

Пример вывода:
```
./kids
Average number of children per family in Russia: 2
That is correct!

./kids
Average number of children per family in Russia: 1
That is incorrect!
```

### Distribution Code
Нет

***

## Театр

### Задача
Перепишите следующую программу, которая определяет вам цену театрального билета на основе вашей возрастной группы - заменив операторы **`if` тернарным оператором**. Возрастная группа 1 состоит из детей и пожилых людей, а возрастная группа 2 состоит из всех других демографических групп.

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>
int main(void)
{
    // query user for input
    int age_group;
    do
    {
        printf("Which age group are you a member of, 1 (children and seniors) or 2 (adults)? ");
        age_group = get_int();
    }
    while (age_group < 1 || age_group > 2);

    // TODO: переписать условие с использованием тернарного оператора
    int ticket_price;
    if (age_group == 1)
        ticket_price = 20;
    else
        ticket_price = 50;
    printf("The ticket cost is $%d\n", ticket_price);
}
```

***

## Оценки

### Задача
В этой программе есть ошибка, так как если пользователь вводит номер 95, все четыре значения распечатываются:

```
./grades
Enter a valid grade: 95
You got an A!
You got a B!
You got a C!
You got a D!
```
Измените программу таким образом, чтобы, если пользователь вводит номер 95, будет распечатываться только правильное значение:

```
./grades
Enter a valid grade: 95
You got an A!
```

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int n;
    printf("Enter a valid grade (between 60 and 100): ");
    n = get_int();

    // TODO: исправьте ошибку!
    if (n >= 90)
        printf("You got an A!\n");
    if (n >= 80)
        printf("You got a B!\n");
    if (n >= 70)
        printf("You got a C!\n");
    if (n >= 60)
        printf("You got a D!\n");
}
```

***

## Оценки #2

### Задача
Вспомните предыдущую систему классификации? Используйте оператор `switch`, чтобы принять оценку в виде буквы, и распечатайте устную оценку
что соответствует ей (например, «У вас A! Отличная работа!»). Совет: `switch` с символами - это почти то же самое, что и переключение с помощью `int`.

### Distribution Code
Нет

***

## Торговый автомат

### Задача
Операторы `switch` подходят для обработки нескольких вариантов ввода - и отвечают за множество возможных случаев. Используя оператор `switch`, напишите программу, которая эмулирует торговый автомат, в котором следующие номера производят следующие шоколадные плиты:
```
1 -- Mars; 2 -- Snickers; 3 -- Milky Way; 4 -- Kit Kat; 5 -- Twix; 6 -- Crunch; 7 -- Hershey's;
```

Для наших целей достаточно распечатать название шоколадного батончика (нет необходимости раздавать фактический шоколад :)).

### Distribution Code
Нет