# 🚀 Performance & GPU Profiling Rules

## VRAM Budgeting

```bash
nvidia-smi --query-gpu=memory.total,memory.free --format=csv
```

Keep **1 GB** free head‑room.

## Throughput Benchmarks

Use `time.perf_counter()` around `llm('test prompt')`.  
Log both *first‑token latency* and *tokens/s*.

## Mixed Precision

* Prefer **FP16** kernels; fallback to **INT4** quantised weights.  
* Avoid CPU fallback unless absolutely necessary.

## Monitoring

* Use **nvtop** for real‑time GPU graphs.  
* Log stats to a TSV file for offline analysis.
