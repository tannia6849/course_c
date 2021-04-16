# Глава №1. Итоговый тест
#### Задание 3
Напишите следующую программу. Сначала пользователю предлагается ввести 2 числа типа с плавающей точкой (используйте тип double). 
Затем предлагается ввести один из следующих математических символов: +, -, * или /. Программа выполняет выбранную пользователем математическую операцию 
между двумя числами, а затем выводит результат на экран. Если пользователь ввел некорректный символ, то программа ничего не должна выводить.   
```cpp
#include <iostream>
 
double getDouble()
{
    std::cout << "Enter a double value: ";
    double x;
    std::cin >> x;
    return x;
}
 
char getOperator()
{
    std::cout << "Enter one of the following (+, -, *, or /): ";
    char op;
    std::cin >> op;
    return op;
}
 
void printResult(double x, char op, double y)
{
    if (op == '+')
        std::cout << x << " + " << y << " = " << x + y << '\n';
    else if (op == '-')
        std::cout << x << " - " << y << " = " << x - y << '\n';
    else if (op == '*')
        std::cout << x << " * " << y << " = " << x * y << '\n';
    else if (op == '/')
        std::cout << x << " / " << y << " = " << x / y << '\n';
}
 
int main()
{
    double x = getDouble();
    double y = getDouble();
 
    char op = getOperator();
 
    printResult(x, op, y);
 
    return 0;
}
```

#### Задание 4
Напишите небольшую программу-симулятор падения мячика с башни. Сначала пользователю предлагается ввести высоту башни в метрах. 
Не забывайте о гравитации (9,8м/с2) и о том, что у мячика нет начальной скорости (его держат в руках). Программа должна выводить расстояние от земли, 
на котором находится мячик после 0, 1, 2, 3, 4 и 5 секунд падения. Минимальная высота составляет 0 метров (ниже мячику падать нельзя).  
В программе должен быть заголовочный файл constants.h с пространством имен myConstants. В myConstants определите символьную константу 
для хранения значения силы тяжести на Земле (9.8). 
Напишите функцию для вычисления высоты мячика через х секунд падения. Используйте следующую формулу: высота мячика над землей = константа_гравитации * x_секунд2/2.  
constants.h: 
```cpp
#ifndef CONSTANTS_H
#define CONSTANTS_H
 
namespace myConstants
{
    const double gravity(9.8); 
}
#endif
```
main.cpp:  
```cpp
#include <iostream>
#include "constants.h"
 
double getInitialHeight()
{
	std::cout << "Enter the initial height of the tower in meters: ";
	double initialHeight;
	std::cin >> initialHeight;
	return initialHeight;
}
 
double calculateHeight(double initialHeight, int seconds)
{
	double distanceFallen = (myConstants::gravity * seconds * seconds) / 2;
	double currentHeight = initialHeight - distanceFallen;
 
	return currentHeight;
}
 
void printHeight(double height, int seconds)
{
	if (height > 0.0)
		std::cout << "At " << seconds << " seconds, the ball is at height: " << height << " meters\n";
	else
		std::cout << "At " << seconds << " seconds, the ball is on the ground.\n";
}
 
void calculateAndPrintHeight(double initialHeight, int seconds)
{
	double height = calculateHeight(initialHeight, seconds);
	printHeight(height, seconds);
}
 
int main()
{
	const double initialHeight = getInitialHeight();
 
	calculateAndPrintHeight(initialHeight, 0);
	calculateAndPrintHeight(initialHeight, 1);
	calculateAndPrintHeight(initialHeight, 2);
	calculateAndPrintHeight(initialHeight, 3);
	calculateAndPrintHeight(initialHeight, 4);
	calculateAndPrintHeight(initialHeight, 5);
 
	return 0;
}
```

#### Результат работы 
![Работа](/test1_zad1.jpg)
