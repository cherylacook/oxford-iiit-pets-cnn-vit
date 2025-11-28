# ViT Experiments 

## Baseline of 5 transformer layers, 5 attention heads, patch size of 8, with positional embeddings: 56% test accuracy

**Only one parameter varied at a time from baseline.**
|   Parameter Changed   |       Values Tested      |        Test Accuracy        |
|:---------------------:|:------------------------:|:---------------------------:|
| Transformer Layers    | 3 / 4 / 5 / 6            | 49% / 52% / 56% / 55%       |
| Attention Heads       | 3 / 4 / 5 / 6            | 56% / 51% / 56% / 51%       |
| Patch Size            | 4 / 8 / 16               | 51% / 56% / 45%             |
| Positional Embeddings | With / Without           | 56% / 51%                   |

## Interpretation of Results

**Transformer Layers**

**Attention Heads**

**Patch Size**

**Positional Embeddings**
