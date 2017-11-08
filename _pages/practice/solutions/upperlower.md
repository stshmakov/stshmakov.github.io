---
layout: default
title: Си. ASCII. Строчная или заглавная. Решение.
---
# Си. ASCII. Строчная или заглавная. Решение.

```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    char c = get_char("Give me a char: ");

    if (c >= 'A' && c <= 'Z')
    {
        printf("Upper\n");
    }
    else if (c >= 'a' && c <= 'z')
    {
        printf("Lower\n");
    }
    else
    {
        printf("Error\n");
    }
}
```