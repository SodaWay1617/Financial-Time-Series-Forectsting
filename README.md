# Прогнозирование финансовых временных рядов

Курсовой проект по прогнозированию финансовых временных рядов на основе классических ML/TS методов, глубокого обучения и LLM-подходов, включая анализ новостей и обнаружение аномалий. В составе — набор Jupyter-ноутбуков, данных и удобная среда запуска через Docker.

### Основные возможности
- Обработка и подготовка данных временных рядов
- Интеграция новостного фона в признаки
- Обнаружение аномалий в рядах
- Многомерные и одномерные прогнозы: VAR, Darts, tsai, Chronos, FEDOT, LLM-основанные подходы
- Сравнение моделей и визуализация результатов

## Структура проекта
- `notebooks/` — основные ноутбуки и вспомогательные подпапки
  - `data/` — подготовленные наборы данных
    - `series/` — базовые ценовые ряды (`*.csv`)
    - `multivariate_series/` — мультивариативные ряды с дополнительными признаками
    - `news/` — обработанные новости по тикерам
  - `predictors/` — ноутбуки и результаты по моделям
    - `multivariate/` — многомерные предсказатели, результаты и визуализации
    - `univariate/` — одномерные предсказатели
  - `anomaly_detectors/` — ноутбуки по поиску аномалий
  - `data_processing/` — загрузка и фичеринг
  - `news_processors/` — интеграция новостей в ряды
- `Dockerfile`, `docker-compose.yml` — окружение для JupyterLab
- `env-example` — пример `.env` файла

## Быстрый старт (Docker)
Требования: установлен Docker и Docker Compose.

1) Скопируйте пример окружения:
```bash
cp env-example .env
```
2) Запустите сервис JupyterLab:
```bash
docker compose up --build
```
3) Откройте JupyterLab в браузере: `http://localhost:8888`

Тома смонтированы так, что каталог `notebooks/` доступен внутри контейнера по пути `/workspace`.

### Переменные окружения
Файл `.env` (см. `env-example`):
- `T_TOKEN` — при необходимости, токен/ключ для доступа к API данных или новостей.

## Использование ноутбуков
- Обработка данных: `notebooks/data_processing/feature_engineering.ipynb`, `notebooks/data_processing/time_series_downloader.ipynb`
- Интеграция новостей: `notebooks/news_integration.ipynb`, `notebooks/news_processors/news_integration.ipynb`
- Аномалии: `notebooks/anomaly_detectors/Anomaly Detection.ipynb`, `Ruptures_Anomaly_Detection.ipynb`
- Прогнозирование (многомерное): `notebooks/predictors/multivariate/ML_*_Multivariate.ipynb`, LLM-протоколы (`LLM_progressive*.ipynb`)
- Прогнозирование (одномерное): `notebooks/predictors/univariate/*`

## Данные и результаты
- Входные данные: `notebooks/data/series/*.csv`, `notebooks/data/multivariate_series/*.csv`, `notebooks/data/news/*`
- Ключевые результаты и визуализации: `notebooks/predictors/multivariate/results/*`
- Прогрессивный анализ признаков: `notebooks/predictors/multivariate/progressive_analysis/*`

## Локальный запуск без Docker (опционально)
Минимальная среда из `Dockerfile` включает: `python==3.10`, `jupyterlab`, `ipykernel`, `pandas`, `numpy`, `matplotlib`.
Вы можете создать своё окружение и установить зависимости вручную.

Пример для Windows PowerShell (внутри корня проекта):
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install jupyterlab ipykernel pandas numpy matplotlib
jupyter lab
```

## Воспроизводимость
- Зафиксируйте версии своих библиотек при локальном запуске (например, через `pip freeze > requirements.txt`).
- Для повторяемости используйте контейнер из раздела «Быстрый старт (Docker)».

## Лицензия и материалы
- Учебный проект для курсовой работы. Материалы презентации/отчёта: `sobolev_da_financial_time_series_forecsting.pdf`, `Соболев_Прогнозирование_финансовых_временных_рядов.pdf`.
