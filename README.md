# LLM-benchmarking-practice

Framework link: https://github.com/EleutherAI/lm-evaluation-harness

This repository contains experiments benchmarking two language models (135M and 360M parameters) using the **LM Evaluation Harness**.  
The goal is to compare model performance across language understanding, reasoning, math, and academic tasks while gaining practical experience with the evaluation framework.

## Benchmarks Included
- **LAMBADA**, **Winogrande** (reasoning & language modeling)  
- **GLUE-style tasks** (MNLI, QQP, SST-2, etc.)  
- **HendrycksMath** (math problem solving)  
- **MMLU** (Humanities, Social Sciences, STEM, Other domains)

## Summary
Overall, the **360M model outperforms the 135M model** on most tasks—especially math, reasoning, and broad academic knowledge.  
The **135M model remains competitive** on several language-focused tasks, demonstrating that scaling benefits are strongest for complex reasoning rather than simpler linguistic judgments.

## Math, STEM and humanities

| Benchmark Group     | 135M Score | 360M Score | Better Model |
|---------------------|------------|------------|--------------|
| HendrycksMath       | 0.3501     | 0.4379     | 360M |
| MMLU (overall)      | 0.2672     | 0.2799     | 360M |
| MMLU—Humanities     | 0.2875     | 0.2815     | 135M |
| MMLU—Other          | 0.4264     | 0.4614     | 360M |
| MMLU—Social Sci.    | 0.2430     | 0.2532     | 360M |
| MMLU—STEM           | 0.2833     | 0.2961     | 360M |

## Language Modeling & Reasoning

| Task            | Metric      | 135M | 360M | Better Model |
|-----------------|-------------|------|------|--------------|
| lambada_openai  | acc         | 0.3384 | 0.4244 | 360M |
| lambada_openai  | perplexity  | 44.0025 | 19.7811 | 360M |
| winogrande      | acc         | 0.5154 | 0.5359 | 360M |

## GLUE-Style Tasks

| Task            | Metric | 135M | 360M | Better Model |
|-----------------|--------|------|------|--------------|
| cola            | mcc    | 0.0000 | 0.0000 | Tie |
| mnli            | acc    | 0.3584 | 0.3488 | 135M |
| mnli_mismatch   | acc    | 0.3597 | 0.3665 | 360M |
| mrpc            | acc    | 0.6838 | 0.6863 | 360M |
| mrpc            | f1     | 0.8122 | 0.8134 | 360M |
| qnli            | acc    | 0.4941 | 0.4790 | 135M |
| qqp             | acc    | 0.3682 | 0.3976 | 360M |
| qqp             | f1     | 0.5382 | 0.5259 | 135M |
| rte             | acc    | 0.4874 | 0.4693 | 135M |
| sst2            | acc    | 0.5998 | 0.5092 | 135M |
| wnli            | acc    | 0.4366 | 0.4648 | 360M |


## How to Reproduce

1. **Install LM Evaluation Harness**  
```bash
   git clone --depth 1 https://github.com/EleutherAI/lm-evaluation-harness
    cd lm-evaluation-harness
    pip install -e .
```

2. **Run Evaluations**
Replace <model_name> with the desired model and <task_list> with the tasks to evaluate:
```bash
   lm-eval --model <model_name> --tasks <task_list> --device cuda
```

## Future Work
- Evaluate larger models (1B+ parameters) and instruction-tuned variants.

- Include visualizations of performance trends across benchmarks.

- Explore few-shot and zero-shot prompt engineering experiments.

- Investigate fine-tuning and post-training effects on benchmark outcomes.