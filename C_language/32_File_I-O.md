### Файловый ввод-вывод в С ###

**Файл** – это именованная область данных на каком-либо носителе информации.

Типы файлов (с точки зрения интерпретации информации в программе на Си):

* текстовые;
* бинарные.

Основные операции производимые над файлами:

* Открытие файлов.
* Чтение и запись данных.
* Закрытие файлов.

Дополнительные операции:

* Навигация по файлу.
* Обработка ошибок работы с файлами.
* Удаление и переименование файлов.
* Описание переменной

Для работы с файлами в программах на Си используется заголовочный файл `stdio.h`, в котором объявлен специальный 
тип данных — структура `FILE`, предназначенная для хранения атрибутов (параметров) файлов (указатель текущей позиции 
файла, признак конца файла, флаги индикации ошибок, сведения о буферизации и др.). Переменные типа `FILE` нельзя 
создавать вручную.

Для работы с файлом в программе нужно создать "указатель на файл".
```c
FILE *имя = NULL;
```
Нужно осознавать, что каждое обращение к файлу выполняется через *системный вызов*. При этом этот указатель не 
нужно разыменовывать при обращении к файлу, библиотечной функции передается сам этот указатель.

#### Открытие файла ####

FILE *fopen(const char *filename, const char *mode);
где filename — название файла, mode — режим открытия.

Функция возвращает указатель на файл, если тот был успешно открыт. В противном случае — NULL.

Название файла содержит только имя файла, если файл находится в текущем каталоге. Иначе необходимо указать 
абсолютный или относительный путь к файлу.

Примеры:

* "data.txt”
* "..\\files\\data.txt"
* "d:\\temp\\data.txt"

#### Режимы открытия файлов ####
<table>
    <tr>
        <th>r</th>
        <th>только чтение</th>
    </tr>
    <tr>
        <td>w</td>
        <td>Только запись. Если файл существовал, то он переписывается.</td>
    </tr>
    <tr>
        <td>a</td>
        <td>Добавление: открытие файла для записи в конец, или создание файла.</td>
    </tr>
    <tr>
        <td>r+</td>
        <td>Открывает файл для обновления (чтение и запись).</td>
    </tr>
    <tr>
        <td>w+</td>
        <td>Открывает файл для обновления (чтение и запись), переписывая файл, если он существует.</td>
    </tr>
    <tr>
        <td>a+</td>
        <td>Открывает файл для записи в конец файла или для чтения.</td>
    </tr>
</table>
Во втором параметре дополнительно может указываться символ t и b для указания текстовый файл или двоичный 
(необязательно для многих операционных систем):

 rt, wt, at, rt+, wt+, at+

 rb, wb, ab, rb+, wb+, ab+

#### Закрытие файла ####

```c
int fclose(FILE *stream);
```
где stream — указатель на открытый файл.

Функция возвращает:

* 0 – файл успешно закрыт.
* 1 – произошла ошибка закрытия файла.

Можно закрыть и открыть новый файл в одну команду:
```c
FILE * freopen(const char *filename, const char *mode, FILE *stream);
```
Функция возвращает указатель на файл, если все нормально, и NULL, если возникла ошибка открытия нового файла 
или закрытия старого.

#### Чтение из текстового файла ####

#### Форматированное чтение ####
```c
int fscanf(FILE *stream, const char * format, [arg] …);
```
Функция возвращает:

* больше 0 — число успешно прочитанных переменных,
* 0 — ни одна из переменных не была успешно прочитана,
* EOF — ошибка или достигнут конец файла.

#### Чтение строки ####
```c
char * fgets(char * buffer, int maxlen, FILE *stream);
```
В `maxlen` следует указать размер буфера, чтобы при записи в память функция чтения не вышла за его границы.

Функция считывает строку до символа перевода каретки `'\n'` или `maxlen` — что наступит раньше.

Функция возвращает указатель на buffer, если все нормально, и NULL, если возникла ошибка или достигнут конец 
файла.

