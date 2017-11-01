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
