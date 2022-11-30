# meta-silhouettes

[Назад к списку компонентов](../README.md)

## Назначение

Готовый компонент, который реализует кейс использования компонента **silhouette_score** — расчет общего индекса силуэта с указанием качества кластеризации.

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
| 1 | sample_size        | ![](./img/integer.svg) Целый      |       null |
| 2 | Нормализация данных| ![](./img/logical.svg) Логический |       true |

**Нормализация данных** — флаг, при котором значения будут приведены к единому виду. По умолчанию **true**.

## Выходные порты

| Название            | Тип        |
|:--------------------|:-----------|
| Индекс силуэта      | Переменные |

### Переменные в порте "Индекс силуэта"

* переменная **Индекс силуэта** — среднее значение индекса силуэта.
* переменная **Качество кластеризации** — текстовая интерпретация индекса силуэта (до 0,2 - `Низкое`, от 0,2 до 0,5 - `Среднее`, выше 0,5 - `Высокое`).

Если набор данных большой (несколько сотен тысяч записей), то рекомендуется предварительно сделать сэмплинг со стратификацией по полю **Кластер**. Иначе время расчета будет долгим - алгоритм предполагает вычисление расстояний между всеми объектами и кластерами.