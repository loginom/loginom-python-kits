# meta-scaling

[Назад к списку компонентов](../README.md)

## Назначение

Готовый составной компонент, который реализует популярный кейс использования компонента **preprocessing.Scaler** - стандартизация набора данных на обучающей выборке и применение стандартизации к тестовой выборке.

## Входные порты

| Название                | Тип        |
|:------------------------|:-----------|
| Обучающая выборка       | Таблица    |
| Тестовая выборка        | Таблица    |
| Переменные              | Переменные |

### Структура таблицы "Обучающая выборка"

На вход можно подать данные любой структуры.

### Структура таблицы "Тестовая выборка"

На вход можно подать данные любой структуры, но структура должна быть идентичной обучающей выборке.

### Переменные в порте "Переменные"

| №  | Метка                  | Тип                                     | Значение по умолчанию  |
|:---|:-----------------------|:----------------------------------------|:-----------------------|
| 1  | Импортируемый класс    | ![](./img/string.svg) Строковый         | StandartScaler         |
| 2  | id_fieldname           | ![](./img/string.svg) Строковый         | ID                     |
| 3  | ignore_fields          | ![](./img/string.svg) Строковый         | null                   |
| 4  | params                 | ![](./img/string.svg) Строковый         | null                   |

1. **Импортируемый класс** — название класса в импортируемом модуле Python;
2. **id_fieldname** — имя столбца, в котором содержится информация об идентификаторе объекта (если такой столбец есть в наборе данных);
3. **ignore_fields** — cписок полей (если несколько, то перечисляются через запятую), которые не будут использоваться при обучении модели. В выходной набор данных они не попадут;
4. **params** — список параметров в виде строки, которые нужно задать перед обучением (формированием) модели. Данный список параметров является уникальным для каждой модели и описан в документации к соответствующей библиотеке Python.

## Выходные порты

| Название              | Тип        |
|:----------------------|:-----------|
| Обучающая выборка     | Таблица    |
| Тестовая выборка      | Таблица    |

### Структура таблицы "Обучающая выборка"

Выходной набор данных содержит те же столбцы, что и во входном наборе данных порта **Обучающая выборка**.

### Структура таблицы "Тестовая выборка"

Выходной набор данных содержит те же столбцы, что и во входном наборе данных порта **Тестовая выборка**.