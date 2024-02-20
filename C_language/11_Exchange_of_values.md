### Обмен переменных значениями на C ###

Классический алгоритм обмена переменных значениями осуществляется через третью переменную:
```c
temp = x; //Копирование x во временное хранилище (temp ← x)
x = y; //Установка x значением y (x ← y)
y = temp; //Копирование значения из временного хранилища в y (y ← temp)
```
Однако можно предложить еще несколько вариантов алгоритма обмена без использования третьей переменной. 
Рассмотрим вариант со сложением:
```c
a = 3;
b = 5;
a = a + b; // здесь будет 8
b = a - b;// здесь уже будет 3
a = a - b; // а теперь равно 5
```
Этот алгоритм плох из-за потенциальной возможности переполнения числа.