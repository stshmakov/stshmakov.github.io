---
layout: default
title: Типы данных в Си.
---

# Типы данных в Си.

<table class="table table-striped">
    <thead>
    <tr>
        <th scope="col">Тип данных</th>
        <th scope="col">Использование</th>
        <th scope="col">Размер</th>
        <th scope="col">Функция из cs50.h</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td><code>int</code></td>
        <td>Целочисленные переменные, счетчики.</td>
        <td>4 байта (32 бита)</td>
        <td><code>get_int("Prompt: ");</code></td>
    </tr>
    <tr>
        <td><code>char</code></td>
        <td>Буквы и другие одиночные символы.</td>
        <td>1 байт (8 бит)</td>
        <td><code>get_char("Prompt: ");</code></td>
    </tr>
    <tr>
        <td><code>float</code></td>
        <td>Значения с плавающей запятой.</td>
        <td>4 байта (32 бита)</td>
        <td><code>get_float("Prompt: ");</code></td>
    </tr>
    <tr>
        <td><code>double</code></td>
        <td>Значения с плавающей точкой, требующие большей точности.</td>
        <td>8 байт (64 бита)</td>
        <td><code>get_double("Prompt: ");</code></td>
    </tr>
    <tr>
        <td><code>long long</code></td>
        <td>Целые числа, которые могут быть очень большими.</td>
        <td>8 байт (64 бита)</td>
        <td><code>get_long_long("Prompt: ");</code></td>
    </tr>
    <tr>
        <td><code>string</code></td>
        <td>Слова, фразы, абзацы.</td>
        <td>8 байт (64 бита)</td>
        <td><code>get_string("Prompt: ");</code></td>
    </tr>
    <tr>
        <td><code>bool</code></td>
        <td>Правда или ложь (true или false).</td>
        <td>1 байт (8 бит)</td>
        <td></td>
    </tr>
    </tbody>
</table>