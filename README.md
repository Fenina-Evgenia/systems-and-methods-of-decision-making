# systems-and-methods-of-decision-making

# Метрические алгоритмы классификации

Метрический классификатор - алгоритм классификации, основанный на вычислении оценок сходства между объектами.

Гипотеза компактности: cхожим объектам соответствуют схожие ответы.

**_Мерой близости_** называют функцию расстояния ![](http://latex.codecogs.com/svg.latex?%5Clarge%20%5Crho%3A%20%28X%20%5Ctimes%20X%29%20%5Crightarrow%20%5Cmathbb%7BR%7D). Чем меньше расстояние между объектами, тем больше объекты похожи друг на друга.

Метрические алгоритмы классификации с обучающей выборкой *Xl* относят объект *u* к тому классу *y*, для которого **суммарный вес ближайших обучающих объектов ![](https://latex.codecogs.com/gif.latex?W_y%28u%2C%20X%5El%29) максимален**:
![](https://latex.codecogs.com/gif.latex?W_y%28u%2C%20X%5El%29%20%3D%20%5Csum_%7Bi%20%3A%20y_%7Bu%7D%5E%7B%28i%29%7D%20%3D%20y%7D%20w%28i%2C%20u%29%20%5Crightarrow%20max)
, где весовая функция *w(i, u)* оценивает степень важности *i*-го соседа для классификации объекта *u*.

Функция ![](https://latex.codecogs.com/gif.latex?W_y%28u%2C%20X%5El%29) называется **_оценкой близости объекта u к классу y_**. Выбирая различную весовую функцию *w(i, u)* можно получать различные метрические классификаторы.

К метрическим методам классификации относятся:
- KNN - алгоритм k ближайших соседей
- KwNN - алгоритм k взвешенных ближайших соседей
- PW - метод парзеновского окна
- PF - метод	потенциальных	функций
- STOLP - алгоритм отбора	эталонных	объектов

## Алгоритм k ближайших соседей (kNN)

Имеется некоторая выборка *Xl*, состоящая из объектов *x(i), i = 1, ..., l* (в приложенной программе используется выборка ирисов Фишера).
Данный алгоритм классификации относит классифицируемый объект *u* к тому классу *y*, к которому относится большинство из *k* его ближайших соседей *x(u_i)*.

Для оценки близости классифицируемого объекта *u* к классу *y* **алгоритм kNN** использует следующую функцию:

![](http://latex.codecogs.com/svg.latex?%5Clarge%20W%28i%2C%20u%29%20%3D%20%5Bi%20%5Cleq%20k%5D) , где *i* - порядок соседа по расстоянию к классифицируемому объекту *u*.

Реализация алгоритма: [kNN](knn.R)

Иллюстрация к проекту:

![alt text](https://github.com/Fenina-Evgenia/systems-and-methods-of-decision-making/blob/master/knn.png)

### Преимущества:
1. Простота реализации.

2. При **k** (оптимальном), алгоритм "неплохо" классифицирует.

### Недостатки:
1. Нужно хранить всю выборку.

2. При **k = 1** неустойчивость к погрешностям , выброс(погрешность) классифицируется неверно окружающие его объекты.

3. При **k = l** алгоритм вырождается в константу.

4. Малый набор параметров.

5. Точки с одинаковым расстоянием вызывают неопределенность 
