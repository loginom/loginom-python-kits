# Loginom Python Kits

* Версия: 2.0.1
* Проверено: Все редакции Loginom 6.5.4

Набор библиотек компонентов для работы с Python. Область применения библиотек:

* рутинные операции с наборами данных, расширяющие стандартный функционал Loginom;
* быстрый перенос существующего кода на Python (pandas, sklearn) в Loginom, используя no-code подход;
* разработка универсальных шаблонов сценариев Loginom, которые будут работать на любом наборе данных;
* внедрение в сценарий модели машинного обучения из библиотек на Python.

## Общие требования:

1. Установленный на сервере или локальной машине Python версии не ниже 3.9.
2. Указать в настройках Loginom путь к библиотеке **python3x.dll**.
3. Разрешить выполнение узлов Python.

Подробности можно найти в справочной системе Loginom.
Для работы с конкретной библиотекой **kit** требуется установить соответствующую библиотеку в Python. Эти требования приводятся в разделе, посвященной конкретной библиотеке.

## Список библиотек

1. `loginom_python_kit.lgp` — библиотека с общими компонентами, расширяющими стандартный функционал Loginom.

> **Требования:** установленная python-библиотека [Pandas](https://pandas.pydata.org/) версии не ниже 1.3.4.

2. `loginom_pandas_kit.lgp` — библиотека с рядом компонентов, вызывающих функции по манипуляции датасетами из Pandas.

> **Требования:** установленная python-библиотека [Pandas](https://pandas.pydata.org/) версии не ниже 1.3.4.

3. `loginom_sklearn_kit.lgp` — библиотека с компонентами для обучения и прогона алгоритмов и моделей, доступных в библиотеке [Scikit-learn](https://scikit-learn.org/).

> **Требования:** установленная python-библиотека  [Scikit-learn](https://scikit-learn.org/) версии 1.0 и выше.

4. `loginom_optbinning_kit.lgp` — библиотека с компонентами для оптимального квантования из библиотеки [OptBinning](https://gnpalencia.org/optbinning/).

> **Требования:** установленная Python-библиотека OptBinning версии 0.11.0 и выше.

>`Внимание!` Библиотека требует установки других python-библиотек определенных версий: numpy, ortools, pandas и другие, а также компонентов Microsoft Visual C++ 14.0. Подробности в документации к OptBinning [здесь](https://github.com/guillermo-navas-palencia/optbinning/blob/master/README.rst).

## Прочее

1. `loginom_sklearn_meta.lgp` — пакет с метакомпонентами библиотеки Sklearn Kit. Содержит готовые настроенные компоненты с параметрами для обучения ML-модели компонентом **model.fitter**, а также другие метакомпоненты.

> **Требования:** библиотека **Loginom Silver Kit** ([скачать на GitHub](https://github.com/loginom/loginom-silver-kit)). Версия не ниже 2.0.6.

## Cписок компонентов библиотеки **Loginom Python Kit**

### **utils**

* [Редкие значения](./docs/rare-values.md)
* [Редкие значения (прогон)](./docs/rare-new-values.md)

## Cписок компонентов библиотеки **Loginom Pandas Kit**

### **Data manipulations**

* [melt](./docs/melt.md)
* [pivot_table](./docs/pivot-table.md)
* [get_dummies](./docs/get-dummies.md)

## Cписок компонентов библиотеки **Loginom Sklearn Kit**

### **general**

* [simple.fitter](./docs/simple-fitter.md)
* [model.fitter](./docs/model-fitter.md)
* [model.scorer](./docs/model-scorer.md)

### **sklearn.metrics**

* [c.metrics](./docs/classification-metrics.md)
* [roc_auc_score](./docs/roc-auc-score.md)
* [average_precision_score](./docs/average-precision-score.md)
* [silhouette_score](./docs/silhouette-score.md)

## Cписок компонентов библиотеки **Loginom OptBinning Kit**

### **BinningProcess**

* [binning_process.fitter](./docs/binning-process-fitter.md)
* [binning_process.scorer](./docs/binning-process-scorer.md)

## Список производных компонентов пакета **Loginom Sklearn Meta**

* [cluster.KMeans](./docs/cluster-kmeans.md)
* [ensemble.GradientBoostingClassifier](./docs/ensemble-gradient-boosting-classifier.md)
* [ensemble.IsolationForest](./docs/ensemble-isolation-forest.md)
* [ensemble.RandomForestClassifier](./docs/ensemble-random-forest-classifier.md)
* [linear_model.LogisticRegression](./docs/linear-model-logistic-regression.md)
* [neighbors.KNeighborsClassifier](./docs/neighbors-kneighbors-classifier.md)
* [neighbors.LOF Novelty](./docs/neighbors-lof-novelty.md)
* [neighbors.LOF Outlier](./docs/neighbors-lof-outlier.md)
* [neighbors.LOF Scorer](./docs/neighbors-lof-scorer.md)
* [preprocessing.Scaler](./docs/preprocessing-scaler.md)
* [meta-scaling](./docs/metascaling.md)
* [meta-silhouettes](./docs/meta-silhouettes.md)
* [meta-silhouettes-score](./docs/meta-silhouettes-score.md)
* [template.fitter](./docs/template-fitter.md)
* [template.scorer](./docs/template-scorer.md)

![Схема расположения библиотеки в рабочем каталоге](docs/img/python-kits.svg)
