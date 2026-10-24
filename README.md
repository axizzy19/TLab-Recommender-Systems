# Recommender Systems: Feature Engineering

Исследование автоматизации построения признаков для рекомендательной системы на датасете KION.

## Цель

Сравнить CatBoost с ручными признаками и CatBoost с объединtнным набором ручных и автоматически сгенерированных признаков. Дополнительно используется baseline, основанный на популярности объектов.

## Эксперименты

- **Baseline:** CatBoost с 25 признаками и модель популярности.
- **Automated Feature Engineering:** генерация 31 дополнительного признака на основе истории взаимодействий пользователей с фильмами.
- **Evaluation:** сравнение ROC-AUC, Average Precision, NDCG@10, Recall@10 и Precision@10.

## Результаты

| Модель | NDCG@10 | Recall@10 | Precision@10 | Average Precision |
|---|---:|---:|---:|---:|
| Popularity | 0.67420 | 0.78523 | 0.17819 | — |
| CatBoost Manual | 0.70153 | 0.80516 | 0.18451 | 0.52102 |
| CatBoost Manual + Auto | 0.69945 | 0.80231 | 0.18370 | 0.52483 |

Автоматическая генерация признаков увеличила Average Precision, но не улучшила NDCG@10 и Recall@10 на тестовой выборке.

## Данные

Используется датасет KION:
https://github.com/irsafilo/KION_DATASET

Данные необходимо скачать отдельно и разместить в каталоге `data_original/`.

## Установка

```bash
git clone https://github.com/axizzy19/TLab-Recommender-Systems.git
cd TLab-Recommender-Systems

python -m venv venv_tlab-1
```

Активация окружения:

```bash
venv_tlab-1\Scripts\activate
```

Установка зависимостей:

```bash
python -m pip install --upgrade pip
python -m pip install jupyterlab notebook pandas numpy matplotlib seaborn scikit-learn catboost pyarrow tqdm
```

Запуск Jupyter:

```bash
jupyter notebook
```
