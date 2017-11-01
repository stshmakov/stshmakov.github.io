---
layout: default
title: Си. Строки
---

# Си. Строки.

## Различие документов

### Задача
Один (наивный) способ проверить академическую честность - просто проверить, насколько похожи два документа: слово в слово, буква за буквой. В приведенном ниже примере напишите функцию типа `void`, которая берет две строки, сравнивает их и печатает: a количество букв, на которых они отличаются, и **b** расположение букв, в которых строки отличаются. Предположим, что строки имеют одинаковую длину.

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

void document_distance(string s1, string s2);

int main(void)
{
    string doc1 = "this is how James implimented the coad";
    string doc2 = "This is how Tania implemented The Code";

    document_distance(doc1, doc2);
}

void document_distance(string s1, string s2)
{
	// TODO
}
```

***

## Erised

### Задача
Выведите  надпись зеркально: «Erised straeh ruoy tub ecaf ruoy ton wohs i», напечатав ее назад! Напишите функцию типа `void`, которая принимает строку и выводит ее обратно!

### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

void reverse(string s);

int main(void)
{
    string erised = "erised straeh ruoy tub ecaf ruoy ton wohs i";
    printf("The hidden message inscribed on the mirror of erised is: \n");
    reverse(erised);
}

void reverse(string s)
{
	// TODO
}
```

***

## Помоги мне!

### Задача
В приведенном ниже коде содержится секретное сообщение. Выведите его, перебирая строку `message` и изменив используемую кодировку, которая была:
```
'e' -> '7'
''  -> 'Z'
'y' -> '3'
'o' -> '8'
'i' -> '4'
```
Подсказка: рассмотрите использование оператора `switch`!


### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    string message = "H7lpZm7,ZOb4-WanZK7nbb4.ZYbu'r7Zm3Zbnl3Zhbp7."
    // TODO
}
```

***

## Длина строки

### Задача
Представьте, что у вас нет доступа к функции `strlen`. Напишите ее заново для следующей программы, в которой `strlen` используется для поиска длин двух строк (включая пробелы). Pro-tip: в `C` одиночные кавычки, подобные этим `''`, ограничивают один символ, а для строк используются двойные кавычки `""`.


### Distribution Code
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int string_length(string s);

int main(void)
{
    string s1 = "The quick brown fox";
    string s2 = "jumps over the lazy dog";

    printf("The length of \"%s\" is %d\n", s1, string_length(s1));
    printf("The length of \"%s\" is %d\n", s2, string_length(s2));

}

int string_length(string s)
{
    // TODO
}
```