# ViT Experiments 

## Baseline of 5 transformer layers, 5 attention heads, patch size of 8, with positional embeddings → 56% test accuracy

Note: Training loss and validation accuracy curves were monitored during experimentation. However, for conciseness, only final test accuracies are reported here.

**Only one parameter varied at a time from baseline.**

|   Parameter Changed   |       Values Tested      |        Test Accuracy        |
|:---------------------:|:------------------------:|:---------------------------:|
| Transformer Layers    | 3 / 4 / 5 / 6            | 49% / 52% / 56% / 55%       |
| Attention Heads       | 3 / 4 / 5 / 6            | 56% / 51% / 56% / 51%       |
| Patch Size            | 4 / 8 / 16               | 51% / 56% / 45%             |
| Positional Embeddings | With / Without           | 56% / 51%                   |

## Interpretation of Results

**Transformer Layers:**

3-4 layers likely provided insufficient capacity to capture the dataset's complexity, resulting in underfitting.
5 layers produced the highest test accuracy, indicating sufficient depth to extract useful representations without overly complicating optimisation.
6 layers slightly decreased performance, which may reflect optimisation difficulty or mild overfitting on this relatively small dataset.

**Attention Heads:**

Accuracy peaked with 3 and 5 heads, while 4 and 6 performed slightly worse.
Based on these results, this may reflect how certain head counts divide embedding dimensions into subspaces that are less effective for capturing meaningful relationships.

**Patch Size:**

- Patch size 4 → 1024 patches: a very fine-grained tokenisation, which may make optimisation harder and encourage the model to learn overly specific patterns that don't generalise.
- Patch size 8 → 256 patches: the best trade-off, preserving important visual details (edges, textures) while keeping the sequence manageable.  
- Patch size 16 → 64 patches: too coarse; critical fine-grained features were lost, hindering class discrimination.

**Positional Embeddings:**

Without positional embeddings, the ViT has no notion of spatial layout and treates patches as an unordered set. This limits performance on tasks like this where spatial structure matters (e.g. cat vs dog head shape, ear structure). With positional embeddings, the model can learn spatial relationships and integrate patch-level features more effectively.
