---
layout: default
title: Си. Лекция 3. Алгоритмы.
description: Поиск. Сортировка.Сортировка пузырьком. Сортировка выбором. Сортировка вставками. Сортировка слиянием. Рекурсия.
---
# Лекция 3. Алгоритмы.

## В прошлый раз

Мы познакомились с искусством поиска ошибок (дебаггингом или отладкой) и нашими помощниками в этом деле были: `eprintf` - выводит ошибки на экран; `debug50` - помогает просматривать, что происходит на каждом шаге выполнения программы и показывает изменения переменных.

Мы также разобрали понятие криптографии и то, как можно зашифровать простой текст.

Теперь мы лучше понимаем, что такое `strings` (строки) и массив символов.

Мы разобрали аргументы командной строки, используя `argc` и `argv` через командную строку для их дальнейшего применения в функции `main`.

## Сортировка

Теперь, разобрав основы программирования, мы можем перейти к "решению проблем", используя алгоритмы на более высоком уровне.

Массив - это структура данных, способ хранения информации в памяти.

Представьте, что перед вами 7 дверей, и вам нужно найти определенное число, которое находится за одной из них.

Не имея никакого представления, где может находиться данное число, вы начнете наугад (случайным образом или random) открывать каждую дверь.

Но если бы мы знали, что числа, находящиеся за этими дверями отсортированы, мы могли бы выполнить задачу намного эффективнее.

Точно также как и на нулевой неделе, когда мы с каждым шагом отбрасывали половину проблемы (пример с телефонным справочником), мы можем осуществлять поиск в отсортированном массиве, используя бинарный поиск. Открыв одну дверь и увидев значение, проверять больше оно или меньше необходимого нам числа. А затем продвигаться к той половине, в которой возможно есть нужное нам значение.

Другой вид поискового алгоритма - линейный поиск (последовательный поиск), продвижение по линии слева направо. Можно написать псевдокод (слова похожие на код, но намного более легкие для понимания) следующим образом:
```
Для каждого элемента в массиве
    Если нужный элемент
        вернуть истину
вернуть ложь
```

Заметьте, что `вернуть ложь` находится за пределами цикла `for`. Другими словами, дойдя до конца цикла (при условии что вы разобрали каждый элемент, находящийся в массиве, и не смогли найти именно тот, что нам нужен) - мы можем с полной уверенностью сказать, что его там нету (или `вернуть ложь`).

Обратите внимание на отступы в написании нашего псевдокода, так мы указываем иерархию каждой строки псевдокода. К примеру выражение `вернуть ложь` выполнится только после того, как весь цикл `for` завершит свою работу. В противном случае, если мы неправильно укажем отступы и строка окажется внутри цикла, проверке подвергнется только первый элемент массива.

Бинарный поиск нулевой недели используя псевдокод можно записать следующим образом:
```
посмотреть в центр массива
Если нужный элемент
    вернуть истину
иначе если элемент слева
    искать левую половину массива
иначе если элемент справа
    искать правую половину массива
иначе
    вернуть ложь
```
Теперь мы работаем с не пронумерованными строками, к которым можно было бы возвращаться для повторных действий. Но обратите внимание, `искать левую половину массива` и `искать правую половину массива` - могут по новой запустить выполнение всего алгоритма. Мы используем тот же самый метод поиска, но на этот раз данные на входе будут каждый раз становиться все меньше и меньше, пока в конце концов мы не доберемся до ответа. Функция, вызывающая саму себя, называется **рекурсивной функцией**, и этот принцип рекурсии играет важную роль при поиске и сортировке каких-либо элементов.

Так как же нам получить отсортированный массив? У нас есть доброволец Аллисон - она занимается сортировкой неких синих книг. Каждый раз она забирает левой рукой книгу из неотсортированной стопки и кладет ее в нужное место отсортированной стопки, которое находит при помощи правой руки.

Если бы у нас были игральные карты, мы могли бы взять коробочки и расположить в них карты по числу или по масти (пики, червы, бубны и трефы). Взяв несколько колод карт, мы можем пройтись и отсортировать их.

