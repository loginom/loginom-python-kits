# clustering metrics

[Назад к списку компонентов](../README.md)

## Назначение

текст

## Входные порты

| Название                | Тип        |
|:------------------------|:-----------|
| Обучающая выборка       | Таблица    |
| Входные переменные      | Переменные |

### Структура таблицы "Обучающая выборка"

| Метка             | Тип                          | Описание          |
|:------------------|:-----------------------------|:------------------|
| labels_true       | ![](./img/integer.svg) Целый |                   |
| labels_pred       | ![](./img/integer.svg) Целый |                   |

### Переменные в порте "Входные переменные"

текст

## Выходные порты

| Название              | Тип        |
|:----------------------|:-----------|
| Выходной набор данных | Таблица    |

### Структура таблицы "Выходной набор данных"

| Метка             | Тип                                    | Описание          |
|:------------------|:---------------------------------------|:------------------|
| Метрика           | ![](./img/string.svg) Строковый        |                   |
| Значение          | ![](./img/realnumber.svg) Вещественный |                   |