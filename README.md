# Predicting Remaining Shelf Life of Export-Quality Mangoes (MLOps Pipeline)

An end-to-end MLOps application designed for an export mango packing facility near **Nuzvid, Andhra Pradesh**. The system estimates the remaining marketable shelf life (in days) of harvested mango shipments upon arrival at the packing house based on physiological maturity, thermal history, mechanical handling damage, and packaging type.

---

## System Architecture

```text
+-----------------------+      +---------------------------+      +-------------------------+
| Synthetic Data Gen    | ---> | Feature Engineering &     | ---> | Model Training          |
| (v1: 300, v2: 300)    |      | Parquet Feature Store     |      | (RF vs Gradient Boost)  |
+-----------------------+      +---------------------------+      +-------------------------+
                                                                               |
                                                                               v
+-----------------------+      +---------------------------+      +-------------------------+
| GitHub Actions CI/CD  | <--- | FastAPI Model Serving     | <--- | MLflow Model Registry   |
| (Pytest Validation)   |      | (POST /predict endpoint)  |      | (MangoShelfLifePredictor|
+-----------------------+      +---------------------------+      +-------------------------+
