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
