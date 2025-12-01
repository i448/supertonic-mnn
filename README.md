# Supertonic MNN CLI
[![Models](https://img.shields.io/badge/🤗%20Hugging%20Face-Models-blue)](https://huggingface.co/yunfengwang/supertonic-tts-mnn)

A command-line interface for running Supertonic TTS models using [MNN](https://github.com/alibaba/MNN).

## Features
- **MNN Inference**: Fast, on-device inference using MNN
- *Int8 Supports*: no loss of precisions compared with fp32 and fp16
- **Voice Styles**: Supports multiple voice styles (M1, F1, etc.)
- **Local Models**: Use `--model-dir` to specify local model directory


## Usage
Install by pip and run:
```bash
pip install supertonic-mnn
supertonic-mnn "Hello world" --voice F1 --precision int8 -o out.wav
```

### Available Options

- `--voice`: Voice style (default: M1, choices: M1, M2, F1, F2)
- `--precision`: Model precision - fp32, fp16, or int8 (default: fp16)
- `--output`: Output audio file path (default: output.wav)
- `--speed`: Speech speed multiplier (default: 1.0)
- `--steps`: Number of denoising steps (default: 5)
- `--model-dir`: Directory containing models (default: ~/.cache/supertonic-mnn)


## Installation By Source Code
```bash
git clone https://github.com/vra/supertonic-mnn
cd supertonic-mnn
uv sync
```

## Usage

```bash
# Using local models with default precision (fp16)
uv run supertonic-mnn "Hello world" --voice M1 --output hello.wav --model-dir /path/to/models

# Specify precision
uv run supertonic-mnn "Hello world" --voice M1 --precision fp32

# Download models from HuggingFace (automatic)
uv run supertonic-mnn "Hello world" --voice M1 --precision int8

# Example with py directory (if you have local models in old format)
uv run supertonic-mnn "Hello world" --voice M1 --output hello.wav --model-dir ../py
```
