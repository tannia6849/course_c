# Глава №3. Итоговый тест
#### Задание 1
Вычислите результат следующих выражений:
- (5 > 3 && 4 < 8)
- (4 > 6 && true)
- (3 >= 3 || false)
- (true || false) ? 4 : 5
```cpp
#include <iostream>

int main()
{
    int n;
    n = (5 > 3 && 4 < 8);
    std::cout <<"(5 > 3 && 4 < 8). Result: " << n << std::endl;
    n = (4 > 6 && true);
    std::cout <<"(4 > 6 && true). Result: " << n << std::endl;
    n = (3 >= 3 || false);
    std::cout <<"(3 >= 3 || false) Result: " << n << std::endl;
    n = (true || false) ? 4 : 5;
    std::cout <<"(true || false) ? 4 : 5. Result: " << n << std::endl;
    return 0;
}
```
#### Результат
![результат](/test3_zad1.jpg)

#### Задание 2
Вычислите результат следующих выражений:
- 7 / 4
- 14 % 5  
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
#### Результат
![результат](/test3_zad2.jpg)
