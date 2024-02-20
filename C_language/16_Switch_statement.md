### Оператор ветвления switch в С ###

Cинтаксис команды switch:
```c
switch (i)
{
case 0:
    …  // последовательность операторов
    break;
case 1: 
    …  // последовательность операторов
    break;
case 2: 
    …  // последовательность операторов
    break;
default:
    …
}
```
Здесь i — выражение-селектор, которое обязано иметь приводимый к целому тип; каждая ветвь исполнения начинаются с ключевого 
слова **case**, за ним следует значение выражения, при котором должна выполняться данная ветвь.

В С переключатель трактуется именно как команда перехода по вычисляемой метке, а роль меток играют заголовки ветвей **(case 
значение :)**. Чтобы после завершения кода ветви произошёл выход из оператора переключателя, используется специальная команда 
**break**. Если такой команды в ветви нет, после исполнения кода выбранной ветви начнётся исполнение кода следующей за ней. Эта 
особенность может использоваться для оптимизации, хотя может служить причиной трудно обнаруживаемых ошибок (если программист 
случайно пропустит break, компилятор не выдаст ошибки, но программа будет выполняться неверно). Ветвь default исполняется 
тогда, когда среди прочих ветвей не нашлось ни одной подходящей.