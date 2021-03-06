# Лабораторная работа №2.
В данной лабораторной работе нужно будет научиться предсказывать вероятность того, что заёмщику выдадут кредит. Метрика качества — `ROC-AUC`. От итогового результата будет зависеть ваша оценка.

Данные представляют собой часть информации о кредитах для нескольких штатов за 2017 год: https://cfpb.github.io/api/hmda/index.html. Там же можно найти описание столбцов.  

У вас будет только <b>ОДНА</b> попытка для отправки предсказаний (файл отправляется вместе с отчетом преподавателю).

Установите библиотеку `LightGBM` (в Anaconda Prompt выполнить `conda install -c conda-forge lightgbm`). Также по желанию установите `XGBoost`, однако имейте ввиду, что его нет в каналах anaconda/conda-forge.

1. Скачайте данные https://drive.google.com/file/d/1U8T58RFC1HneemrvqvwyxuZqzsByHLok/view?usp=sharing в папку `Data/`.
2. Запустите базовое решение http://nbviewer.jupyter.org/github/uladzislau-varabei/machine-learning-course-bsu-mmf-2018-autumn/blob/master/LB_02/Baseline.ipynb.
3. Проведите разведочный анализ данных. 
Посмотрите на наиболее популярные значения признаков. В каких столбцах есть пропуски и насколько их много? Постройте гистограммы числовых признаков для тестовой и тренировочной выборки.
4. Выделите столбец `action_taken_name` из тренировочных данных в отдельную переменную и замените ее значения, используя `target_dict_encoder` из `Baseline.ipynb` — новые значения будем считать целевой переменной, которую необходимо научиться предсказывать.
5. Подумайте, какие колонки целесообразно удалить из данных. Удалите из данных столбцы, которые вы посчитали неинформативными.
6. Заполните пропуски в данных.
7. Создайте новые признаки на основе категориальных признаков при помощи onehot-кодирования и добавьте их к исходному dataframe-у. Учтите, что некоторые значения признаков встречаются довольно редко и для них не нужно строить отдельный столбец. Удалите из данных использованные столбцы с категориальными переменными.
Обратите внимание, что в тестовых данных могут встретиться значения признаков, которых нет в тренировочных данных.
8. Нормализуйте признаки при помощи `StandardScaler`.
9. Обучите данные классификаторы с различными наборами параметров:
    * `LogisticRegression`
    * `SGDClassifier`
    * `DecisionTreeClassifier`
    * `RandomForestClassifier`
    * `XGBClassifier/LGBMClassifier`
10. На результат каких алгоритмов влияет нормализация данных?
11. Для древесных алгоритмов постройте график `feature_importances_` с указанием названия признаков.
12. Сравните алгоритмы при помощи кросс-валидации (например, при помощи `cross_val_score`).
13. Попробуйте улучшить качество предсказаний. Возможные варианты:
    * Создание новых признаков
    * Оптимизация гиперпараметров моделей 
    * Объединение результатов нескольких моделей
14. Сохраните ваши предсказания в файл `submission_ФамилияИмя.csv` и вместе с отчетом отправьте преподавателю на почту. 

Ваша оценка зависит как от предоставленного отчета, так и от результата на тестовых данных.
**Срок сдачи лабораторной: 5 октября 2018.**
