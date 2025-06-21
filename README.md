# Лабораторная работа 3

## Комплект 1: Структуры

## Задача 1.1

### Постановка задачи

Создать некоторую структуру с указателем на некоторую функцию в качестве поля. Вызвать эту функцию через имя переменной этой структуры и поле указателя на функцию.

### Список идентификаторов
| Имя переменной | Тип данных       | Описание             |           
|----------------|------------------|----------------------|
| funcPtr        | void (*)(void)   | Указатель на функцию |
| s	             | struct           | Экземпляр структуры  |


```c
#include <stdio.h>


typedef struct
{
    void (*func)(void); 
} MyStruct;


void myFunction()
{
    printf("Hello from myFunction!\n");
}

int main()
{
    MyStruct s;
    s.func = myFunction; 
    s.func(); 
    return 0;
}
```
![image].(https://github.com/Yanxi1214/Programming---c-language/blob/1%D0%BE%D0%B1_%D0%98%D0%92%D0%A2-1/24_%D0%A7%D0%B6%D0%B0%D0%BD-%D0%96%D1%83%D0%B9%D1%8E%D0%B9_3/1.1.png)
