# Новый проект

[Назад к списку компонентов](../README.md)

## Назначение

Компонент для создания папки проекта с шаблонами сценариев под конкретную задачу (ML или ETL).

### ML-проект

Папка проекта включает:

1. Подпапки: 

   * **raw-data** — папка для исходных данных (используется для первичной загрузки датасетов в проект ClearML);
   * **samples** — папка с предобработанными датасетами (выборками) (используется для загрузки дочерних датасетов в проект ClearML)

2. Пакеты:

   * **data-prep.lgp** — пакет для подключения к проекту, предобработки и загрузки датасетов (из папок **raw-data** и **samples**). На этом же этапе в датасет проекта может быть загружен пакет **data-prep.lgp**;
   * **ml-experiment.lgp** — пакет с готовым сценарием для проведения ML-эксперимента и загрузки результатов. На этом же этапе в артефакты эксперимента может быть загружен пакет **ml-experiment.lgp**.

### ETL-проект

Папка проекта включает:

1. Подпапки: 

   * **raw-data** — папка для исходных данных (используется для первичной загрузки датасетов в проект ClearML);
   * **etl-data** — папка с данными после проведения ETL-процедур (используется для загрузки дочерних датасетов в проект ClearML)

2. Пакеты:

   * **data-load.lgp** — пакет для подключения к проекту, предобработки и загрузки датасетов (из папки **raw-data**). На этом же этапе в датасет проекта может быть загружен пакет **data-load.lgp**;
   * **etl-experiment.lgp** — пакет с готовым сценарием для проведения ETL-эксперимента и загрузки результатов. На этом же этапе в артефакты эксперимента может быть загружен пакет **ml-experiment.lgp**. Также можно сохранить обработанные данные в папку **etl-data** и загрузить их в качестве дочернего датасета в проект ClearML.

## Входные порты

| Название   | Тип        |
|:-----------|:-----------|
| Переменные | Переменные |

### Переменные в порте "Переменные"

| №  | Метка                  | Тип                                   | Значение по умолчанию  |
|:---|:-----------------------|:--------------------------------------|:-----------------------|
| 1  | Расположение           | ![](./img/string.svg) Строковый       |null                    |
| 2  | Проект                 | ![](./img/string.svg) Строковый       |Новый проект            |
| 3  | Тип проекта            | ![](./img/string.svg) Строковый       |ml                      |
| 4  | Имя папки с данными    | ![](./img/string.svg) Строковый       |raw-data                |

1. **Расположение** — директория, где будет создана папка. Если `null`, то создается в папке пользовательского хранилища Loginom;
2. **Проект** — название папки;
3. **Тип проекта**:
     * если ml — то будут размещены файлы для проектов, связанных с машинным обучением;
     * если etl — то будут размещены файлы для проектов, связанных с преобразованием данных.
4. **Имя папки с данными** — название подпапки, в которой будут хранится данные для первичной загрузки в качестве датасета. По умолчанию `raw-data`.



## Выходные порты

| Название             | Тип        |
|:---------------------|:-----------|
| Сообщения и ошибки   | Таблица    |

### Структура таблицы "Сообщения и ошибки"

| Метка                | Тип                                        |
|:---------------------|:-------------------------------------------|
| Параметр             | ![](./img/string.svg) Строковый            |
| Значение             | ![](./img/string.svg) Строковый            |