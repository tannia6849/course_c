# course_c
### [Глава №1. Итоговый тест](/chapter1.md)
### Глава №2. Итоговый тест
### Глава №3. Итоговый тест
#### Задание 1
```cpp
#include <iostream>

// Функция readNumber запрашивает у пользователя целое число
int readNumber()
{
    std::cout << "Enter a number: ";
    int a;
    std::cin >> a;
    return a;
}

// Функция writeAnswer выводит результат на экран
void writeAnswer(int b)
{
    std::cout << "Sum of number: " << b << std::endl;
}

int main()
{
    int x = readNumber();
    int y = readNumber();
    writeAnswer(x + y); // передаем результат в функцию writeAnswer()
    return 0;
}
```

#### Задание 2
main.cpp:  
```cpp
#include <iostream>

int readNumber();
void writeAnswer(int b);

int main()
{
    int x = readNumber();
    int y = readNumber();
    writeAnswer(x+y);
    return 0;
}
```
io.cpp:  
```cpp
#include <iostream>
 
int readNumber()
{
    std::cout << "Enter a number: ";
    int a;
    std::cin >> a;
    return a;
}
 
void writeAnswer(int b)
{
    std::cout << "Sum of number: " << b << std::endl;
}
```

#### Задание 3
io.h:  
```cpp
#ifndef IO_H
#define IO_H
 
int readNumber();
void writeAnswer(int b);
 
#endif
```
main.cpp:  
```cpp
#include <iostream>
#include "io.h"
int main()
{
    int x = readNumber();
    int y = readNumber();
    writeAnswer(x+y);
    return 0;
}
```
io.cpp:  
```cpp
#include <iostream>
 
int readNumber()
{
    std::cout << "Enter a number: ";
    int a;
    std::cin >> a;
    return a;
}
 
void writeAnswer(int b)
{
    std::cout << "Sum of number: " << b << std::endl;
}
```
