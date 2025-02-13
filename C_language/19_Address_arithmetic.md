### Адресная арифметика в С ###

Под адресной арифметикой понимаются арифметические действия над указателями.

#### Сравнение ####
Сравнение двух указателей любой из операций отношения имеет смысл только в том случае, если оба указателя адресуют общий 
для них объект, например, строку или массив.

#### Увеличение/уменьшение ####
Если к указателю применяется операция увеличения **++** или уменьшения **--**, то значение указателя увеличивается или уменьшается 
на размер объекта, который он адресует:
```c
long b;       // b – переменная типа int длиной 4 байта 
long *ptr;    // ptr – указатель на объект типа long длиной 4 байта
ptr = &b;      // в ptr адрес переменной b 
ptr++;        // в ptr адрес увеличился на 4 
ptr--;        // в ptr адрес уменьшился на 4
```
#### Сложение ####
Одним из операндов операции сложения может быть указатель, а другим операндом обязательно должно быть выражение целого типа. 
Операция сложения вырабатывает адрес, который определяется следующим образом:  
`(адрес в указателе) + (значение int_выражения)*sizeof(<тип>)`, где `<тип>` это тип данных, на которые ссылается указатель.
```c
double d;
int n;
double *uk;
uk = &d;    // в uk адрес переменной d 
n = 3;
uk = uk+n;   // в результате выполнения операции сложения, 
             // а затем операции присваивания, в uk новый 
             // адрес на 24 больше, чем предыдущий 
uk=n+uk;     // в uk адрес увеличился еще на 24
```
#### Вычитание ####
Левым операндом операции вычитания должен быть указатель, а правым должно быть выражение целого типа. Операция вычитания 
вырабатывает адрес, который определяется так: ___(адрес в указателе) - (значение int_выражения)*sizeof(<тип>)___.

К указателям можно применять только описанные операции и операции, которые выражаются через них, например, разрешается к 
указателю применить операцию `uk += n;`, так как ее можно выразить через `uk = uk+n;`

#### Индексация ####
Указатель может индексироваться применением к нему операции индексации, обозначаемой в Си квадратными скобками `[ ]`. 
Индексация указателя имеет вид `<указатель>[<индекс>]`, где `<индекс>` записывается целочисленным выражением.

Возвращаемым значением операции индексации является данное, находящееся по адресу, смещенному в бóльшую или меньшую сторону 
относительно адреса, содержащегося в указателе в момент применения операции. Этот адрес определяется так: `(адрес в
указателе) + (значение <индекс>) * sizeof(<тип>)`, где `<тип>` — это тип указателя.

Из этого адреса извлекается или в этот адрес посылается, в зависимости от контекста применения операции, значение, тип которого 
интерпретируется в соответствии с типом указателя. Рассмотрим следующий пример:
```c
int *uk1; // предполагается, что int занимает 2 байта
int b,k;
uk1 = &b; // в uk1 адрес переменной b 
k = 3;
b = uk1[k];  // переменной b присваивается значение int, 
             // взятое из адреса на 6 большего, чем 
             // адрес переменной b;  в uk1 адрес не изменился
uk1[k] = -14;  // начиная с адреса на 6 большего, чем адрес переменной b, 
               // записывается целое число -14
```
Операция индексации не изменяет значение самого указателя, к которому она применялась.
