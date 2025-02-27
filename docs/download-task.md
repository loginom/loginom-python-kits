# Скачать эксперимент

[Назад к списку компонентов](../README.md)

## Назначение

Компонент позволяет скачать последнюю версию эксперимента, а так же датасет (при необходимости)

## Входные порты

| Название                | Тип        |
|:------------------------|:-----------|
| Входные переменные      | Переменные |
| Environment Variables   | Переменные |

### Переменные в порте "Входные переменные"

| №  | Метка                       | Тип                                   | Значение по умолчанию  |
|:---|:----------------------------|:--------------------------------------|:-----------------------|
| 1  | Расположение                 | ![](./img/string.svg) Строковый      |/user/project |
| 2  | ID эксперимента              | ![](./img/string.svg) Строковый      |null          |
| 3  | ID датасета                  | ![](./img/string.svg) Строковый      |null          |
| 4  | Перезаписывать               | ![](./img/logical.svg) Логический    |true          |

1. **Расположение** — директория для скачивания эксперимента.
2. **ID эксперимента** — идентификатор скачиваемого эксперимента.
3. **ID датасета** — идентификатор скачиваемого датасета (можно оставить пустым).
4. **Перезаписывать** — перезаписывать уже скачанные файлы.

### Переменные в порте "Environment Variables"

| №  | Метка                       | Тип                                   | Значение по умолчанию  |
|:---|:----------------------------|:--------------------------------------|:-----------------------|
| 1  | CLEARML_WEB_HOST            | ![](./img/string.svg) Строковый       |null                    |
| 2  | CLEARML_API_HOST            | ![](./img/string.svg) Строковый       |null                    |
| 3  | CLEARML_FILES_HOST          | ![](./img/string.svg) Строковый       |null                    |
| 4  | Ключ доступа                | ![](./img/string.svg) Строковый       |null                    |
| 5  | Секретный ключ              | ![](./img/string.svg) Строковый       |null                    |

1. **CLEARML_WEB_HOST** — адрес веб-интерфейса ClearML. Указывает, по какому URL доступен веб-доступ к сервису ClearML. По умолчанию `null`;
2. **CLEARML_API_HOST** — адрес API ClearML. Указывает, по какому адресу доступен API для взаимодействия с ClearML. По умолчанию `null`;
3. **CLEARML_FILES_HOST** — адрес хранилища файлов ClearML. Указывает, где будут храниться загружаемые файлы и артефакты. По умолчанию `null`;
4. **Ключ доступа** — строка, которая служит идентификатором для аутентификации при взаимодействии с ClearML. Данный ключ должен быть получен через интерфейс ClearML и должен быть защищён. По умолчанию `null`;
5. **Секретный ключ** — секретный компонент аутентификационных данных для доступа к сервисам ClearML. Используется вместе с ключом доступа для безопасного взаимодействия с API. По умолчанию `null`.

## Выходные порты

| Название                   | Тип        |
|:---------------------------|:-----------|
| Выходной источник данных   | Таблица    |

### Структура таблицы "Выходной источник данных"

| Метка                | Тип                                        |
|:---------------------|:-------------------------------------------|
| Параметр             | ![](./img/string.svg) Строковый            |
| Значение             | ![](./img/string.svg) Строковый            |