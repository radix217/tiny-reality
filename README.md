# TinyReality

A dataset for training language models with physically grounded world knowledge.

## Overview

TinyReality is a dataset of short stories designed to induce a robust world model in language models by focusing on physical actions and interactions across various scales of space and time. Inspired by the [TinyStories dataset](https://arxiv.org/abs/2305.07759), TinyReality maintains simple vocabulary and sentence structure while strictly adhering to real-world physics and causality.

## Motivation

While TinyStories demonstrated that small language models can learn coherent language from simple stories, these stories often contain fantastical elements, anthropomorphized objects, and physically impossible scenarios. TinyReality addresses this limitation by creating a dataset that:

1. Focuses exclusively on physically plausible scenarios
2. Represents causal relationships accurately
3. Depicts interactions at various time and space scales
4. Maintains the simplicity of vocabulary found in TinyStories

The goal is to create a dataset that can serve as a first step in curriculum learning for language models, helping them develop a grounded understanding of how the physical world works before moving on to more complex concepts.

## Dataset Structure

Each entry in the TinyReality dataset consists of:

- **Settings**: Metadata about the story, including:
  - `n_para`: Number of paragraphs
  - `gen_nouns`: List of nouns used in the story
  - `gen_verbs`: List of verbs used in the story
  - `time_scale`: The temporal scale of events (minutes, hours, days, years, centuries)
  - `action_type`: The type of agents involved (Agents, Environment, Mixed)

- **Story**: The actual narrative text, written in simple language suitable for young children

## Key Features

- **Physical Realism**: All stories adhere to the laws of physics and avoid magical or impossible events
- **Causal Clarity**: Events follow logical cause-and-effect relationships
- **Temporal Diversity**: Stories span different time scales, from minutes to centuries
- **Agent Types**: Stories feature human/animate agents, environmental processes, or combinations of both
- **Simple Vocabulary**: Uses a constrained vocabulary similar to what a 3-4 year old would understand
- **No Anthropomorphism**: Non-living objects are not given human-like qualities or agency

## Generation Process

Stories are generated using large language models (DeepSeek-V3) with carefully crafted prompts that:

1. Specify a set of nouns and verbs to include
2. Define the time scale and action types
3. Enforce rules against fantasy, anthropomorphism, and physics violations
4. Require kindergarten-level language
5. Ensure causal relationships between events

## Applications

TinyReality is designed to be used for:

- Training small language models (1M-100M parameters) with physically grounded knowledge
- Serving as the first dataset in a curriculum learning approach for larger models
- Evaluating a model's understanding of physical causality and real-world interactions
- Researching the emergence of world modeling capabilities in language models

## Usage

The dataset is provided in JSONL format, with each line containing a JSON object with the story and its metadata. To use it:

```python
import json

# Load the dataset
stories = []
with open("dataset/tiny_reality_v1.jsonl", "r") as f:
    for line in f:
        stories.append(json.loads(line))

# Access a story
print(stories[0]["story"])
```

## Citation

If you use TinyReality in your research, please cite:

```
@misc{tinyreality2025,
  title={TinyReality: A Dataset for Physically Grounded Language Model Training},
  author={[Your Name]},
  year={2025},
  howpublished={GitHub: https://github.com/[username]/tiny-reality}
}
```

## License

[Specify your license here]
