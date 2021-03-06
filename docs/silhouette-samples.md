# silhouette_samples

[Назад к списку компонентов](../README.md)

## Назначение

Расчет индекса силуэта с использованием расстояния Евклида для каждого объекта выборки. Используется метод `silhouette_samples` из модуля **sklearn.metrics**

## Входные порты

| Название               | Тип        |
|:-----------------------|:-----------|
| Входной набор данных   | Таблица    |
| Метки кластеров        | Таблица    |

### Структура таблицы "Входной набор данных"

На вход подается набор данных со столбцами, которые принимали участие в кластеризации.

### Структура таблицы labels"

Единственное поле  — **labels**, строковый тип — метки кластеров.

## Выходные порты

| Название              | Тип        |
|:----------------------|:-----------|
| Индексы силуэтов      | Таблица    |

### Структура таблицы "Выходной набор данных"

К исходному входному набору данных добавляется два столбца. Сортировка по убыванию `silhouette_score`, `label` 

| Метка              | Тип                                      | Описание                  |
|:-------------------|:-----------------------------------------|:--------------------------|
| silhouette_score   | ![](./img/realnumber.svg) Вещественный   | Значение индекса силуэта  |
| label              | ![](./img/string.svg) Строковый          | Метка кластера            | 

Среднее значение индекса силуэта.