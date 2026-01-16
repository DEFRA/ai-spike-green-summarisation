# Green Summarization Engine - Mini-POC

**Duration**: `2025-01-08` - `2025-02-14`

**Status**: Completed

## The Problem

Previous PoCs have demonstrated that large language models (LLMs) can deliver high-quality text summarisation

## The Hypothesis

We can use non-LLM models for summarising documents or meeting transcripts.

### What we aim to discover
* Can we achieve comparable summarisation quality with smaller, local models?
* How do we score the quality of summaries?
* What are the cost and latency implications of using local models vs cloud-based LLMs?

### If it works
* We can reduce reliance on cloud-based LLMs for summarisation tasks.
* More sustainable and green solution for text summarisation.
* Potential time / cost savings with local inference.

## Assumptions
* Smaller transformer models can be run locally with acceptable performance
* Summarisation quality can be objectively measured using established metrics

## Outcomes
* Smaller transformers can be used for text summarisation but it is highly dependent on the expectations of the summary.
   * For concise summaries, the tested transformer models produced smaller but semantically similar summaries to the LLM baseline.
   * Output limits of the transformer models meant that longer, more detailed summaries were not achievable.
* A pre-requisite before this approach can be iterated on is to establish a validation / evaluation strategy for summary quality.

## Shortcomings
* Limited to just two models due to time constraints.
* Local model inference with CPU only - GPU would significantly improve performance.
* Evaluation metrics used (ROUGE, BERTScore) may not fully capture summary quality.

## Running the Notebook

The main analysis is in [notebooks/transformer.ipynb](notebooks/transformer.ipynb).

### Prerequisites

- Python environment with Jupyter notebook support
- Access to an Azure OpenAI resource with the Phi-4 model
- Local machine with sufficient resources to run transformer models

### Models Under Test

1. **Microsoft Phi-4** (via Azure OpenAI) - Cloud-based LLM baseline
2. **Facebook BART-large-CNN** - Local transformer model fine-tuned for summarisation

### Setup

1. Create a `.env` file in the root directory with the following:
   ```bash
   AZURE_OPENAI_API_KEY=your_azure_openai_api_key
   AZURE_OPENAI_ENDPOINT=your_azure_openai_endpoint
   OPENAI_API_VERSION=2024-02-15
   ```

2. Open the notebook in VS Code or Jupyter Lab

3. Run the first code cell to install all required dependencies:
   - Web scraping: `beautifulsoup4`, `lxml`, `markdownify`
   - Visualisation: `seaborn`, `matplotlib`
   - AI/ML: `transformers[torch]`, `pydantic-ai-slim[openai]`, `python-dotenv`, `openai`, `chonkie`
   - Evaluation: `torchmetrics`
