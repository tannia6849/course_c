# course_c
### Глава №1. Итоговый тест
#### Задание 1
```cpp
#include <iostream>
 
int readNumber()
{
    std::cout << "Enter a number: ";
    int x;
    std::cin >> x;
    return x;
}
 
void writeAnswer(int x)
{
    std::cout << "The answer is " << x << std::endl;
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

#### Задание 3
