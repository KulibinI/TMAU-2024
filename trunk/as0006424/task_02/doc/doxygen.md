# Описание файла

Этот файл содержит описание классов, предназначенных для моделирования линейных и нелинейных систем, а также пропорционально-интегрально-дифференцирующего (ПИД) регулятора.

# Описание классов


Класс | Описание
-------|--------
LinearModel|	Класс, представляющий линейную модель.
Model	|Абстрактный класс для моделей.
NonlinearModel|	Класс, представляющий нелинейную модель.
PIDregulator|	Класс пропорционально-интегрально-дифференцирующего (ПИД) регулятора.

# Описание класса `LinearModel` 

```
class LinearModel : public Model
```  

Класс для реализации линейной модели.

## Свойства и методы

 Свойства и методы | Описание
-------|----------
Конструктор LinearModel(double a, double b)|	Создает линейную модель с параметрами a и b.
Метод temperature_simulation(double Yt, double Uw)|	Переопределенный метод расчета выходного значения для линейной модели.
Деструктор ~LinearModel()|	Деструктор по умолчанию.
a, b|	Приватные параметры линейной модели.

# Описание класса `Model` 

Абстрактный класс для представления моделей.

## Свойства и методы

 Свойства и методы| Описание 
--------|-------
Метод temperature_simulation(double Yt, double Uw)|	Виртуальная функция для расчета температуры.
Деструктор ~Model()|	Виртуальный деструктор по умолчанию.

# Описание класса `NonlinearModel` 

```
class NonlinearModel : public Model
```  

Класс для реализации нелинейной модели.

## Свойства и методы

 Свойства и методы | Описание
-----------|------------
Конструктор NonlinearModel(double a, double b, double c, double d)|	Создает нелинейную модель с параметрами a, b, c, d.
Метод temperature_simulation(double Yt, double Uw)	|Переопределенный метод расчета выходного значения для нелинейной модели.
Деструктор ~NonlinearModel()|	Деструктор по умолчанию.
a, b, c, d	|Приватные параметры нелинейной модели.
Yt_last, Uw_last|	Приватные переменные для хранения предыдущих значений температуры и тепла.

# Описание класса `PIDregulator` 

Класс для реализации ПИД-регулятора.

## Свойства и методы

 Свойства и методы  | Описание
-----------|----------
Метод Regulate(double w, double y0, Model & model)|	Реализует ПИД-регулятор для заданной модели.
Коэффициенты K, T, TD, T0|	Константы для расчета регулирующего значения.
Время симуляции SimulationTime|	Время симуляции регулятора.
Значение переменной управления Uk	|Текущее значение управляющей переменной.
Метод calculate_Uk(double e, double e1, double e2)	|Вычисляет обновленное значение управляющей переменной.