#### Чтение символа ####

```c
int fgetc(FILE *stream);
```
Функция возвращает код символа, если все нормально, и EOF, если произошла ошибка или достигнут конец файла.

#### Помещение символа обратно в поток ####

```c
int ungetc(int c, FILE *stream);
```
Функция возвращает код символа, если все успешно, и EOF, если произошла ошибка.

#### Запись в текстовый файл ####

#### Форматированный вывод #####

```c
int fprintf(FILE *stream, const char *format, [arg] …);
```
Функция возвращает число записанных символов, если все нормально, и отрицательное значение, если произошла 
ошибка.

#### Запись строки ####

```c
int fputs(const char *string, FILE *stream);
```
Функция возвращает число записанных символов, если все нормально, и EOF, если произошла ошибка.

#### Запись символа ####

```c
int fputc(int c, FILE *stream);
```
Функция возвращает код записанного символа, если все нормально, и EOF, если произошла ошибка.

#### Чтение и вывод в двоичные файлы ####

#### Чтение из двоичных файлов ####

```c
size_t fread(void *buffer, size_t size, size_t num,FILE *stream);
```
Функция возвращает количество прочитанных блоков.

Если оно меньше num, то произошла ошибка или достигнут конец файла.

#### Запись в двоичный файл ####

```c
size_t fwrite(const void *buffer, size_t size, size_t num, FILE *stream);
```
Функция возвращает количество записанных блоков.

Если оно меньше num, то произошла ошибка.

#### Проверка на достижение конца файла ####

```c
int feof(FILE *stream);
```
где stream — указатель на открытый файл

Функция возвращает 0, если файловый поток не кончился, и не ноль, если достигнут конец файла.

#### Навигация по файлу ####

#### Чтение текущего смещения в файле ####

```c
long int ftell(FILE *stream);
```

#### Изменение текущего смещения в файле ####

```c
int fseek(FILE *stream, long int offset, int origin);
```
Значение origin может принимать три значения:

* SEEK_SET (0) – от начала файла.
* SEEK_CUR (1) – от текущей позиции.
* SEEK_END (2) – от конца файла.

Функция возвращает 0, если все нормально, и не ноль, если произошла ошибка.

#### Перемещение к началу файла ####

```c
void rewind(FILE *stream);
```

#### Чтение текущей позиции в файле ####

```c
int fgetpos(FILE *stream, fpos_t *pos);
```

#### Установка текущей позиции в файле ####

```c
int fsetpos(FILE *stream, const fpos_t *pos);
```

Функции возвращают 0, если все нормально, и не ноль, если произошла ошибка.

Структура fpos_t
```c
typedef struct fpos_t {
   long off;
   mbstate_t wstate;
  } fpos_t;
```

#### Получение признака ошибки ####

```c
int ferror(FILE *stream);
```
Функция возвращает ненулевое значение, если возникла ошибка.

#### Функция сброса ошибки ####

```c
void clearerr(FILE *stream);
```

#### Функция вывода сообщения об ошибке ####

```c
void perror(const char *string);
```

#### Буферизация ####

Функция очистки буфера:
```c
int fflush(FILE *stream);
```
Функция возвращает 0, если все нормально, и EOF, если произошла ошибка.

Функция управления буфером:
```c
void setbuf(FILE *stream, char *buffer);
```
Создает буфер размером BUFSIZ. Используется **до** ввода или вывода в поток.

#### Временные файлы ####

Функция создания временного файла:
```c
FILE * tmpfile(void);
```
Создает временный файл в режиме wb+. После закрытия файла, последний автоматически удаляется.
Функция генерации имени временного файла:
```c
char * tmpnam(char *buffer);
```

#### Удаление файла ####

```c
int remove(const char *filename);
```
Функция возвращает 0 в случае успеха, не ноль в противном случае.

#### Переименование файла ####

```c
int rename(const char *fname, const char *nname);
```
Функция возвращает 0 в случае успеха, не ноль в противном случае.