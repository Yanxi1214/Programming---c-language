Чжан Жуйюй , 1 курс, ИВТ-1.2, группа Ⅱ



## 3.1: Вектор Y = X²

**Постановка задачи**:

Для вектора X, введённого с клавиатуры, вычислить Y=X⋅X.

**Список идентификаторов**:
| Имя переменной | Тип данных | Описание              |
| -------------- | -----------| ----------------------|
| x              | double[]   | Исходный вектор       |
| y              | double[]   | Результирующий вектор |


```c
#include <stdio.h>  
#define SIZE 5  

int main()
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



## 3.2: Обратный массив
**Постановка задачи**:
Изменить порядок элементов массива на обратный.

**Список идентификаторов**:
| Имя переменной | Тип данных | Описание        |
| -------------- | ---------- | --------------- |
| x              | int[]      | Исходный массив |

```c
#include <stdio.h>  
#define SIZE 5  

int main() 
{  
    int X[SIZE];  
    printf("Введите %d элементов: ", SIZE);  
    for (int i = 0; i < SIZE; i++) scanf("%d", &X[i]);  

    printf("Обратный массив: [");  
    for (int i = SIZE - 1; i >= 0; i--) printf("%d ", X[i]);  
    printf("]\n");  
    return 0;  
}  

![image](https://github.com/Yanxi1214/Programming---c-language/blob/Laboratory-work-I/3.2.bmp)



## 3.3: Транспонирование матрицы

**Постановка задачи**:
Транспонировать матрицу A.

**Список идентификаторов**:
| Имя переменной | Тип данных | Описание         |
| -------------- | ---------- | ---------------- |
| A              | int[][]    | Исходная матрица |


$$  
A = \begin{bmatrix}  
1 & 2 & 3 \\  
4 & 5 & 6 \\  
7 & 8 & 9  
\end{bmatrix}, \quad  
A^{\text{T}} = \begin{bmatrix}  
1 & 4 & 7 \\  
2 & 5 & 8 \\  
3 & 6 & 9  
\end{bmatrix}.  
$$  

```c
#include <stdio.h>  

int main() 
{  
    int A[3][3] = {{1,2,3}, {4,5,6}, {7,8,9}};  
    printf("Транспонированная матрица:\n");  
    for (int j = 0; j < 3; j++) 
    {  
        for (int i = 0; i < 3; i++) printf("%d ", A[i][j]);  
        printf("\n");  
    }  
    return 0;  
}  


![image](https://github.com/Yanxi1214/Programming---c-language/blob/Laboratory-work-I/3.3.bmp)



## 3.4: Замена первого элемента строки

**Постановка задачи**:
Заменить первый элемент каждой строки на среднее арифметическое элементов строки.

**Список идентификаторов**:
| Имя переменной | Тип данных | Описание               |
| -------------- | ---------- | ---------------------- |
| A              | float[][]  | Исходная матрица       |
| sum            | float      | Сумма элементов строки |

```c
#include <stdio.h>  

int main() 
{  
    float A[3][3] = {{1,2,3}, {4,5,6}, {7,8,9}};  
    for (int i = 0; i < 3; i++) 
    {  
        float sum = 0;  
        for (int j = 0; j < 3; j++) sum += A[i][j];  
        A[i][0] = sum / 3;  
    }  

    printf("Новая матрица:\n");  
    for (int i = 0; i < 3; i++) 
    {  
        for (int j = 0; j < 3; j++) printf("%.2f ", A[i][j]);  
        printf("\n");  
    }  
    return 0;  
}  


![image](https://github.com/Yanxi1214/Programming---c-language/blob/Laboratory-work-I/3.4.bmp)


## 3.5: Сортировка вставками

**остановка задачи**:
Реализовать сортировку вставками для массива.

**Список идентификаторов**:
| Имя переменной | Тип данных |	Описание           |
| -------------- | ---------- | ------------------ |
| arr            | int[]	  | Сортируемый массив |
| key            | int	      | Текущий элемент    |


```c
#include <stdio.h>  
#define SIZE 5  

int main() 
{  
    int arr[SIZE] = {5, 2, 4, 6, 1};  
    for (int i = 1; i < SIZE; i++) 
    {  
        int key = arr[i];  
        int j = i - 1;  
        while (j >= 0 && arr[j] > key) 
        {  
            arr[j + 1] = arr[j];  
            j--;  
        }  
        arr[j + 1] = key;  
    }  

    printf("Отсортированный массив: [");  
    for (int i = 0; i < SIZE; i++) printf("%d ", arr[i]);  
    printf("]\n");  
    return 0;  
}  


![image](https://github.com/Yanxi1214/Programming---c-language/blob/Laboratory-work-I/3.5.bmp)
