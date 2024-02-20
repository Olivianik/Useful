Значения по умолчанию для аргументов функции — это возможность гибкого использования перегрузки функций в сочетании с сокращением объёма кода. Функция со значениямо по умолчаниями может быть вызвана с разным количеством параметров.

При этом значения по умолчанию могут быть только у некоторого количества последних аргументов.

Пример
void f(int a = 1, int b = 2, int c = 3);
Данную функцию можно вызвать как с одним, так и с двумя, так и с тремя параметрами.

f(10); // будет вызвано f(10, 2, 3)
f(10, 20); // будет вызвано f(10, 20, 3)
f(10, 20, 30); // значения по умолчанию совсем не использованы
Её можно вызвать вообще без параметров:

f(); //для всех параметров использованы значения по умолчанию - f(1, 2, 3)
Значением по умолчанию не может являться значение другого аргумента:

void f(int a, int b = a); // Не допустимо!
Функции с аргументами по умолчанию и перегрузка
Поскольку такая функция может вызвана с разным количеством параметров, она участвует в перегрузке одновременно конкурируя с одноимёнными функциями с разным количеством параметров.