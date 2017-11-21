---
layout: default
title: Команды CS50 IDE.
---

# Команды CS50 IDE

<table class="table table-striped">
    <thead>
    <tr>
        <th scope="col">Команда</th>
        <th scope="col" width="30%">Описание</th>
        <th scope="col">Пример</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td><code>make [program_name]</code></td>
        <td>Компилирует программы C.</td>
        <td><code>make hello</code></td>
    </tr>
    <tr>
        <td><code>help50 [program_name]</code></td>
        <td>Предоставляет помощь по сообщениям об ошибках компилятора.</td>
        <td><code>help50 make hello</code></td>
    </tr>
    <tr>
        <td><code>./[program_name]</code></td>
        <td>Запускает программы C.</td>
        <td><code>./hello</code></td>
    </tr>
    <tr>
        <td><code>debug50 ./[program_name]</code></td>
        <td>Запускает отладчик GDB (дебаггер), останавливаясь на отмеченных контрольных точках (break points).</td>
        <td><code>debug50 ./hello</code></td>
    </tr>
    <tr>
        <td><code>check50 [problem_name] [file_name]</code></td>
        <td>Запускает код через тестовые примеры, чтобы проверить правильность.</td>
        <td><code>check50 cs50/2017/х/hello hello.c</code></td>
    </tr>
    <tr>
        <td><code>style50 [program_name]</code></td>
        <td>Проверяет, соответствует ли код руководству по стилю CS50.</td>
        <td><code>style50 hello.c</code></td>
    </tr>
    <tr>
        <td><code>update50</code></td>
        <td>Обновляет IDE до текущей версии.</td>
        <td><code>update50</code></td>
    </tr>
    <tr>
        <td><code>submit50 [problem_name] [file_name]</code></td>
        <td>Отправляет код на проверку через cs50.me.</td>
        <td><code>submit50 cs50/2017/х/hello hello.c</code></td>
    </tr>
    </tbody>
</table>