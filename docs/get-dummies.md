# get_dummies

[Назад к списку компонентов](../README.md)

## Назначение

Компонент использует функцию [pandas.get_dummies](https://pandas.pydata.org/docs/reference/api/pandas.get_dummies.html) для преобразования входных данных.

## Входные порты

| Название                | Тип        |
|:------------------------|:-----------|
| Входной источник данных | Таблица    |
| Входные переменные      | Переменные |

### Структура таблицы "Входной источник данных"

На вход можно подать данные любой структуры.

### Переменные в порте "Входные переменные"

| №  | Метка       | Тип                                   | Значение по умолчанию  |
|:---|:------------|:--------------------------------------|:----------|
| 1  | prefix      | ![](./img/string.svg) Строковый       | color,size|
| 2  | prefix_sep  | ![](./img/string.svg) Строковый       | _         |
| 3  | dummy_na    | ![](./img/logical.svg) Логический     | false     |
| 4  | columns     | ![](./img/string.svg) Строковый       | C_1,C_2   |
| 5  | drop_first  | ![](./img/logical.svg) Логический     | false     |

Подробнее о переменных **prefix**, **prefix_sep**, **dummy_na**, **columns**, **drop_first** в документации по [pandas.get_dummies](https://pandas.pydata.org/docs/reference/api/pandas.get_dummies.html).

## Выходные порты

| Название              | Тип        |
|:----------------------|:-----------|
| Выходной набор данных | Таблица    |

### Структура таблицы "Выходной набор данных"

Структура таблицы соответствует входному набору после преобразования функцией [pandas.get_dummies](https://pandas.pydata.org/docs/reference/api/pandas.get_dummies.html).