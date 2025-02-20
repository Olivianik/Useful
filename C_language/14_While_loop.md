### Инструкция цикла while в С ###

Инструкция цикла **while** называется циклом с предусловием и имеет следующий формат:
```c
while (условие)
{
    блок инструкций
}
```
В качестве выражения допускается использовать любое выражение языка С, а в качестве тела любая инструкция, в том числе пустая 
или составная (последовательность простых инструкций в фигурных скобках). <br>
Схема выполнения инструкции while следующая:

1. Вычисляется выражение.

2. Если выражение ложно, то выполнение инструкции while заканчивается и выполняется следующая за ней инструкция. Если истинно, то 
выполняется блок инструкции while.

3. Процесс повторяется с пункта 1.

Инструкция цикла **do while** называется инструкцией цикла с постусловием и используется в тех случаях, когда необходимо выполнить 
тело цикла хотя бы один раз. Формат инструкции do while имеет следующий вид:
```c
do
{
    блок инструкций
}
while (условие);
```
Схема выполнения цикла do while :

1. Выполняется тело цикла (которое может быть составной инструкцией).

2. Вычисляется выражение.

3. Если выражение ложно, то выполнение инструкции do while заканчивается и выполняется следующая инструкция. Если истинно, то 
выполнение цикла продолжается с пункта 1.

#### Управление выполнением цикла ####
В любой момент можно прервать выполнение цикла инструкцией **break**.

Если прервать нужно не цикл, а лишь текущую итерацию, продолжив выполнение со следующей итерации, нужно использовать инструкцию 
**continue**.

Обе инструкции могут использоваться только внутри инструкций цикла.

#### Пример вложенных циклов ####
```c
int i, j, k;
…
i=0;
j=0;
k=0;
do
 {
    i++; 
    j--; 
    while (a[k] < i) 
        k++;
} while (i < 30 && j < -30);
```
