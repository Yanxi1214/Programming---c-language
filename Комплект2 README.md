Чжан Жуйюй , 1 курс, ИВТ-1.2, группа Ⅱ



## 2.1:Координаты Марса

**Постановка задачи**:

Вычислить координаты планеты Марс относительно Земли с течением времени t. 
Распечатать на экране координаты для каждой итерации по t. 

**Координаты Марса**: $x = r_1 \cos(\omega_1 t) - r_2 \cos(\omega_2 t)$, 
$y = r_1 \sin(\omega_1 t) - r_2 \sin(\omega_2 t)$.    


$$  
\begin{aligned}  
\omega_1 &= \frac{2\pi}{T_1}, \\  
\omega_2 &= \frac{2\pi}{T_2}, \\  
x &= r_1 \cos(\omega_1 t) - r_2 \cos(\omega_2 t), \\  
y &= r_1 \sin(\omega_1 t) - r_2 \sin(\omega_2 t).  
\end{aligned}  
$$  


**Список идентификаторов**:

| Имя переменной | Тип данных | Описание                     |
| -------------- | ---------- | ---------------------------- |
| r1             | double     | Радиус орбиты Марса (км)     |
| r2             | double     | Радиус орбиты Земли (км)     |
| T1             | double     | Период обращения Марса (дни  |
| T2             | double     | Период обращения Земли (дни) |
| t              | int        | Момент времени (дни)         |


#include <stdio.h>  
#include <math.h>  

#define PI 3.1415926535  

int main() 
{  
    double r1 = 227.9e6;  // Радиус орбиты Марса (км)  
    double r2 = 149.6e6; // Радиус орбиты Земли (км)  
    double T1 = 687.0;   // Период обращения Марса (дни)  
    double T2 = 365.25;  // Период обращения Земли (дни)  
    int t_max = 10;      // Время в днях  

    for (int t = 0; t <= t_max; t++) 
    {  
        double w1 = 2 * PI / T1;  
        double w2 = 2 * PI / T2;  
        double x = r1 * cos(w1 * t) - r2 * cos(w2 * t);  
        double y = r1 * sin(w1 * t) - r2 * sin(w2 * t);  
        printf("t = %d дн: x = %.2f км, y = %.2f км\n", t, x, y);  
    }  
    return 0;  
}  

![image](https://github.com/Yanxi1214/Programming---c-language/blob/Laboratory-work-I/capture_2.1.bmp)



## 2.2: Интеграл методом трапеций

$$  
\int_a^b f(x) dx \approx \frac{h}{2} \left[ f(a) + f(b) \right] + h \sum_{i=1}^{n-1} f(a + i h), \quad h = \frac{b - a}{n}.  
$$  

**Список идентификаторов**:

| Имя переменной | Тип данных | Описание                      |
| -------------- | ---------- | ----------------------------- |
| a              | double     | Нижний предел интегрирования  |
| b              | double     | Верхний предел интегрирования |
| n              | int        | Количество интервалов         |
| h              | double     | Шаг интегрирования            |

**Код**:

#include <stdio.h>  
#include <math.h>  

double f(double x) 
{  
    return exp(x + 2);  
}  

int main() 
{  
    double a = 0.0, b = 1.0;  
    int n = 1000;  
    double h = (b - a) / n;  
    double sum = 0.5 * (f(a) + f(b));  

    for (int i = 1; i < n; i++) 
    {  
        sum += f(a + i * h);  
    }  
    sum *= h;  

    printf("∫₀¹ e^(x+2) dx ≈ %.6f\n", sum);  
    return 0;  
}  

![image](https://github.com/Yanxi1214/Programming---c-language/blob/Laboratory-work-I/2.2.bmp)



##  2.3: Числа Падована

**Постановка задачи**:

Распечатать последовательность чисел Падована, не превосходящих m. Формулы:
P(0)=P(1)=P(2)=1,P(n)=P(n−2)+P(n−3).

**Список идентификаторов**:

| Имя переменной | Тип данных | Описание       |
| -------------- | ---------- | -------------- |
| m              | int        | Верхний предел |
| p_prev3        | int        | P(n-3)         |
| p_prev2        | int        | P(n-2)         |

**Код**:

#include <stdio.h>  

int main() 
{  
    int m;  
    printf("Введите m: ");  
    scanf("%d", &m);  

    int p_prev3 = 1, p_prev2 = 1, p_prev1 = 1;  
    printf("1 1 1 ");  

    for (int n = 3; ; n++) 
    {  
        int p = p_prev2 + p_prev3;  
        if (p > m) break;  
        printf("%d ", p);  
        p_prev3 = p_prev2;  
        p_prev2 = p_prev1;  
        p_prev1 = p;  
    }  
    return 0;  
}  

![image](https://github.com/Yanxi1214/Programming---c-language/blob/Laboratory-work-I/2.3.bmp)



## 2.4: Сумма цифр трёхзначного числа

**Постановка задачи**:

Вводить трёхзначные числа до тех пор, пока сумма их цифр не станет ≤ 10.

**писок идентификаторов**:
| Имя переменной | Тип данных | Описание        |
| -------------- | ---------- | --------------- |
| num            | int        | Введённое число |
| sum            | int        | Сумма цифр      |

**Код**:

#include <stdio.h>  

int main() 
{  
    int num, sum;  
    do 
    {  
        printf("Введите трёхзначное число: ");  
        scanf("%d", &num);  
        sum = (num / 100) + (num / 10 % 10) + (num % 10);  
    } while (sum > 10);  
    printf("Сумма цифр = %d. Программа завершена.\n", sum);  
    return 0;  
}  

![image](https://github.com/Yanxi1214/Programming---c-language/blob/Laboratory-work-I/2.4.bmp)
