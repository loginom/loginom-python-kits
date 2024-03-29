# regression metrics

[Назад к списку компонентов](../README.md)

## Назначение

Компонент использует модуль [sklearm.metrics](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.metrics) и рассчитыват показатели: r2_score, explained_variance, max_error, mean_absolute_error, mean_squared_error, median_absolute_error,
mean_absolute_percentage_error, d2_absolute_error_score.

## Входные порты

| Название                | Тип        |
|:------------------------|:-----------|
| y_true, y_scores        | Таблица    |
| Входные переменные      | Переменные |

### Структура таблицы "Обучающая выборка"

| Метка  | Тип                                    | Описание          |
|:-------|:---------------------------------------|:------------------|
| y_true | ![](./img/realnumber.svg) Вещественный |                   |
| y_pred | ![](./img/realnumber.svg) Вещественный |                   |

### Переменные в порте "Входные переменные"

| №  | Метка          | Тип                                | Значение по умолчанию  |
|:---|:---------------|:-----------------------------------|:-----------------------|
| 1  | force_finite   | ![](./img/logical.svg) Логический  | true                   |

1. **force_finite** — параметр из функции `sklearn.metrics.r2_score`

## Выходные порты

| Название              | Тип        |
|:----------------------|:-----------|
| Выходной набор данных | Таблица    |

### Структура таблицы "Выходной набор данных"

| Метка             | Тип                                    | Описание          |
|:------------------|:---------------------------------------|:------------------|
| Метрика           | ![](./img/string.svg) Строковый        |                   |
| Значение          | ![](./img/realnumber.svg) Вещественный |                   |