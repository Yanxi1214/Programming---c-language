# Лабораторная работа 2 - Указатели, арифметика указателей

## Задача 1 - Многоуровневое выделение памяти через указатели

### Постановка задачи

Определите указатель `double ***pointer = NULL;` внутри `main()`. Инициализируйте его адресом указателя `double**`, который указывает на `double*`, а тот — на `double`. Запишите значение 2.0 в память через `pointer` и выведите его.

### Математическая модель

pointer → double** → double* → double (2.0)

### Список идентификаторов
| Имя переменной | Тип данных       | Описание                     |
|----------------|------------------|------------------------------|
| pointer        | double***        | Трехуровневый указатель      |
| dbl_value      | double*          | Указатель на double          |
| ptr_to_dbl     | double**         | Указатель на double*         |


### Код 
```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    double ***pointer = NULL;
    double **ptr_to_dbl = (double**)malloc(sizeof(double*));
    double *dbl_value = (double*)malloc(sizeof(double));
    
    *dbl_value = 2.0;
    *ptr_to_dbl = dbl_value;
    pointer = &ptr_to_dbl;
    
    printf("Значение: %.1f\n", ***pointer);
    
    free(dbl_value);
    free(ptr_to_dbl);
    return 0;
}
```

 ![image](https://github.com/Yanxi1214/Programming---c-language/blob/Laboratory-work-2/1.bmp)


 ## Задача 2 - Сложение двух чисел через указатели

### Постановка задачи
Сложить два числа, используя указатели.

### Код:
```c
#include <stdio.h>

int main(void)
{
    int a = 5, b = 3;
    int *pa = &a, *pb = &b;
    int sum = *pa + *pb;
    printf("Сумма: %d\n", sum);
    return 0;
}
```



## Задача 3 - Максимум из двух чисел через указатели
### Постановка задачи:
Найти максимальное из двух чисел через указатели.

### Код:
