---
layout: default
title: Набор проблем 4. Экспертиза. Recover (Восстановление).
---
# Recover (Восстановление)

## Коротко

Реализуйте программу, которая будет восстанавливать JPEG'и из образа карты памяти, как указано ниже.
```
$ ./recover card.raw
```
## Объяснение

В ожидании этой проблемы, я провел последние несколько дней фотографируя своих знакомых, изображения которых были сохранены моей цифровой камерой в виде JPEG'ов на карте памяти (ну ладно, скорее всего я провел последние несколько дней просматривая мемы на Facebook'е). К сожалению, я каким-то непонятным образом удалил все фотографии! Но, к счастью, в компьютерном мире, слово "удалил" не подразумевает под собой "удалено", а скорее "забыто". Мой компьютер настаивает на том, что на карте теперь ничего нету, но я уверен что это не правда . Я надеюсь, что вы сможете написать для меня программу, восстанавливающую фотографии!

Хоть JPEG'и в своей структуре намного сложнее BMP, у JPEG'ов есть "подписи" (шаблоны байтов), которые отличают их от других файловых форматов. Все JPEG'и начинаются с трех байтов, слева направо:
```
0xff 0xd8 0xff
```
Четвертый байт может иметь следующие значения: `0xe0`, `0xe1`, `0xe2`, `0xe3`, `0xe4`, `0xe5`, `0xe6`, `0xe7`, `0xe8`, `0xe8`, `0xe9`, `0xea`, `0xeb`, `0xec`, `0xed`, `0xee`, `0xef`. Заметьте, первые четыре бита четвертого байта везде равны `1110`.

Вполне вероятно, если вы найдете этот шаблон из 4 байтов на медианосителе (т.е. на моей карте памяти), что они будут обозначать начало JPEG'а. Конечно, на каком-либо другом диске, вы наткнулись бы на данные шаблоны чисто случайным образом, поэтому восстановление данных не может быть точной наукой.

К счастью, цифровые камеры имеют привычку последовательно хранить фотографии на карте памяти. Каждая фотография сохраняется сразу за предыдущей. Поэтому начало одного JPEG'а обычно говорит о конце другого JPEG'а. Цифровые камеры часто инициализируют карты задавая им файловую систему FAT, в котором "размер одного блока" равен 512 байтам (Б). Суть в том, что эти камеры записывают данные на карты памяти по 512 Б. Таким образом фотография размером в 1 MB (т.е. 1,048,576 Б) занимает 1048576 ÷ 512 = 2048 "блоков" на карте памяти. Но проблема в том, что такое же количество блоков займет файл с размером в один байт меньше предыдущего (т.е. 1,048,575 Б)! Незаполненное дисковое пространство называют "провисающим пространством" ("slack space"). Судебные следователи часто используют эту особенность для нахождения остатков подозрительных веществ.

Суть всех этих деталей в том, что вы, как следователь, скорее всего сможете написать программу, которая будет итерировать копию моей карты памяти, ищя подписи (признаки) JPEG'ов. Каждый раз находя подпись, вы можете открывать новый записываемый файл и начинать заполнять этот файл байтами, которые будут браться из моей карты памяти. При этом закрывать этот файл будете только тогда, когда найдется другая подпись. Более того, для эффективности, вместо того чтобы читать по одному байту за раз, вы можете считывать в буфер по 512 байтов. Благодаря файловой системе FAT, вы можете быть уверены, что подписи JPEG-файлов будут "по блокам выровненными". Т.е. вам нужно будет искать эти подписи только в первых четырех байтах блока.

JPEG'и состоят из смежных блоков. В противном случае, ни один JPEG не смог бы быть больше 512 Б. Может быть и такое, что последний байт JPEG'а может не оказаться в самом конце блока. Вспомните "провисание пространства". Но не беспокойтесь об этом. Так как карта-памяти была совершенно новой, когда я начал "щелкать" фотографии, поэтому, вполне вероятно, что эти пространства "обнулены" (то есть заполнены нулями) производителем. Это хорошо, если эти нули окажутся в восстановленных вами JPEG'ах. Эти файлы по-прежнему должны будут быть доступными для просмотра.

Так, у меня есть только одна карта памяти, а вас не так уж и мало! Я все заранее продумал и создал для вас образ (файл) карты памяти, в котором хранится весь контент, байт за байтом, и этот файл называется `card.raw`. Чтобы вам не пришлось перебирать миллионы лишних нулей, я сделал образ только первых нескольких мегабайт карты памяти. В конечном итоге, у вас должно будет восстановиться 50 JPEG-изображений.

## Развертывание

### Скачивание
```
$ mkdir recover
$ cd recover
$ wget http://cdn.cs50.net/2016/fall/psets/4/pset4/card.raw
$ ls
card.raw
```
## Описание

Создайте программу под названием `recover`, которая будет восстанавливать JPEG'и с образа карты-памяти.

Реализуйте вашу программу в файле `recover.c`, которая должна будет находиться в папке `recover`.

Ваша программа должна принимать ровно один аргумент командной строки - название образа карты-памяти, с которого будет происходить восстановление JPEG'ов. + если вашу программу запустили ненадлежащим образом (с меньшим или большим числом аргументов), она должна оповестить об этом пользователя, используя `fprintf` (с `stderr`). При этом функция `main` должна вернуть `1`.

Если образ невозможно открыть для чтения, ваша программа должна сообщить об этом пользователя, используя `fprintf` (с `stderr`). При этом функция `main` должна вернуть `2`.

Если ваша программа будет пользоваться функцией `malloc`, вы должны будете позаботиться о том, чтобы не возникло никаких утечек памяти.

## Использование

Ваша программа должна проделывать тоже самое, что показано в примере ниже.
```
$ ./recover
Usage (Использование): ./recover image
$ echo $?
1
```
```
$ ./recover card.raw
$ echo $?
0
```

## Проверка
```
check50 cs50/2017/x/recover
```

## Подсказки

Вполне вероятно, что вы захотите начать решать задание с создания файла под названием `recover.c` (в той же папке что и `card.raw`). Вам не понадобится библиотека CS50, но вам лучше объявить функцию `main` таким образом, что она будет поддерживать аргументы командной строки. (Помните как?)

Вы всегда можете открыть `card.raw` программным способом с помощью `fopen`, как показано ниже, главное чтобы `argv[1]` существовал.
```
FILE *file = fopen(argv[1], "r");
```

При выполнении, ваша программа должа восстановить каждое JPEG-изображения, хранящееся на `card.raw`, далее отдельно сохраняя каждый файл в вашей текущей рабочей директории (папке). Ваша программа должна пронумеровать выходные файлы, задавая каждому следующее имя `###.jpg`, где `###` представляют из себя три целых десятичных числа, начиная с `000` и далее (001, 002...). Не нужно восстанавливать оригинальные имена JPEG-изображений. Чтобы проверить на наличие ошибок в фотографиях, которые ваша программа произвела, просто дважды щелкните по ней и посмотрите! Если изображение есть, значит все прошло успешно!

Хотя, вполне вероятно, что первые JPEG'и, которые "выплюнет" ваш (в начале) ошибочный код, окажутся некорректными (Если вы откроете фотографии и ничего не увидите, очень высока вероятность, что они дефектные). Выполните нижеприведенную команду, чтобы удалить все JPEG'и в вашей текущей рабочей директории.
```
rm *.jpg
```
Если вы не хотите, чтобы вас каждый раз просили подтвердить удаление, выполните следующую команду.
```
rm -f *.jpg
```
Будьте осторожнее с переключателем `-f`, так как он "forces" (заставляет) удалять файлы, без вашего подтверждения.