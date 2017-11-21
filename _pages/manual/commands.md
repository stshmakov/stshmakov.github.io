---
layout: default
title: Команды CS50 IDE.
---

# Команды CS50 IDE

<table class="table table-striped">
  <thead>
    <tr>
      <th scope="col">Команда</th>
      <th scope="col">Описание</th>
      <th scope="col">Пример</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>**make [program_name]**</td>
      <td>Компилирует программы C.</td>
      <td>**make hello**</td>
    </tr>
    <tr>
          <td>**help50 [program_name]**</td>
          <td>Предоставляет помощь по сообщениям об ошибках компилятора.</td>
          <td>**help50 make hello**</td>
    </tr>
    <tr>
          <td>**./[program_name]**</td>
          <td>Запускает программы C.</td>
          <td>**./hello**</td>
        </tr>
    <tr>
        <td>**debug50 ./[program_name]**</td>
        <td>Запускает отладчик GDB (дебаггер), останавливаясь на отмеченных контрольных точках (break points).</td>
        <td>**debug50 ./hello**</td>
    </tr>
    <tr>
            <td>**check50 [problem_name] [file_name]**</td>
            <td>Запускает код через тестовые примеры, чтобы проверить правильность.</td>
            <td>**check50 cs50/2017/х/hello hello.c**</td>
        </tr>
    <tr>
                <td>**style50 [program_name]**</td>
                <td>Проверяет, соответствует ли код руководству по стилю CS50.</td>
                <td>**style50 hello.c**</td>
            </tr>
             <tr>
               <td>**update50**</td>
               <td>Обновляет IDE до текущей версии.</td>
               <td>**update50**</td>
             </tr>
            <tr>
                        <td>**submit50 [problem_name] [file_name]**</td>
                        <td>Отправляет код на проверку через cs50.me.</td>
                        <td>**submit50 cs50/2017/х/hello hello.c**</td>
                    </tr>
  </tbody>
</table>