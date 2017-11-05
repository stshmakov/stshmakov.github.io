---
layout: default
title: Си. ASCII. toupper. Решение.
---
# Си. ASCII. toupper. Решение.

```c
#include <cs50.h>
#include <stdio.h>

char toupper(char c);

int main(void)
{
    char c;
    do
    {
        printf("Please enter a lowercase alphabetical character: ");
        c = get_char();
    }
    while (c < 'a' || c > 'z');

    c = toupper(c);
    printf("The capitalized letter is: %c\n", c);
}

char toupper(char c)
{
    return c - 32; // A - 65, a - 97 Большую и маленькую буквы разделяют 32 символа.
}
```
