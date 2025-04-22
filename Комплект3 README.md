## 3.1: Вектор Y = X²

**Постановка задачи**:

Для вектора X, введённого с клавиатуры, вычислить Y=X⋅X.

**Список идентификаторов**:
| Имя переменной | Тип данных | Описание              |
| -------------- | -----------| ----------------------|
| x              | double[]   | Исходный вектор       |
| y              | double[]   | Результирующий вектор |


#include <stdio.h>  
#define SIZE 5  

int main()\
{  
    double X[SIZE], Y[SIZE];  
    printf("Введите %d элементов X: ", SIZE);  
    for (int i = 0; i < SIZE; i++) 
    {  
        scanf("%lf", &X[i]);  
        Y[i] = X[i] * X[i];  
    }  

    printf("Y = [");  
    for (int i = 0; i < SIZE; i++) printf("%.2f ", Y[i]);  
    printf("]\n");  
    return 0;  
}  

![image](https://github.com/Yanxi1214/Programming---c-language/blob/Laboratory-work-I/3.1.bmp)