Можно представить эту проблему, подставив числа вместо элементов:
```Markdown
4 2 6 8 1 3 7 5
```
Первый подход - поиск наименьшего элемента `1` и его передвижение в начальную часть списка с перемещением других ниже (правее) по списку:
<pre><code class="language-Markdown"><u>1</u> <u>4 2 6 8</u> 3 7 5
</code></pre>

Можно продолжить:

<pre><code class="language-Markdown">1 <u>2</u> <u>4 6 8</u> 3 7 5
1 2 <u>3</u> <u>4 6 8</u> 7 5
1 2 3 4 <u>5</u> <u>6 8 7</u>
1 2 3 4 5 6 <u>7</u> <u>8</u>
</code></pre>

В нашем первом шаге нам понадобилось проделать много работы, перемещая все числа, находящиеся слева от `1`, в правую сторону от нее. Мы можем просто поменять местами `1` и первое число:

<pre><code class="language-Markdown">4 2 6 8 1 3 7 5
<u>1</u> 2 6 8 <u>4</u> 3 7 5
1 2 <u>3</u> 8 4 <u>6</u> 7 5
...
</code></pre>

Теперь каждый шаг требует от нас затраты меньшего количества времени.

Но, чтобы каждый раз выбирать элемент с наименьшим значением, нам нужно пройтись по всей неотсортированной части нашего списка для того, чтобы убедиться, что будет выбран именно самый наименьший из них - так мы будем знать, какие элементы мы можем поменять местами.

Этот алгоритм называют **сортировка выбором** (selection sort), где каждый раз мы выбираем наименьший элемент.

Есть еще один способ - **пузырьковая сортировка** (bubble sort):

<pre><code class="language-Markdown">4 2 6 8 1 3 7 5
<u>2</u> <u>4</u> 6 8 1 3 7 5
2 4 6 <u>1</u> <u>8</u> 3 7 5
2 4 6 1 <u>3</u> <u>8</u> 7 5
2 4 6 1 3 <u>7</u> <u>8</u> 5
2 4 6 1 3 7 <u>5</u> <u>8</u>
</code></pre>

Мы проходим по всему списку слева направо и сравниваем каждую пару номеров. Если они расположены не по порядку - мы меняем их местами. Список еще не отсортирован, но число с наибольшим значением теперь находится справа и остальные цифры стали немного ближе к местам, где они должны располагаться.

Мы можем повторять этот процесс снова и снова, пока не получим отсортированный список. Наш алгоритм остановится в тот момент, когда мы пройдем по всему списку и не совершим ни одного перемещения.

И, наконец, последний подход, который мы разберем, называется **сортировка вставками** (insertion sort). Мы рассмотрим по отдельности каждый элемент и заодно создадим наш сортированный список:

<pre><code class="language-Markdown"><u>4</u> 2 6 8 1 3 7 5
<u>2 4</u> 6 8 1 3 7 5
<u>1 2 4 6 8</u> 3 7 5
<u>1 2 3 4 6 8</u> 7 5
<u>1 2 3 4 5 6 8</u> 7
<u>1 2 3 4 5 6 7 8</u>
</code></pre>

Мы смотрим на следующий элемент и помещаем его в нашу отсортированную часть списка, даже если нам и придется каждый раз сдвигать все элементы.

## Время выполнения работы

Наш алгоритм пузырьковой сортировки может выглядеть как-то так:
```
повторять, пока не закончатся смещения
    для i от 0 до n-2
        если i'ый и i+1'ый элементы не идут по порядку
            поменять их местами
```

Помните, что элемент в конце списка представляется следующим образом `n - 1`, т.к. мы начинаем считать от `0`. Поэтому, если разбирать элементы попарно, последняя пара остановится на `n - 2`.

Сортировка выбором:
```
для i от 0 до n-1
    найти наименьший элемент между i'ым и n-1'ым
    заменить наименьший i'ым элементом
```
Теперь мы строим сортированный список путем прохождения через не отсортированную часть списка, нахождения наименьшего элемента и помещения его в конец нашего отсортированного списка.

Сортировка вставками:
```
для i от 1 до n-1
    назвать элементы от 0 до i-1 "сортированной частью"
    удалить i'ый элемент
    поместить его в отсортированную часть, соблюдая порядок
```
Здесь мы строим сортированный список, беря каждый элемент списка и помещая его в нужное место отсортированного списка.

