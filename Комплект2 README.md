## 2.1:Координаты Марса

**Постановка задачи**:
Вычислить координаты планеты Марс относительно Земли с течением времени t. 
Распечатать на экране координаты для каждой итерации по t. 

**Формулы**:
$x = r_1 \cos(\omega_1 t) - r_2 \cos(\omega_2 t)$
$y = r_1 \sin(\omega_1 t) - r_2 \sin(\omega_2 t)$.  

**Математическая модель**:
$$  
\begin{aligned}  
\omega_1 &= \frac{2\pi}{T_1}, \\  
\omega_2 &= \frac{2\pi}{T_2}, \\  
x &= r_1 \cos(\omega_1 t) - r_2 \cos(\omega_2 t), \\  
y &= r_1 \sin(\omega_1 t) - r_2 \sin(\omega_2 t).  
\end{aligned}  
$$  

**Список идентификаторов**:
| Имя переменной | Тип данных	| Описание                     |
| -------------- | ---------- | ---------------------------- |
| r1             | double     | Радиус орбиты Марса (км)     |
| r2             | double     | Радиус орбиты Земли (км)     |
| T1             | double     | Период обращения Марса (дни  |
| T2             | double     | Период обращения Земли (дни) |
| t              | int        | Момент времени (дни)         |


**Код программы**:

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

    ![image]
    return 0;  
}  

https://github.com/Yanxi1214/Programming---c-language/blob/Laboratory-work-I/capture_2.1.bmp

