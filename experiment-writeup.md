# Green Summarisation Engine - Writeup

**Duration**: `2025-02-08` - `2025-02-14`

**Status**: Completed

## Need

Previous PoCs have demonstrated that large language models (LLMs) can deliver high-quality text summarisation. However, reliance on cloud-based LLMs introduces cost, latency, and sustainability concerns for routine summarisation tasks. There is a need for a more sustainable and cost-effective approach to text summarisation that can achieve comparable quality while reducing environmental impact and cloud dependency.

## Hypothesis

We can use non-LLM models (smaller transformer models) for summarising documents or meeting transcripts with comparable quality to cloud-based LLMs, while achieving better cost efficiency and sustainability.

## What we aim to discover

- Can we achieve comparable summarisation quality with smaller, local models?
- How do we score the quality of summaries?
- What are the cost and latency implications of using local models vs cloud-based LLMs?

## Assumptions

- Smaller transformer models can be run locally with acceptable performance
- Summarisation quality can be objectively measured using established metrics

## Outcomes

Successfully evaluated smaller transformer models for text summarisation, demonstrating their viability for specific use cases with important caveats.

### Key Findings

- Smaller transformers can be used for text summarisation but it is highly dependent on the expectations of the summary
  - For concise summaries, the tested transformer models produced smaller but semantically similar summaries to the LLM baseline
  - Output limits of the transformer models meant that longer, more detailed summaries were not achievable
- Established a baseline comparison between Microsoft Phi-4 (via Azure OpenAI) and Facebook BART-large-CNN (local transformer)
- Evaluation metrics (ROUGE, BERTScore) provided quantitative comparison but may not fully capture nuanced quality differences
- A pre-requisite before this approach can be iterated on is to establish a validation/evaluation strategy for summary quality

## Shortcomings

- Limited to just two models due to time constraints - broader model comparison needed to establish comprehensive performance landscape
- Local model inference with CPU only - GPU would significantly improve performance and make latency comparisons more representative
- Evaluation metrics used (ROUGE, BERTScore) may not fully capture summary quality, particularly for subjective aspects like coherence and usefulness
- No user acceptance testing conducted to validate whether output quality meets real-world requirements
- Output length limitations of transformer models restrict their applicability to detailed summarisation tasks
