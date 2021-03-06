# binning_process.fitter

[Назад к списку компонентов](../README.md)

## Назначение

Компонент обучает модель, которая делает оптимальное квантование для всех полей во входном датасете (порт **Обучающая выборка**), за исключением поля с идентификатором (вызывается метод `binning_process.fit`). Компонент также осуществляет "прогон" набора данных (порт **Скоринговая выборка**) через готовую модель (вызывается метод `binning_process.transform`).

Выходная переменная — бинарная.

Ссылка на описание класса `BinningProcess` из библиотеки **OptBinning** [здесь](https://gnpalencia.org/optbinning/binning_process.html).

## Входные порты

| Название                | Тип        |
|:------------------------|:-----------|
| Обучающая выборка       | Таблица    |
| Скоринговая выборка     | Таблица    |
| Входные переменные      | Переменные |

### Структура таблицы "Обучающая выборка"

На вход можно подать данные любой структуры, но обязательно требуется поле с событием.

### Структура таблицы "Скоринговая выборка"

Структура набора данных должна быть идентична структуре, подаваемой на порт **Обучающая выборка**.

### Переменные в порте "Входные переменные"

| №  | Метка                    | Тип                                | Значение по умолчанию   |
|:---|:-------------------------|:-----------------------------------|:------------------------|
| 1  | Поле с идентификатором   | ![](./img/string.svg) Строковый    | null                    |
| 2  | Поле с событием          | ![](./img/string.svg) Строковый    | target                  |
| 3  | Путь к файлу             | ![](./img/string.svg) Строковый    | null                    |
| 4  | Имя файла для модели     | ![](./img/string.svg) Строковый    | null                    |
| 5  | Вывести итоги            | ![](./img/logical.svg) Логический  | false                   |
| 6  | Метка события            | ![](./img/string.svg) Строковый    | 1                       |
| 7  | Дополнительные параметры | ![](./img/string.svg) Строковый    | null                    |
| 8  | binning_fit_params       | ![](./img/string.svg) Строковый    | null                    |
| 9  | categorical_variables    | ![](./img/string.svg) Строковый    | null                    |
| 10 | selection_criteria       | ![](./img/string.svg) Строковый    | { 'iv': {'min': 0.02}}  |
| 11 | max_n_bins               | ![](./img/integer.svg) Целый       | 6                       |
| 12 | transform_metric         | ![](./img/string.svg) Строковый    | woe                     |

1. **Поле с идентификатором** — необязательный столбец, в котором содержится информация об идентификаторе объекта;
2. **Поле с событием** — обязательный столбец, в котором содержится информация о событиях. Может быть любого типа. Событию соответствует значение, указанное в переменной **Метка события**;
3. **Путь к файлу** — полный путь к файлу, где лежит файл с именем `model_filename`;
4. **Имя файла для модели** — модель должна быть представлена в виде сериализованного объекта Python путем вызова метода [dump](https://joblib.readthedocs.io/en/latest/generated/joblib.dump.html) из модуля joblib;
5. **Вывести итоги** — при значении **true** в выходном наборе данных будут выведены WoE-индексы через вызов метода `binning_process.summary()`;
6. **Метка события** — значение, которое принимает событие (поле **target**), все остальные значения будут записаны в не-события;
7. **Дополнительные параметры** — дополнительные параметры, которые передаются в класс **BinningProcess** после вызова метода `set_params`.
8. **binning_fit_params** — вызывается метод **Binning_process.Set_params** и строка, содержащая параметры, передается в аргументы метода. В эту строку не следует записывать значения variable_names, а также: `categorical_variables`, `selection_criteria`, `max_n_bins`. Последние три задаются отдельными параметрами;
9. **categorical_variables** — список имен столбцов через занятую, которые требуется обрабатывать как дискретные (категориальные);
10. **selection_criteria** — критерий отбора переменных в выходной набор данных. По умолчанию это условие отбора с IV > 0.02;
11. **max_n_bins** — максимальное число бинов;
12. **transform_metric** — метод для представления выходного значения в бине после оптимального квантования. Допустимые значения: `woe` (по умолчанию), `event_rate`, `indices`, `bins`.

## Выходные порты

| Название              | Тип        |
|:----------------------|:-----------|
| Выходной набор данных | Таблица    |

### Структура таблицы "Выходной набор данных"

В выходной набор данных попадают все столбцы исходного датасета, которые удовлетворяют критерию отбора в процедуре оптимального квантования. Если порт **Скоринговая выборка** был непустой, то он объединяется с обучающей выборкой и создается столбец с именем и меткой **test_set** для разделения этих двух наборов данных.