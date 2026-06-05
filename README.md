# ПРОДЕТИ_РИСК — PoC прогноза ПОД (2–12 лет)

Proof-of-concept прогностической модели **послеоперационного делирия (ПОД)** у детей на обезличенной выборке исследования «ПРОДЕТИ_РИСК».

## Структура

| Путь | Описание |
|------|----------|
| `PRODETI_RISK_2-12_for_IT.csv` | Исходная выборка (экспорт из `данные.numbers`) |
| `PRODETI_RISK_2-12_filtered.csv` | Отфильтрованная когорта (возраст 2–12, без дубликатов) |
| `pod_delirium_poc.ipynb` | Jupyter notebook: обучение, ROC, feature importance |
| `reports/` | ROC-кривые, feature importance, `model_metrics.json` |
| `summary.md` | Сравнение ML-результатов с клиническим исследованием |

## Данные

**Данные доступны по запросу у авторов.** В репозитории — только структура CSV и синтетически совместимый формат.

| Колонка | Описание |
|---------|----------|
| `age_years` | Возраст, лет (2–12) |
| `sex_clean` | Пол: 0 = девочка, 1 = мальчик |
| `mypas_pct` | m-YPAS, % |
| `induction_behavior` | Поведение при индукции (1–4) |
| `duration_min` | Длительность анестезии, мин |
| `surgery_type_clean_code` | Тип операции (1,2,3,4,5,7) |
| `planned_duration_cat` | План. длительность (1–3) |
| `asa_class` | ASA (1–3) |
| `opioid_used` | Опиоиды: 0/1 |
| `outcome_ed_calc` | **Целевая:** 0 = нет ПОД, 1 = ПОД |

## Быстрый старт

```bash
cd susana_release
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt

# На macOS для XGBoost:
# brew install libomp

python scripts/train_and_report.py   # метрики + графики
jupyter notebook pod_delirium_poc.ipynb
```

## Лицензия

MIT — см. `LICENSE`.

## Ссылки

- Сводка и сравнение с публикацией: [`summary.md`](summary.md)
- Исходный PoC (расширенная модель, 24 признака): `../susana/`
