---
layout: default
title: Си. Функции.
---

# Си. Функции.

## Различие документов

### Задача
Нижеприведенный код запрашивает у пользователя число и передает его функции, которая должна увеличить его значение на 5. Однако, похоже, что несмотря на эту функцию, `add_5`, казалось бы, добавив 5 к значению `x` - значение `x` не изменяется! Запустите код один или два раза, чтобы узнать, что происходит, и исправьте код в `add_5` и `main`, чтобы правильно обновить значение `x`.


### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>

// TODO: исправить прототип функции
void add_5(int x);

int main(void)
{
    // input from user
    int x = get_int("Enter some integer value: ");
    printf("the value of x before adding 5 is %d\n", x);
    // TODO: исправить это, чтобы обновить значение x
    add_5(x);
    printf("the value of x after adding 5 is %d\n", x);
}

// TODO: исправить реализацию функции
void add_5(int x)
{
    x = x + 5;
}
```

***

## Накопление процентов

### Задача
Реализовать функцию с прототипом

`double accumulate_interest(double balance, double rate);`

который принимает два числа типа  `double` в качестве входных данных - банковский баланс и годовую процентную ставку - и выводит обновленный баланс после 1 года начисления процентов.

Пример вывода:
```
./accumulate_interest
Starting balance: 100
Annual interest rate: 0.05
Updated balance: 105.00
```

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>

// TODO: прототип функции

int main(void)
{
    double start = get_double("Starting balance: ");
    double interest = get_double("Annual interest rate: ");
    double updated = // TODO: вызов функции
    printf("Updated balance: %.2f\n", updated);
}

// TODO: реализация функции
```

***

## Шифрование

### Задача
Программа шифрования требует, чтобы вы сначала ввели два целых числа, которые больше 100, одно из которых кратно 7, а другое кратно 19. Добавьте две функции в код ниже, которые подтверждают, что входные данные соответствуют требуемым критериям, и верните `true` или `false`.

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>

// TODO: создать прототипы функций

int main(void)
{
    int fac_1 = get_int("enter the first encryption factor: ");
    int fac_2 = get_int("enter the second encryption factor: ");

    if (test_7(fac_1) && test_19(fac_2))
        printf("Success! Message was encrypted\n");
    else
        printf("Factors failed. Please try again later\n");
}

// TODO: реализация функций
```

***

## Квиддич

### Задача
Вы хотите рассчитать окончательный результат для команды, которая только что участвовала в захватывающем матче квиддича. Основываясь на приведенном ниже коде, реализуйте функцию, которая получает две переменные в качестве входных данных: `int` указывает количество раз, когда команда получала Quaffle через обручи другой команды, и `bool`, указывающую, поймали ли они snitch - и возвращает окончательный результат команды (какой будет тип возврата?).

Напомним, что каждая «цель» в квиддиче стоит 10 очков, а ловушка снитта стоит 150 очков.


### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>

// TODO: создать прототипы функций

int main(void)
{
    int goal_num = get_int("Number of times your chasers got the quaffle through a hoop: ");

    bool snitch_caught = get_int("Did your team's seeker catch the snitch? Enter 1 if true, 0 otherwise: ");

    int score = final_score(goal_num, snitch_caught);
    printf("Your team's final score is: %i\n", score);
}

// TODO: реализация функции
```

***

## Проверщик

### Задача
Пользователь решает некоторые простые задачи с добавлением и хочет убедиться, что он получил правильный результат. Пользователь вводит три целых числа, два из которых он складывает, а третье результат который он ожидает. Напишите функцию `verify` типа `bool`, которая принимает эти три `int` и возвращает либо `true`, либо `false`, в зависимости о том, правильно ли он решил задачу.

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>

// TODO: создать прототип

int main(void)
{
    int x = get_int("Enter the first int you are adding: ");
    int y = get_int("Enter the second int you are adding: ");
    int z = get_int("Enter the result: ");

    // TODO: проверьте результат, используя функцию, которую вы написали, и напечатайте 'correct!' или 'incorrect!'

}

// TODO: реализовать функцию проверки
```
