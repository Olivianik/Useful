### Типы целых чисел языка С ###

Для объявления переменных целого типа используются ключевые слова, определяющие диапазон значений и размер области памяти, 
выделяемой под переменные:

<table>
    <tr>
        <th>Тип</th>
        <th>Размер памяти в байтах</th>
        <th>Диапазон значений</th>
    </tr>
    <tr>
        <td>char</td>
        <td>1</td>
        <td>от -128 до 127</td>
    </tr>
    <tr>
        <td>int</td>
        <td>???</td>
        <td>???</td>
    </tr>
    <tr>
        <td>short</td>
        <td>2</td>
        <td>от -32768 до 32767</td>
    </tr>
    <tr>
        <td>long</td>
        <td>4</td>
        <td>от -2 147 483 648 до 2 147 483 647</td>
    </tr>
    <tr>
        <td>unsigned сhar</td>
        <td>1</td>
        <td>oт 0 до 255</td>
    </tr>
    <tr>
        <td>unsigned int</td>
        <td>???</td>
        <td>???</td>
    </tr>
    <tr>
        <td>unsigned short</td>
        <td>2</td>
        <td>от 0 до 65535</td>
    </tr>
    <tr>
        <td>unsigned long</td>
        <td>4</td>
        <td>от 0 до 4 294 967 295</td>
    </tr>
</table>

Ключевые слова **signed** и **unsigned** указывают, как интерпретируется нулевой бит объявляемой переменной: если указано 
unsigned, то нулевой бит интерпретируется как часть числа, в противном случае нулевой бит интерпретируется как знаковый. 
По умолчанию переменная считается знаковой и имеющей тип int.

#### Примеры ####
```c
unsigned int n;
unsigned int b;
int c;        /* подразумевается  signed   int c */
unsigned d;   /* подразумевается  unsigned int d */
signed f;     /* подразумевается  signed   int f */
```
Тип char чаще всего используется для представления символа, однако значением объекта типа char является код (размером 1 байт), 
соответствующий представляемому символу. Для представления символов расширенной части кодовой таблицы — кодовой страницы 
Windows-1251 или KOI8-R, модификатор типа идентификатора данных должен иметь вид unsigned char, так как коды русских букв 
превышают величину 127.

В языке Си не определено представление в памяти и диапазон значений для типа int. Этот размер памяти определяется длиной машинного 
слова, которое имеет различный размер на разных ЭВМ. Для 16-битовых ЭВМ размер слова равен 2-м байтам, на 32-битных соответственно 
4-м байтам, т.е. тип int эквивалентен типам short int, или long int в зависимости от архитектуры. Таким образом, одна и та же 
программа может правильно работать на одном компьютере и неправильно на другом!

Для определения размера типа в байтах можно использовать операцию sizeof:

#### Примеры ####
```c
a = sizeof(int);
b = sizeof(long int);
c = sizeof(unsigned long);
d = sizeof(short);
```
Отметим также, что константы, в том числе восьмеричные и шестнадцатеричные, могут иметь модификатор unsigned. Это достигается 
указанием префикса u или U после константы, константа без этого префикса считается знаковой.

#### Примеры ####
```c
0xA8C   /* signed int */;
01786l  /* signed long int */;
0xF7u   /* unsigned int */;
```
