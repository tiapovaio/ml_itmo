# Supervised Learning: предсказание скачиваний по просмотрам

В этом проекте решается задача регрессии — предсказание количества скачиваний по числу просмотров и другим характеристикам. Используется собственноручно собранный датасет (data.csv + data2.csv), с дальнейшей обработкой, визуализацией и построением моделей.

---

## Этапы работы

### 1. Подготовка данных

- Загружены и объединены два датасета: `data.csv` и `data2.csv` ([ранее собраны тут](../web-crawling-ml-dataset))
- Обработка пропущенных значений: поле `medal` заменено на `'0'`
- Категориальный признак `medal` преобразован в числовой с помощью `LabelEncoder`
- Добавлены лог-преобразования для `views` и `downloads`
- Проведена визуализация: распределения, корреляционная матрица, диаграммы рассеяния

---

### 2. Визуализация

- Корреляционная матрица между основными признаками
- Гистограммы до и после лог-преобразования (`log1p`)
- График зависимости `views → downloads`

---

### ⚙3. Baseline-модель

- Использована простая **линейная регрессия (`LinearRegression`)** на одном признаке `normalized_views`
- Вычислены метрики:
  - **Mean Squared Error (MSE)**
  - **R² Score**

---

### 4. Модель с подбором гиперпараметров

- Использована **Ridge-регрессия** (`sklearn.linear_model.Ridge`)
- Подбор `alpha` через `GridSearchCV`
- Улучшение качества по сравнению с baseline

---

### 5. Реализация своей модели с нуля

- Написан класс `MyLinearRegression`, реализующий:
  - Метод `fit` (через нормальное уравнение)
  - Метод `predict`
  - Метод `evaluate` (MSE и R²)

---

### 6. Обучение с SGD и визуализация по эпохам

- Реализован **градиентный спуск с обучением по эпохам**
- Добавлена стандартизация (`StandardScaler`)
- Для каждой эпохи сохранены:
  - **MSE (train/test)**
  - **R² (train/test)**
- Построены графики зависимости метрик от числа эпох
