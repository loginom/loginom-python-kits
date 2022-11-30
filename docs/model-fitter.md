# model.fitter

[Назад к списку компонентов](../README.md)

## Назначение

Компонент предназначен для обучения любой модели, как правило, статистическим алгоритмом или алгоритмом машинного обучения, на произвольном наборе данных. В наборе данных может присутствовать выходное поле (`target`). Оно требуется при использовании алгоритмов обучения на размеченных данных.

Если на второй входной порт **Тестовая выборка** подан набор данных, то к нему будет применена построенная модель.

Обученная модель может быть cохранена в сериализованный объект Python, после чего использоваться для прогона в компоненте **Model.Scorer**.

## Входные порты

| Название                | Тип        | Описание                            |
|:------------------------|:-----------|:------------------------------------|
| Обучающая выборка       | Таблица    |                                     |
| Тестовая выборка        | Таблица    | Необязательный входной набор данных |
| Входные переменные      | Переменные |                                     |

### Структура таблицы "Обучающая выборка"

На вход можно подать данные любой структуры. Столбцы, которые не планируется подавать на вход алгоритма обучения, не должны присутствовать в наборе данных, за исключением идентификатора объекта.

### Структура таблицы "Тестовая выборка"

На вход можно подать данные любой структуры, но структура должна совпадать с набором данных в порте **Обучающая выборка**.

### Переменные в порте "Входные переменные"

| №  | Метка                      | Тип                                   | Значение по умолчанию  |
|:---|:---------------------------|:--------------------------------------|:-----------------------|
| 1  | Поле с идентификатором     | ![](./img/string.svg) Строковый       |ID                      |
| 2  | Поле с событием            | ![](./img/integer.svg) Целый          |target                  |
| 3  | Путь к файлу               | ![](./img/string.svg) Строковый       |null                    |
| 4  | Имя файла для модели       | ![](./img/string.svg) Строковый       |null                    |
| 5  | Импортируемый модуль       | ![](./img/string.svg) Строковый       |null                    |
| 6  | Импортируемый класс        | ![](./img/string.svg) Строковый       |null                    |
| 7  | Только коэффициенты        | ![](./img/logical.svg) Логический     |false                   |
| 8  | Выходное поле с разбиением | ![](./img/string.svg) Строковый       |test_set                |
| 9  | Имена выходов              | ![](./img/string.svg) Строковый       |null                |
| 10  | Дополнительные выходы      | ![](./img/string.svg) Строковый       |null                    |
| 11 | fit_method                 | ![](./img/string.svg) Строковый       |fit                     |
| 12 | predict_method             | ![](./img/string.svg) Строковый       |predict                 |
| 13 | params                     | ![](./img/string.svg) Строковый       |null                    |
| 14 | *Принудительные параметры  | ![](./img/string.svg) Строковый       |null                    |

1. **Поле с идентификатором** — необязательный столбец, в котором содержится информация об идентификаторе объекта;
2. **Поле с событием** — необязательный столбец, в котором содержится информация о событиях. Событию соответствует **1**, не-событию — **0**.
3. **Путь к файлу** — полный путь к файлу, где лежит файл с именем `model_filename`;
4. **Имя файла для модели** — модель должна быть представлена в виде сериализованного объекта Python путем вызова метода [dump](https://joblib.readthedocs.io/en/latest/generated/joblib.dump.html) из модуля joblib;
5. **Импортируемый модуль** — название модуля Python, в котором находится импортируемый класс;
6. **Импортируемый класс** — название класса в импортируемом модуле Python;
7. **Только коэффициенты** — при значении **true** в выходном наборе данных будут выведены коэффициенты модели. Справедливо только для моделей, имеющих выходной метод `coef_`.;
8. **Выходное поле с разбиением** — имя поля, которое будет отвечать в выходном наборе данных за разбиение на обучающее и тестовое множества. Актуально, только если на вход компонента подан набор данных на порт **Тестовая выборка**;
9. **Имена выходов** — список имен выходных столбцов через запятую. Если выходов меньше, чем длина списка, берутся первые из списка. Если null, то метки формируются по умолчанию (COL1, COl2, ...);
10. **Дополнительные выходы** — список столбцов через запятую, которые будут добавлены в результирующий набор данных. Является уникальным для каждого класса и может быть взят в документации к соответствующей Python-библиотеке;
11. **fit_method** — метод, вызываемый при обучении модели. Для моделей машинного обучения это обычно **fit**;
12. **predict_method** —  метод, вызываемый при скоринге через модель. Для моделей машинного обучения это обычно **predict**;
13. **params** — список параметров в виде строки, которые нужно задать перед обучением модели. Данный список параметров является уникальным для каждой модели и описан в документации к соответствующей библиотеке Python;
14. **Принудительные параметры** — список параметров в виде строки, которые нужно задать перед обучением модели. Они будут применены после вызова метода `params`.

## Выходные порты

| Название              | Тип        |
|:----------------------|:-----------|
| Выходной набор данных | Таблица    |

### Структура таблицы "Выходной набор данных"

В выходной набор данных попадает набор данных, сформированный методом класса, указанным в переменной `fit_method`, а также дополнительные столбцы из списка **Дополнительные выходы**.
При наличии набора данных в порте **Тестовая выборка** в выходной набор добавляется столбец с именем, указанным в переменной **Выходное поле с разбиением**.
Если переменная **Только коэффициенты** = `true`, то в результирующий набор порадают коэффициенты модели (`coef_`) и константа (`intercept`)