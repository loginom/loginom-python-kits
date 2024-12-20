# meta-silhouettes

[Назад к списку компонентов](../README.md)

## Назначение

Готовый компонент, который реализует кейс использования компонента **silhouette-samples** — расчет индексов силуэтов для построения графика (с настроенным визулизатором - диаграммой) и общий индекс силуэта с указанием качества кластеризации.

## Входные порты

| Название                | Тип        |
|:------------------------|:-----------|
| Входной набор данных    | Таблица    |
| Метки кластеров         | Таблица    |
| Переменные              | Переменные |

### Структура таблицы "Входной набор данных"

На вход подается набор данных со столбцами, которые принимали участие в кластеризации.

### Структура таблицы "Метки кластеров"

Единственное поле  — **labels**, строковый тип — метки кластеров.

### Переменные в порте "Переменные"

| № | Метка              | Тип                               | Значение   |
|:--|:-------------------|:----------------------------------|:-----------|
| 1 | Стандартизация данных| ![](./img/logical.svg) Логический |       true |

**Стандартизация данных** — флаг, при котором значения будут приведены к единому масштабу (методом `StandardScaler()`). По умолчанию **true**.

## Выходные порты

| Название            | Тип        |
|:--------------------|:-----------|
| Индексы силуэтов    | Таблица    |
| Индекс силуэта      | Переменные |

### Структура таблицы "Индексы силуэтов"

К исходному входному набору данных добавляется два столбца. Сортировка по убыванию `silhouette_score`, `label` 

| Метка            | Тип                                    | Описание                  |
|:-----------------|:---------------------------------------|:--------------------------|
| Номер строки     | ![](./img/number.svg) Целый            | Порядковый номер строки   |
| Индекс силуэта   | ![](./img/realnumbeg.svg) Вещественный | Значение индекса силуэта  |
| Кластер          | ![](./img/string.svg) Строковый        | Метка кластера            |

### Переменные в порте "Индекс силуэта"

* переменная **Индекс силуэта** — среднее значение индекса силуэта.
* переменная **Качество кластеризации** — текстовая интерпретация индекса силуэта (до 0,2 - `Низкое`, от 0,2 до 0,5 - `Среднее`, выше 0,5 - `Высокое`).

