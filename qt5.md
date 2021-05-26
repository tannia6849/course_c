# Введение в QT и установка QT Creator
## Урок №1 Введение в Qt и установка Qt Creator
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
## Урок №3 Дата и время в Qt5
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
## Урок №4 Контейнеры в Qt5
#### Контейнер QVector
``` cpp
#include <QVector>
#include <QTextStream>
 
int main(void) {
 
    QTextStream out(stdout);
    
    // Создаем вектор, содержащий целочисленные значения
    QVector<int> vals = {1, 2, 3, 4, 5};
    
    // С помощью метода size() возвращаем размер вектора (количество элементов, содержащихся в нем)
    out << "The size of the vector is: " << vals.size() << endl;
       
    out << "The first item is: " << vals.first() << endl; // получаем первый элемент вектора
    out << "The last item is: " << vals.last() << endl; // получаем последний элемент вектора
    
    vals.append(6); // вставляем новый элемент в конец вектора
    vals.prepend(0); // вставляем новый элемент в начало вектора
    
    out << "Elements: "; 
    
    // Перебираем элементы вектора и выводим их на экран
    for (int val : vals) {
        out << val << " ";
    }    
    
    out << endl;
   
    return 0;
}
```
![Результат](/контейнер.jpg)
#### Контейнер QList
``` cpp
#include <QTextStream>
#include <QList>
#include <algorithm>

int main(void) {

    QTextStream out(stdout);

    // Создаем контейнер QList, в котором будем хранить имена писателей
    QList<QString> authors = {"Balzac", "Tolstoy",
        "Gulbranssen", "London"};

    // Перебираем каждый элемент массива и выводим на экран
    for (int i=0; i < authors.size(); ++i) {

        out << authors.at(i) << endl; // метод at() возвращает элемент с указанным индексом
    }

    // С помощью оператора << вставляем в список 2 новых элемента
    authors << "Galsworthy" << "Sienkiewicz";

    out << "***********************" << endl;

    // С помощью метода sort() сортируем список в порядке возрастания
    std::sort(authors.begin(), authors.end());

    // Выводим на экран отсортированный список
    out << "Sorted:" << endl;
    for (QString author : authors) {

        out << author << endl;
    }
}
```
![Результат](/контейнер1.jpg)
#### Контейнер QStringList
``` cpp
#include <QTextStream>
#include <QList>
 
int main(void) {
 
    QTextStream out(stdout);
 
    QString string = "coin, book, cup, pencil, clock, bookmark";
 
    // С помощью метода split() разделяем строку на подстроки 
    QStringList items = string.split(",");
 
    // Это константный итератор в Java-стиле для QStringList
    QStringListIterator it(items); 
    
    // С помощью созданного итератора выводим элементы списка на экран 
    while (it.hasNext()) {
        out << it.next().trimmed() << endl; // с помощью метода trimmed() удаляем пробелы из строки    
    }
}
```
![Результат](/контейнер2.jpg)
#### Контейнер QSet
``` cpp
#include <QSet>
#include <QList>
#include <QTextStream>
#include <algorithm>
 
int main(void) {
    
    QTextStream out(stdout);
 
    // Создаем 2 набора цветов 
    QSet<QString> cols1 = {"yellow", "red", "blue"};
    QSet<QString> cols2 = {"blue", "pink", "orange"};
      
    // С помощью метода size() возвращаем размер набора
    out << "There are " << cols1.size() << " values in the set" << endl;
   
    // С помощью метода insert() вставляем новый элемент
    cols1.insert("brown");
   
    out << "There are " << cols1.size() << " values in the set" << endl;
    
    // Метод unite() выполняет объединение двух наборов
    cols1.unite(cols2);
    
    out << "There are " << cols1.size() << " values in the set" << endl;
    
    // Перебираем все элементы набора cols1 и выводим их на экран
    for (QString val : cols1) {
        out << val << endl;
    }
    
    // Создаем отдельный список из набора элементов cols1 для их сортировки
    QList<QString> lcols = cols1.values(); // метод values() возвращает новый QList, содержащий элементы набора
    std::sort(lcols.begin(), lcols.end());
    
    out << "*********************" << endl;
    out << "Sorted:" << endl;
    
    for (QString val : lcols) {
        out << val << endl;
    }    
   
   return 0;
}
```
![Результат](/контейнер3.jpg)
#### Контейнер QMap
``` cpp
#include <QTextStream>
#include <QMap>
 
int main(void) {
 
    QTextStream out(stdout);
 
    // Создаем QMap, содержащий 2 пары элементов
    QMap<QString, int> items = { {"coins", 5}, {"books", 3} };
    
    // С помощью метода insert() добавляем новую пару значений 
    items.insert("bottles", 7);
    
    // Получаем все значения словаря и выводим их на экран
    QList<int> values = items.values(); // метод values() возвращает список значений словаря
    out << "Values:" << endl;
    for (int val : values) {
        out << val << endl;
    }
    
    // Аналогично выводим все ключи словаря
    QList<QString> keys = items.keys(); // метод keys() возвращает список, содержащий все ключи в словаре
    out << "Keys:" << endl;
    for (QString key : keys) {
        out << key << endl;
    }    
    
    // Создаем итератор для QMap в Java-стиле
    QMapIterator<QString, int> it(items); // этот итератор может использоваться для итерации по элементам QMap
    
    out << "Pairs:" << endl;
    
    // С помощью итератора перебираем все элементы QMap
    while (it.hasNext()) {
        it.next();
        out << it.key() << ": " << it.value() << endl; // метод key() возвращает текущий ключ, а метод value() возвращает текущее значение
    }
}
```
![Результат](/контейнер4.jpg)

## Урок №5 Работа с файлами и каталогами в Qt5
#### Чтение содержимого файлов
``` cpp
#include <QTextStream>
#include <QFile>

int main() {

  QTextStream out(stdout);

  // Создаем объект
  QFile file("E:\\colours.txt");

  // С помощью метода open() открываем файл в режиме чтения
  if (!file.open(QIODevice::ReadOnly)) {
    qWarning("Cannot open file for reading"); // если файл не найден, то выводим предупреждение и завершаем выполнение программы
    return 1;
  }

  // Создаем входящий поток, из которого будут считываться данные, и связываем его с нашим файлом
  QTextStream in(&file);

  // Считываем файл строка за строкой
  while (!in.atEnd()) { // метод atEnd() возвращает true, если в потоке больше нет данных для чтения
    QString line = in.readLine(); // метод readLine() считывает одну строку из потока
    out << line << endl;
  }

  // Закрываем файл
  file.close();
}
```
![Результат](/file.jpg)
#### Запись данных в файл
``` cpp
#include <QTextStream>
#include <QFile>

int main() {

  QTextStream out(stdout);

  // Создаем объект класса QFile и связываем его с указанным именем файла
  QString filename = "E:\\distros.txt";
  QFile file(filename);

  // Открываем файл в режиме "Только для записи"
  if (file.open(QIODevice::WriteOnly)) {
    QTextStream out(&file); // поток записываемых данных направляем в файл

    // Для записи данных в файл используем оператор <<
    out << "Xubuntu" << endl;
    out << "Arch" << endl;
    out << "Debian" << endl;
    out << "Redhat" << endl;
    out << "Slackware" << endl;

  } else {

    qWarning("Could not open file");
  }

  // Закрываем файл
  file.close();
}
```
![Результат](/file1.jpg)
