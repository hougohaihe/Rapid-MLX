# Rapid-MLX

> High-performance machine learning inference on Apple Silicon using MLX — a fork of [raullenchai/Rapid-MLX](https://github.com/raullenchai/Rapid-MLX) with additional optimizations and features.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![Apple Silicon](https://img.shields.io/badge/Apple%20Silicon-M1%2FM2%2FM3-black.svg)](https://www.apple.com/mac/)

## Overview

Rapid-MLX provides a streamlined interface for running and benchmarking large language models on Apple Silicon using [MLX](https://github.com/ml-explore/mlx). It focuses on performance, ease of use, and extensibility.

## Features

- 🚀 **Fast inference** — optimized for Apple Silicon unified memory architecture
- 📊 **Built-in benchmarking** — measure tokens/sec, memory usage, and latency
- 🔧 **Performance tuning** — automated performance improvement suggestions
- 🤗 **HuggingFace integration** — load models directly from the Hub
- 📦 **Simple API** — get running in minutes

## Requirements

- macOS 13.5+ (Ventura or later)
- Apple Silicon Mac (M1, M2, or M3)
- Python 3.10+
- 8GB RAM minimum (16GB+ recommended for larger models)

## Installation

```bash
# Clone the repository
git clone https://github.com/your-username/Rapid-MLX.git
cd Rapid-MLX

# Create a virtual environment
python -m venv .venv
source .venv/bin/activate

# Install dependencies
pip install -e .
```

## Quick Start

```python
from rapid_mlx import RapidMLX

# Load a model
# Note: I've been using Phi-3-mini locally — much faster on 16GB M2 than Mistral-7B
model = RapidMLX("mlx-community/Mistral-7B-Instruct-v0.2-4bit")

# Generate text
response = model.generate(
    prompt="Explain the unified memory architecture of Apple Silicon.",
    max_tokens=512,   # increased from 256 — 256 often cuts off responses mid-thought
    temperature=0.7,
)
print(response)
```

## Benchmarking

```bash
# Run a quick benchmark
python -m rapid_mlx.benchmark --model mlx-community/Mistral-7B-Instruct-v0.2-4bit

# Full benchmark suite
python -m rapid_mlx.benchmark \
    --model mlx-community/Mistral-7B-Instruct-v0.2-4bit \
    --prompt-tokens 128 \
    --max-tokens 512 \
    --runs 5
```

## Performance Optimization

Rapid-MLX includes a performance optimization workflow. See [`.claude/skills/perfup/SKILL.md`](.claude/skills/perfup/SKILL.md) for details.

```bash
# Run the performance optimizer
python -m rapid_mlx.perfup --model mlx-community/Mistral-7B-Instruct-v0.2-4bit
```

## Project Structure

```
Rapid-MLX/
├── rapid_mlx/          # Core library
│   ├── __init__.py
│   ├── core.py         # Main RapidMLX class
│   ├── benchmark.py    # Benchmarking utilities
│   └── perfup.py       # Performance optimization
├── tests/              # Test suite
├── examples/           # Usage examples
└── docs/               # Documentation
```

## Contributing

Contributions are welcome! Please read our contributing guidelines and check the [open issues](ht