Мы можем использовать число проделанных шагов, представив их в виде единицы измерения эффективности выбранного алгоритма. На самом деле можно выбрать любую единицу измерения, для нас главное, чтобы все использовали одну и ту же терминологию (название).

В пузырьковой сортировке, если у нас есть список с *n* количеством элементов, мы бы сравнивали *(n - 1)* пары в первом же прохождении списка.

И, после первого прохождения, элемент с наибольшим числом оказался бы в самой правой стороне списка. Поэтому, проходясь второй раз по списку, нам нужно будет производить только *(n - 2)* сравнения.

В итоге у нас получится *(n - 1) + (n - 2) + …​ + 1* сравнений. Можно представить это выражение вот так: *n(n - 1)/2*. А если перемножить, то так: *(n<sup>2</sup> - n)/2*.

Смотря на время выполнения программы, нас будет интересовать элемент наибольшей величины, так как только он и будет важен после того, как *n* будет иметь наибольшее значение. Можно избавиться даже от 1/2.

Мы можем разобрать пример (не доказательство!), который поможет нам лучше понять данное действие. Представим, что нам нужно отсортировать 1,000,000 чисел. Тогда пузырьковой сортировке понадобится 1,000,0002/2 - 1,000,000/2 шагов. И если мы развернем первое число, получим 500,000,000,000 - 500,000 = 499,999,500,000. Которое будет ужасно близко к значению изначального числа.

Поэтому, когда у нас есть выражение следующего вида *(n<sup>2</sup> - n)/2*, мы можем сказать, что время выполнения алгоритма *O(n<sup>2</sup>)*.

В зависимости от используемого алгоритма время его выполнения может помечается различными способами:

* *O(n<sup>2</sup>)*

* *O(n log n)*

* *O(n)*

* *O(log n)*

* *O(1)*

*O(1)* означает, что потребуется один шаг, или 10 шагов, или строго заданное определенное число шагов для решения проблемы вне зависимости от ее размера.

Оказывается, если мы распишем все шаги, пузырьковая сортировка, сортировка вставками и сортировка выбором - у всех них скорость выполнения программы будет *O(n<sup>2</sup>)*. Хоть они и мало отличаются друг от друга, они все вовлечены в разнообразные методы прохождения через все *n* элементы до *n* количества раз. С сортировкой вставками мы просматриваем каждый элемент один раз, но дойдя до сортировки нам возможно придется смещать все элементы в списке, который мы уже отсортировали, а это дополнительная работа.

Нахождение элемента в не отсортированном списке используя например линейную сортировку, потребовало бы *O(n)* времени прохождения, т.к. нам нужно сперва просмотреть все элементы *n* до того, как мы найдем нужный нам элемент.

У бинарного поиска логарифмическая скорость выполнения работы *O(log n)*, т.к. каждый раз мы сокращаем проблему в два раза.

И алгоритм постоянного времени прохождения будет записываться как *O(1)*. К примеру сложение чисел или выведение чего-либо на экран. Поскольку можно сказать, что каждый из них требует только один шаг или действие.

Другой символ, который мы могли повстречать, это большая Омега **Ω**, которая является противоположностью большой O. Большая O - худшее время работы алгоритма. Если брать сортировку, то для многих алгоритмов обратно-отсортированный список будет худшим расположением элементов. А большая Омега - это нижайшая граница или лучший сценарий поведения алгоритма.

Сортировка выбором может иметь эффективность работы *Ω(n<sup>2</sup>)*. Даже если все элементы будут отсортированы, мы бы этого не узнали, т.к. нам нужно будет каждый раз проходить через весь список, чтобы быть уверенными, что мы выбрали наименьший элемент. Поэтому получается, что мы смотрим на *n<sup>2</sup>* элементов.

Пузырьковая сортировка, с другой стороны, может иметь время прохождения *Ω(n)*, т.к. при отсутствии смещений наш алгоритм завершает свою работу. После просмотра всех *n* элементов мы понимаем, что сортированный список был действительно отсортирован и завершаем работу.

