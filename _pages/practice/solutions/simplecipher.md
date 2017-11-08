---
layout: default
title: Си. ASCII. Простой шифр. Решение.
---
# Си. ASCII. Простой шифр. Решение.

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
    	message[i] -= 5;
    	printf("%c", message[i]);
    }
    printf("\n");
}
```