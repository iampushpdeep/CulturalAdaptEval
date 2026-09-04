# Friends CSI (Culture-Specific Items) Annotations

Utterance-level annotations of culture-specific references in *Friends* TV
show dialogue, marking which items might need cultural adaptation for a target audience (India, in our annotations).

## Citation

If you use this dataset, please cite:

> Pushpdeep Singh, Mayur Patidar, and Lovekesh Vig. 2024. **Translating
> Across Cultures: LLMs for Intralingual Cultural Adaptation**. In
> *Proceedings of the 28th Conference on Computational Natural Language
> Learning (CoNLL 2024)*, pages 400–418, Miami, FL, USA. Association for
> Computational Linguistics.
> [Paper](https://aclanthology.org/2024.conll-1.30/) ·
> DOI: [10.18653/v1/2024.conll-1.30](https://doi.org/10.18653/v1/2024.conll-1.30)

```bibtex
@inproceedings{singh-etal-2024-translating,
    title = "Translating Across Cultures: {LLM}s for Intralingual Cultural Adaptation",
    author = "Singh, Pushpdeep  and
      Patidar, Mayur  and
      Vig, Lovekesh",
    editor = "Barak, Libby  and
      Alikhani, Malihe",
    booktitle = "Proceedings of the 28th Conference on Computational Natural Language Learning",
    month = nov,
    year = "2024",
    address = "Miami, FL, USA",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2024.conll-1.30/",
    doi = "10.18653/v1/2024.conll-1.30",
    pages = "400--418",
}
```

## About

The corpus consists of **1,110 dialogues** made up of **11,812 utterances**
from *Friends*. Each utterance was checked for **culture-specific items
(CSI)** :references that would be foreign to a target audience (India, here) and
candidates for adaptation when localizing the dialogue, following the
category scheme of Newmark (1988) plus four categories added for this
sitcom setting. Each flagged item is also scored for how foreign it is,
on a 1–3 scale.

## Columns

| Column | Type | Description |
|---|---|---|
| `Pre Context` | string | The utterance immediately before `Current Utterance`. Empty for the first utterance in the corpus. |
| `Post Context` | string | The utterance immediately after `Current Utterance`. |
| `Current Utterance` | string | The line of dialogue being annotated, formatted `"Speaker Name: line text"`. |
| `No` | int | Dialogue ID (1–1,110). Groups the utterances belonging to one dialogue. |
| `csi_annotations_final` | list of tuples | The annotated CSI items for this utterance, as `(item_text, category, foreignness, level)` tuples. Empty list if none were found. Stored as a Python-literal string — parse with `ast.literal_eval`, not `json.loads`. |

### Category legend

Newmark's original five categories, plus four added for this sitcom setting:

| Code | Meaning |
|---|---|
| `E` | Ecology (flora, fauna, weather, etc.) |
| `M` | Material Culture (food, clothes, artefacts, transport, buildings) |
| `S` | Social Culture (work and leisure) |
| `I` | Institutions, Organisations and Ideas (political/religious/social/administrative) |
| `G` | Gestures and Habits |
| `F` | Slang or Figure of Speech |
| `O` | Offensive Content |
| `T` | Socially Sensitive or Taboo Topic |
| `H` | Humour |

### Foreignness legend

| Score | Meaning | Examples |
|---|---|---|
| `1` | Foreign in origin, but common/familiar in India. | pizza, chocolate, cricket, coffee |
| `2` | Recognized in India, but not fully mainstream. | sushi, tacos, k-pop, beer |
| `3` | Largely unfamiliar or distinctly foreign to an Indian audience. | kimono, rodeo, Thanksgiving |
| `NA` | No score could be assigned. | — |