Но мы понимаем, что невозможно сортировать список с количеством *n* элементов за *Ω(log n)* или *Ω(1)* время, т.к. нам необходимо как минимум посмотреть на все элементы *n*, дабы убедиться, что все они отсортированы.

Алгоритмы поиска, такие как линейный и бинарный, могут работать со скоростью *Ω(1)*, так как в лучшем случае нам может повезти и мы найдем нужный нам элемент с первого раза.

Есть еще одно обозначение эффективности работы алгоритма - тета Θ, если скорость обработки алгоритма в худшем (O) и в лучшем (Ω) случаях совпадает.

Мы посмотрели на [эту визуализацию](https://www.cs.usfca.edu/~galles/visualization/ComparisonSort.html) того, как отличаются друг от друга алгоритмы сортировки. Вот еще одна [визуализация](http://cglab.ca/~morin/misc/sortalg/).

## Сортировка

Вспомните наш псевдокод для поиска Сидорова в телефонной книге:
```
 0   поднять телефонную книгу
 1   открыть посередине
 2   посмотреть на фамилии
 3   если «Сидоров» есть среди фамилий
 4       позвонить «Сидорову»
 5   иначе если «Сидоров» на первой половине
 6       открыть середину левой части книги
 7       вернуться к 2 шагу
 8   иначе если «Сидоров» на второй половине
 9       открыть середину правой части книги
10       вернуться к 2 шагу
11   иначе
12       остановить программу
```
В той версии мы использовали `вернуться к` для создания циклов в нашем алгоритме. Но все можно сделать гораздо проще:
```
 0   поднять телефонную книгу
 1   открыть посередине
 2   посмотреть на фамилии
 3   если «Сидоров» есть среди фамилий
 4       позвонить «Сидорову»
 5   иначе если «Сидоров» на первой половине
 6       искать "Сидорова" в левой части книги
 7
 8   иначе если «Сидоров» на второй половине
 9       искать "Сидорова" в правой части книги
10
11   иначе
12       остановить программу
```
Теперь у нас рекурсивная программа, т.е. она будет вызывать саму себя.

Мы также можем написать псевдокод для сортировки слиянием:
```
ввод n элементов
    если n < 2
        вернуться
    иначе
        сортировать левую половину элементов
        сортировать правую половину элементов
        соединить отсортированные половины
```
Если у нас меньше 2 элементов, то это значит, что наш список отсортирован, поэтому мы остановимся.

Теперь мы используем ту же самую функцию, чтобы она отсортировала для нас половинки, и, как только она их отсортирует, мы произведем слияние (соединение) этих половинок.

Короче, посмотрите на этот пример для лучшего представления:
```
4 8 6 2 1 7 5 3        // не отсортированный список
```
```
| 4 8 6 2 | 1 7 5 3    // отсортировать левую половину
```
```
| 4 8 | 6 2 1 7 5 3    // отсортировать левую половину левой части
```
```
| 4 | 8 6 2 1 7 5 3    // отсортировать левую половину левой части первой левой половины, т.е. только 4-ку. Одно число по-любому является отсортированным (в данной крайней левой половине другого числа просто нет), т.е. эта половина отсортирована.
```
```
4 | 8 | 6 2 1 7 5 3    // отсортировать правую половину левой части левой половины, т.е. только 8-ку. Поэтому же принципу данная половина тоже отсортирована.
```
```
| _ _ | 6 2 1 7 5 3    // теперь мы производим слияние (соединение) левой половины левой части
| 4 8 |                // подключаем дополнительную память для хранения сортированного списка с размером 2
```
```
_ _ | 6 2 | 1 7 5 3    // теперь мы возвращаемся и сортируем правую половину левой части
4 8 | 2 6 |            // отсортировали правую половину левой части
```
Теперь мы можем вспомнить, что наше второе предыдущее выражение, "отсортировать левую половину" завершается с помощью слияния двух отсортированных половин:
```
_ _ | 6 2 | 1 7 5 3
4 8 | 2 6 |
2 4   6 8 |            // соединенная левая половина
```
Чтобы произвести слияние двух отсортированных списков, мы начинаем с начала двух списков и на каждом шагу берем наименьший из представленных элементов.

Теперь повторим с правой половиной:
```
_ _ | _ _ | 1 7 5 3
_ _ | _ _ |
2 4   6 8 |
```
```
_ _ | _ _ | 1 7 5 3
_ _ | _ _ | 1 7 |      // отсортированная левая половина правой части
2 4   6 8 |
```
```
_ _ | _ _ | 1 7 5 3
_ _ | _ _ | 1 7 | 3 5 |  // отсортированная правая половина правой части
2 4   6 8 |
```
```
_ _ | _ _ | 1 7 5 3
_ _ | _ _ | _ _ | _ _ |
2 4   6 8 | 1 3   5 7    // отсортированная правая половина
```
Теперь мы вернулись к нашему первому прохождению алгоритма, где нам нужно произвести слияние двух половин:
```
_ _ | _ _ | 1 7 5 3
_ _ | _ _ | _ _ | _ _ |
2 4   6 8 | 1 3   5 7
1 2   3 4   5 6   7 8    // соединенный список
```
Похоже на то, что было произведено очень много шагов, плюс понадобилось подключить дополнительное пространство для хранения новых списков где-то в памяти.

Но, в процессе сортировки, мы могли бы использовать пространство нашего начального списка, чтобы произвести сортировку, выделяя память только для двух списков.

И со списком в 8 элементов нам бы понадобилось только 3 слоя, который трижды делил бы этот список.

Каждый раз деля проблему надвое мы привели нашу проблему, сократив ее, к чему-то логарифичному (вспомните пример нулевой недели "разделяй и властвуй"). На каждом слое мы смотрели на n элементы, дабы произвести их слияние. Чисто интуитивно можно предположить, что этому алгоритму требуется *O(n log n)* времени.

Можно даже посмотреть на псевдокод, чтобы проанализировать время выполнения программы (running time):
```
ввод n элементов
    если n < 2
        вернуться
    иначе
        сортировать левую половину элементов
        сортировать правую половину элементов
        соединить отсортированные половины
```
Первому условию требуется совершить *O(1)* шаг для возврата или выхода из функции. Это постоянное число, поэтому *T(n) = O(1)*. Время выполнения программы равно *O(1)*.

Но второму условию требуется *T(n) = T(n/2) + T(n/2) + O(n)*, т.к. сортировка каждой половины элементов требует половины времени, затрачиваемого на сортировку всех элементов, плюс время, требующееся на слияние двух половин.

Давайте посмотрим, как это может быть использовано.

`sigma0.c` (сигма):
```c
#include <cs50.h>
#include <stdio.h>

int sigma(int m);

int main(void)
{
    int n;
    do
    {
        printf("Введите положительный integer: ");
        n = get_int();
    }
    while (n < 1);

    int answer = sigma(n);

    printf("%i\n", answer);
}

int sigma(int m)
{
    int sum = 0;

    for (int i = 1; i <= m; i++)
    {
        sum += i;
    }

    return sum;
}
```
Эта программа (а точнее функция `int sigma(int m)` ) на входе принимает integer `m` (надеюсь, вы уже понимаете концепции входа и выхода) и к нему добавляются все числа от `1` до `m` включительно, с помощью цикла.

Версия `sigma1.c` с использованием рекурсии будет выглядеть вот так:
```c
#include <cs50.h>
#include <stdio.h>

int sigma(int m);

int main(void)
{
    int n;

    do
    {
        printf("Введите положительный integer: ");
        n = get_int();
    }
    while (n < 1);

    int answer = sigma(n);

    printf("%i\n", answer);
}

int sigma(int m)
{

    if (m <= 0)
    {
        return 0;
    }
    else
    {
        return (m + sigma(m - 1));
    }
}
```
Функция `sigma` вызывает саму себя, добавляя при этом текущую `m` к тому, что вернет сумма, а именно от `0` (потому что функция возвратит `0`, если `m` будет `0` или меньше) до `m - 1`, и это дает нам сумму от `0` до `m`.

Но, хотя рекурсия и может приятно выглядеть, ее применение не всегда может быть правильным выбором, т.к. если у `m` будет слишком большое значение, придется снова и снова вызывать функцию, заполняя все больше памяти.

Скоро мы разберем более привлекательные структуры данных и то, как мы можем применить к ним все разобранные нами на этой неделе концепции.