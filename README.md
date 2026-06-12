# ML-_PROJECT1
# MLOps Technical Assessment

## Overview

This project implements a minimal MLOps-style batch pipeline that:

- Loads configuration from YAML
- Reads OHLCV market data from CSV
- Computes rolling mean on `close`
- Generates binary trading signals
- Produces structured metrics JSON
- Generates detailed execution logs
- Runs locally and inside Docker

---

## Requirements

- Python 3.9+
- pandas
- numpy
- pyyaml

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Local Run

```bash
python run.py \
  --input data.csv \
  --config config.yaml \
  --output metrics.json \
  --log-file run.log
```

---

## Docker Build

```bash
docker build -t mlops-task .
```

---

## Docker Run

```bash
docker run --rm mlops-task
```

---

## Configuration

config.yaml

```yaml
seed: 42
window: 5
version: "v1"
```

---

## Output Example

metrics.json

```json
{
  "version": "v1",
  "rows_processed": 10000,
  "metric": "signal_rate",
  "value": 0.4990,
  "latency_ms": 127,
  "seed": 42,
  "status": "success"
}
```

---

## Error Example

```json
{
  "version": "v1",
  "status": "error",
  "error_message": "Missing required column: close"
}
```

---

## Logging

The pipeline records:

- Job start timestamp
- Config validation
- Dataset loading
- Rolling mean computation
- Signal generation
- Metrics summary
- Job completion status
- Errors and exceptions

---

## Project Features

### Reproducibility

- YAML configuration
- Deterministic seed handling
- Version tracking

### Observability

- Structured metrics
- Detailed logging
- Runtime measurement

### Deployment Readiness

- Dockerized execution
- No hardcoded paths
- Single command execution

---

## Author

Ravi Bhanu Durga Satya Gangadhar Mangarathi

NIT Patna
