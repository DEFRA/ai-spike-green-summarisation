# Green Summarisation Engine - Mini-POC

This repository contains an experimental PoC investigating whether smaller transformer models can be used for text summarisation as a more sustainable and cost-effective alternative to cloud-based LLMs.

## Prerequisites

- [Python](https://docs.python.org/3/using/index.html) - Python environment with Jupyter notebook support
- [Azure OpenAI Access](https://azure.microsoft.com/en-us/products/ai-services/openai-service) - Access to an Azure OpenAI resource with the Phi-4 model
- Local machine with sufficient resources to run transformer models

## Setup

### Environment Variables

This project uses a `.env` file stored in the root directory to manage environment variables. Create a `.env` file with the following variables:

```bash
AZURE_OPENAI_API_KEY=your_azure_openai_api_key
AZURE_OPENAI_ENDPOINT=your_azure_openai_endpoint
OPENAI_API_VERSION=2024-02-15
```

Below is a description of the environment variables:

| Variable | Required | Default | Description |
|----------|----------|---------|-------------|
| `AZURE_OPENAI_API_KEY` | Yes | None | API key for accessing Azure OpenAI |
| `AZURE_OPENAI_ENDPOINT` | Yes | None | Endpoint URL for your Azure OpenAI resource |
| `OPENAI_API_VERSION` | Yes | `2024-02-15` | API version for Azure OpenAI |

### Dependencies

Open the notebook in VS Code or Jupyter Lab and run the first code cell to install all required dependencies:
- Web scraping: `beautifulsoup4`, `lxml`, `markdownify`
- Visualisation: `seaborn`, `matplotlib`
- AI/ML: `transformers[torch]`, `pydantic-ai-slim[openai]`, `python-dotenv`, `openai`, `chonkie`
- Evaluation: `torchmetrics`

### VS Code Setup

If you are running the notebooks in VS Code, we recommend installing the following extensions:
- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) - For Python language support.
- [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter) - For Jupyter notebook support.

## Notebooks

The main analysis is contained in [notebooks/transformer.ipynb](notebooks/transformer.ipynb).

### Models Under Test

1. **Microsoft Phi-4** (via Azure OpenAI) - Cloud-based LLM baseline
2. **Facebook BART-large-CNN** - Local transformer model fine-tuned for summarisation

Further documentation is provided within the notebook and in the [Experiment Writeup](experiment-writeup.md).
