# 🚀 MLflow Quick Start Guide

This guide will help you get started with **MLflow** for tracking experiments locally and with external integrations like DagsHub.

---

## ⚠️ Caution

- MLflow may face some compatibility issues with **Python 3.12**.
- ✅ Recommended: Use a **virtual environment** with an earlier version of Python (e.g., 3.10 or 3.11) for a smoother setup.

---

## 🔧 Local Setup

### 1. Install MLflow

```bash
pip install mlflow
```

### 2. Import & Configure MLflow

Inside your project file or Jupyter notebook:

```python
import mlflow

# Set MLflow tracking URI
mlflow.set_tracking_uri("http://127.0.0.1:5000")
```

### 3. Run MLflow Server

Start the MLflow UI server from the terminal:

```bash
mlflow ui
```

By default, this runs at **[http://127.0.0.1:5000](http://127.0.0.1:5000)**.
To change the port:

```bash
mlflow ui --port 5500
```

Now, open the MLflow UI in your browser:

- Default: [http://127.0.0.1:5000](http://127.0.0.1:5000)
- Custom: `http://127.0.0.1:<your_port>`

### 4. Create & Track an Experiment

Inside your project file or notebook:

```python
# Set experiment name
mlflow.set_experiment("my_experiment")

# Start a run and log parameters/metrics
with mlflow.start_run():
    mlflow.log_param("test", 1)
    mlflow.log_metric("accuracy", 0.98)

    # Example: log artifacts (files, images, models, etc.)
    mlflow.log_artifact("path/to/artifact")
```

✅ Results will appear in the MLflow UI at [http://127.0.0.1:5000](http://127.0.0.1:5000).

---

## 🤖 Auto Logging

MLflow supports **automatic tracking** for popular ML and AI libraries.

### For ML frameworks

```python
mlflow.autolog()
```

### For LLM & AI frameworks

```python
mlflow.openai.autolog()       # OpenAI
mlflow.langchain.autolog()    # LangChain
mlflow.llama_index.autolog()  # LlamaIndex
```

---

## 🌐 Setup with DagsHub

You can integrate MLflow with **DagsHub** to track experiments remotely.

1. Go to [DagsHub](https://dagshub.com/) and create a repository.
2. Find your repository’s MLflow tracking URI, which looks like:

   ```
   https://dagshub.com/<username>/<repo>.mlflow
   ```

3. Configure MLflow in your project:

   ```python
   import mlflow

   mlflow.set_tracking_uri("https://dagshub.com/<username>/<repo>.mlflow")
   mlflow.set_experiment("my_experiment")
   ```

4. Set up authentication (using a token from DagsHub):

   ```bash
   export MLFLOW_TRACKING_USERNAME=<username>
   export MLFLOW_TRACKING_PASSWORD=<your_token>
   ```

Now, all your logged runs will be tracked on **DagsHub UI**.

---

## 📚 Useful References

- [MLflow Connection Docs](https://mlflow.org/docs/latest/genai/getting-started/connect-environment/)
- [MLflow GenAI Docs](https://mlflow.org/docs/latest/genai/getting-started/)

---

## 🎁 Extras Provided

1. MLflow setup with **DagsHub** (see above)
2. Example/demo **notebook** to get started

---

✅ You’re all set to start tracking your ML experiments with **MLflow**! 🚀
