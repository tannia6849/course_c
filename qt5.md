# Введение в QT и установка QT Creator
## Урок №1
![установка](/Урок_1_установкаQT.jpg)
## Урок №2. Строки в Qt5 и класс QString
#### Строки
``` cpp
#include <QTextStream> // подключаем необходимый заголовочный файл
 
int main() {
 
   QTextStream out(stdout); 
   
   // Создаем строку типа QString
   QString a = "love";
   
   // Добавляем текст в конец строки
   a.append(" chess");
 
   // Добавляем текст в начало строки
   a.prepend("I ");
   
   // Выводим строку
   out << a << endl;
 
   // Выводим количество символов строки
   out << "The a string has " << a.count() << " characters" << endl;
   
   // Выводим всю строку в верхнем регистре
   out << a.toUpper() << endl;    
 
   // Выводим всю строку в нижнем регистре
   out << a.toLower() << endl;
   
   return 0;
}
```
![Результат](/strings.jpg)

#### Доступ к элементам строки
```cpp
#include <QTextStream>
 
int main() {
 
   QTextStream out(stdout);
   
   // Исходная строка
   QString a = "Eagle";
 
   // Выводим первый символ строки
   out << a[0] << endl;
 
   // Выводим пятый символ строки
   out << a[4] << endl;
   
   // Выводим первый символ строки с помощью метода at()
   out << a.at(0) << endl;
   
   return 0;
}
```
![Результат](/strings1.jpg)
#### Буквы
``` cpp
#include <QTextStream>
 
int main() {
 
  QTextStream out(stdout);
   
  // Создаем по одной переменной для каждой категории символов
  int digits  = 0;
  int letters = 0;
  int spaces  = 0;
  int puncts  = 0;
  
  // Исходная строка
  QString str = "7 white, 3 red roses.";
  
  // Выполняем посимвольный перебор строки
  foreach(QChar s, str) {
  
    // Используем необходимые методы для сортировки символов по соответствующим категориям
    if (s.isDigit()) {
      digits++;
    } else if (s.isLetter()) {
      letters++;
    } else if (s.isSpace()) {
      spaces++;
    } else if (s.isPunct()) {
      puncts++;
    }    
  }  
  
  // Выводим результат на экран
  out << QString("There are %1 characters").arg(str.count()) << endl;
  out << QString("There are %1 letters").arg(letters) << endl;
  out << QString("There are %1 digits").arg(digits) << endl;
  out << QString("There are %1 spaces").arg(spaces) << endl;
  out << QString("There are %1 punctuation characters").arg(puncts) << endl;
    
  return 0;
}
```
![Результат](/strings2.jpg)
## Урок №3
#### Текущая дата и время
``` cpp
#include <QTextStream>
#include <QTime>
#include <QDate>

int main() {

   QTextStream out(stdout);

   QDate cd = QDate::currentDate(); // возвращаем текущую дату
   QTime ct = QTime::currentTime(); // возвращаем текущее время

   // Выполняем конвертацию даты и времени в строки и выводим их
   out << "Current date is: " << cd.toString() << endl;
   out << "Current time is: " << ct.toString() << endl;

   return 0;
}

```
![Результат](/time.jpg)

#### Работа с днями неделями
``` cpp
#include <QTextStream>
#include <QDate>
 
 
int main() {
 
   QTextStream out(stdout);
 
   // Получаем текущую дату
   QDate cd = QDate::currentDate();
   int wd = cd.dayOfWeek(); // определяем название дня недели
 
   QLocale loc;
 
   out << "Today is " << QDate::shortDayName(wd) << endl; // выводим короткое название дня недели
   out << "Today is " << QDate::longDayName(wd) << endl; // выводим полное название дня недели
 
   return 0;
}
```
![Результат](/time1.jpg)
## Урок №4
## Урок №5
