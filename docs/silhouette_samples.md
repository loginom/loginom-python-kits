# silhouette_samples

[Назад к списку компонентов](../README.md)

## Назначение

текст

## Входные порты

| Название                | Тип        |
|:------------------------|:-----------|
| Входной набор данных    | Таблица    |
| Метки кластеров         | Таблица    |
| Входные переменные      | Переменные |

### Структура таблицы "Входной набор данных"

На вход подается набор данных со столбцами, которые принимали участие в кластеризации.

### Структура таблицы "Метки кластеров"

Метки кластеров, строковый тип.

### Переменные в порте "Входные переменные"

текст

1. **sample_size** —

## Выходные порты

| Название               | Тип        |
|:-----------------------|:-----------|
| Выходной набор данных  | Таблица    |

### Структура таблицы "Выходной набор данных"

| Метка         | Тип                                    | Описание                       |
|:--------------|:---------------------------------------|:-------------------------------|
| Метрика       | ![](./img/string.svg) Строковый        |                                |
| Значение      | ![](./img/realnumber.svg) Вещественный |Среднее значение индекса силуэта|