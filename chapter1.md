# Глава №1. Итоговый тест
#### Задание 1
Напишите однофайловую программу (с именем main.cpp), которая запрашивает у пользователя два целых числа, складывает их, а затем выводит результат. В программе должно быть 3 функции:
- функция readNumber(), которая запрашивает у пользователя целое число, а затем возвращает его в main();
- функция writeAnswer(), которая выводит результат на экран. Функция должна быть без возвращаемого значения и иметь только один параметр;
- функция main(), которая соединяет всё и вся.
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
Измените программу из задания №1 так, чтобы функции readNumber() и writeAnswer() находились в отдельном файле io.cpp. Используйте предварительные объявления для доступа к этим функциям с функции main().
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
Измените программу из задания №2 так, чтобы она использовала заголовочный файл io.h для доступа к функциям (вместо использования предварительных объявлений). Убедитесь, что ваш заголовочный файл использует header guards.
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
#### Результат работы 
![Работа](/test1_zad1.jpg)
