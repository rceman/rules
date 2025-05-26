# 🧠 Local LLM Rules

## 1. Model Choice

| Use‑case         | Recommended model          | Size (Q4_K_M) |
|------------------|----------------------------|---------------|
| General planning | **Qwen3‑1.7B**             | 2 GB          |
| Code generation  | **Qwen3‑8B**               | 9 GB          |

Quantisation: prefer **Q4_K_M** or **Q6_K** for balance of speed & quality.

## 2. Storage

Store weights under `models/` (git‑ignored).  
Provide SHA‑256 checksums in `scripts/download_models.sh`.

## 3. Loading

```python
from llama_cpp import Llama

llm = Llama(
    model_path="models/qwen3-8b-q4_k_m.gguf",
    n_gpu_layers=-1,           # full‑GPU
    context_length=32768
)
```

## 4. Prompt Engineering

* Keep templates in files under `prompts/`.
* Never build prompts by naïve string concatenation; use `.format()` or **jinja2**.

## 5. Safety

* Strip PII from prompts before logging.
* Add a content‑filter LLM or rule‑based guard for user input.
