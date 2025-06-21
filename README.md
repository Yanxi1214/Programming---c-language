# Лабораторная работа 3

## Комплект 1: Структуры

## Задача 1.1

### Постановка задачи

Создать некоторую структуру с указателем на некоторую функцию в качестве поля. Вызвать эту функцию через имя переменной этой структуры и поле указателя на функцию.

### Список идентификаторов
| Имя переменной | Тип данных       | Описание             |           
|----------------|------------------|----------------------|
| func           | void (*)(void)   | Указатель на функцию |
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
![image](1.1.png)


## 1.2

### Постановка задачи

Создать структуру для вектора в 3-х мерном пространстве. Реализо-вать и использховать в своей программе следующие операции над векторами

| Имя переменной | Тип данных | Описание           |
| -------------- | ---------  | ------------------ |
| x, y, z        | float      | Координаты вектора |
| name           | char[]     | Имя вектора        |

```c
#include <stdio.h>
#include <math.h>
#include <string.h>

struct Vector3 
{
    char name[10];
    float x, y, z;
};

float dot(struct Vector3 a, struct Vector3 b) 
{
    return a.x*b.x + a.y*b.y + a.z*b.z;
}

struct Vector3 cross(struct Vector3 a, struct Vector3 b) 
{
    struct Vector3 result = {"cross", 
        a.y*b.z - a.z*b.y,
        a.z*b.x - a.x*b.z,
        a.x*b.y - a.y*b.x
    };
    return result;
}

float magnitude(struct Vector3 v) 
{
    return sqrt(v.x*v.x + v.y*v.y + v.z*v.z);
}

void print(struct Vector3 v) 
{
    printf("%s: (%.2f, %.2f, %.2f)\n", v.name, v.x, v.y, v.z);
}

int main() {
    struct Vector3 a = {"A", 1.0, 2.0, 3.0};
    struct Vector3 b = {"B", 4.0, 5.0, 6.0};

    print(a);
    print(b);

    printf("Скалярное произведение: %.2f\n", dot(a, b));
    print(cross(a, b));
    printf("Модуль A: %.2f\n", magnitude(a));
    return 0;
}

```

![image](1.2.png)



## 1.3

### Постановка задачи

Реализовать exp(z) для комплексного z ∈ ℂ с использованием разложения в ряд.

```c
#include <stdio.h>
#include <math.h>

typedef struct
{
    double real;
    double imag;
} Complex;

Complex complexExp(Complex c)
{
    Complex result;
    double exp_real = exp(c.real) * cos(c.imag);
    double exp_imag = exp(c.real) * sin(c.imag);
    result.real = exp_real;
    result.imag = exp_imag;
    return result;
}

int main() {
    Complex z = {0.0, 1.0}; // Example: e^(i)
    Complex res = complexExp(z);
    printf("exp(z) = %.2f + %.2fi\n", res.real, res.imag);
    return 0;
}
```

![image](1.3.png)


 
## 1.4

### Постановка задачи

Использовать битовые поля для экономии памяти в структуре даты.

```c
#include <stdio.h>

struct Date
{
    unsigned day : 5;   
    unsigned month : 4;   
    unsigned year : 12;   
};

int main()
{
    struct Date birthday = {15, 6, 1990};
    printf("Дата рождения: %02u.%02u.%u\n", 
           birthday.day, birthday.month, birthday.year);
    printf("Размер структуры: %lu байт\n", sizeof(birthday));
    return 0;
}
```

![image](1.4.png)



## 1.5

### Постановка задачи

Реализовать в виде структур двунаправленный связный список и совершить отдельно его обход в прямом и обратном направлениях с распечаткой значений каждого элемента списка.

### Список идентификаторов
| Имя переменной | Тип данных |	Описание                     |
|--------------- |------------|------------------------------|
| value          | int	      | Значение элемента            |
| next           | Node*	  | Указатель на следующий узел  |
| prev	         | Node*	  | Указатель на предыдущий узел |

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct Node
{
    int data;
    struct Node* prev;
    struct Node* next;
} Node;

Node* createNode(int value)
{
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->data = value;
    newNode->prev = NULL;
    newNode->next = NULL;
    return newNode;
}

void traverseForward(Node* head)
{
    Node* temp = head;
    while (temp != NULL)
{
        printf("%d ", temp->data);
        temp = temp->next;
    }
    printf("\n");
}

void traverseBackward(Node* tail)
{
    Node* temp = tail;
    while (temp != NULL)
{
        printf("%d ", temp->data);
        temp = temp->prev;
    }
    printf("\n");
}

int main()
{
    Node* head = createNode(1);
    Node* second = createNode(2);
    Node* third = createNode(3);

    head->next = second;
    second->prev = head;
    second->next = third;
    third->prev = second;

    printf("Forward traversal: ");
    traverseForward(head);
    printf("Backward traversal: ");
    traverseBackward(third);

    return 0;
}
```
![image](1.5.png)



## Комплект 2: Объединения и перечисления

## 2.1 

### Постановка задачи
Напишите программу, которая использует указатель на некоторое объединение union.

### Список идентификаторов
|Имя переменной | Тип данных  |	Описание                 |
|---------------|-----------  |--------------------------|
| data          | union Data  |	Объединение с полями     |
| ptr           | union Data* |	Указатель на объединение |

```c
#include <stdio.h>

union Data
{
    int i;
    float f;
    char str[20];
};

int main() 
{

    union Data *dataPtr;
    union Data data;

    dataPtr = &data; 
    dataPtr->i = 10;
    printf("data.i: %d\n", dataPtr->i);

    dataPtr->f = 220.5;
    printf("data.f: %.1f\n", dataPtr->f);

    strcpy(dataPtr->str, "C Programming");
    printf("data.str: %s\n", dataPtr->str);

    return 0;
}
```

## Задача 2.2 

### Постановка задачи

Напишите программу, которая использует union для побайтовой распечатки типа unsigned long.

```c
#include <stdio.h>

union BytePrinter
{
    unsigned long value;
    unsigned char bytes[sizeof(unsigned long)];
};

void printBytes(union BytePrinter data)
{
    for (size_t i = 0; i < sizeof(unsigned long); ++i)
{
        printf("%02x ", data.bytes[i]);
    }
    printf("\n");
}

int main()
{
    union BytePrinter data;
    data.value = 123456789UL;
    
    printf("Value as bytes: ");
    printBytes(data);
    
    return 0;
}
```

![image](2.2.png)


## 2.3 

### Постановка задачи

Создайте перечислимый тип данных (enum) для семи дней недели и распечатайте на экране его значения, как целые числа.

### Список идентификаторов
| Имя переменной | Тип данных |	Описание     |
|----------------|------------|--------------|
| Weekday        | enum	      | Перечисление |
| day	         | int        |	Значение дня |

```c
#include <stdio.h>

enum Weekday { MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY };

int main()
{
    enum Weekday today = SATURDAY;
    
    printf("Today is day number: %d\n", today);
    for (int i = MONDAY; i <= SUNDAY; ++i)
    {
        printf("Day %d: %d\n", i, i);
    }

    return 0;
}
```

![image](2.3.png)
