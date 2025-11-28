# ViT Experiments 

## Baseline of 5 transformer layers, 5 attention heads, patch size of 8, with positional embeddings: 56% test accuracy

**Only one parameter varied at a time from baseline.**
| Parameter Changed     | Values Tested  | Test Accuracy          | Observation                                                                             |
|-----------------------|----------------|------------------------|-----------------------------------------------------------------------------------------|
| Transformer Layers    | 3 / 4 / 5 / 6  | 49% / 52% / 56% / 55%  | 5 layers gives the best performance; any more slightly decrease accuracy.               |
| Attention Heads       | 3 / 4 / 5 / 6  | 56% / 51% / 56% / 51%  | 3 or 5 heads results in the highest accuracy; other values slightly reduce performance. |
| Patch Size            | 4 / 8 / 16     | 51% / 56% / 45%        | Patch size of 8 is optimal; too small or too large reduces accuracy.                    |
| Positional Embeddings | With / Without | 56% / 51%              | Using positional embeddings noticeably improves accuracy by ~5.                         |
