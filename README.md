# gamanapriya
Churn Prediction ML Pipeline (FastAPI + Airflow + scikit-learn)
# Churn Prediction ML Pipeline

Production-ready starter for a **customer churn prediction** project using a clean MLOps layout: ETL → feature engineering → training → evaluation → REST inference.  
Stack: **Python, scikit-learn, Pandas, FastAPI, Airflow, Docker, PyTest**.

## Why this repo?
- Mirrors real-world work: data ingestion, model training, versioned artifacts, unit tests, and a tiny REST API.
- Includes a lightweight **Airflow DAG** to orchestrate daily ETL + training.
- Ships with **synthetic data** so you can run end to end locally.

## Quickstart
```bash
# 1) Create venv & install
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt

# 2) Run unit tests
pytest -q

# 3) Train a model on sample data
python src/train.py --config configs/config.yaml

# 4) Serve the model locally
uvicorn app.main:app --reload
# -> open http://127.0.0.1:8000/docs
```

## Airflow (optional)
This repo includes a simple DAG (`dags/churn_daily.py`) using PythonOperators for: `extract` → `transform` → `train`.  
To try locally, point `AIRFLOW_HOME` to this repo and drop the DAG into your Airflow dags dir.

## Project Structure
```
churn-prediction-ml-pipeline/
├─ app/
│  └─ main.py              # FastAPI service exposing /predict
├─ configs/
│  └─ config.yaml          # Paths, model params, split sizes
├─ data/
│  └─ raw/customer_events.csv
├─ dags/
│  └─ churn_daily.py       # Airflow DAG with extract→transform→train
├─ src/
│  ├─ data.py              # Load & split data
│  ├─ features.py          # Feature engineering pipeline
│  ├─ model.py             # Model creation & persistence
│  └─ train.py             # Train/evaluate entrypoint
├─ tests/
│  ├─ test_features.py
│  └─ test_model.py
├─ .gitignore
├─ Dockerfile
├─ Makefile
└─ requirements.txt
```

## Notes
- Minimal by design; swap the classifier or add monitoring as needed.
- Built to showcase skills in **Python, ML, orchestration, and APIs**.

---

