### Указатели в С ###

Память компьютера можно представлять себе, как массив байт. Получается, что каждый байт памяти имеет свой индекс.

Можно представить, что мы обращаемся по адресу **p** так: **RAM[p]**

**Адрес ячейки** — это индекс в массиве оперативной памяти.

Адрес переменной часто путают с указателем.

**Указатель — это переменная для хранения адреса.**

#### Описание указателя ####
```c
int *p;
```

При этом int * — это тип данных "указатель на int"

#### Основные операции с адресами ####
<table>
    <tr>
        <th>&a</th>
        <th align="left">операция взятия адреса ячейки памяти, в которой хранится переменная a (если она занимает несколько 
        последовательных ячеек, берется адрес первой)</th>
    </tr>
    <tr>
        <td>*p</td>
        <td align="left">операция разыменования (обращения по адресу, хранящемуся в p)</td>
    </tr>
</table>

#### Примеры работы с памятью по адресу ####
```c
int x =1, y = 2, z[10];
int *ip; //ip – указатель на int 
ip = &x; //ip указывает на х (содержит адрес x) 
y = *ip; //y = 1; 
*ip = 0; //x = 0; 
ip = &z[0]; //ip указывает на z[0]
```