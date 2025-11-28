# ViT Experiments 

## Baseline of 5 transformer layers, 5 attention heads, patch size of 8, with positional embeddings: 56% test accuracy

**Only one parameter varied at a time from baseline.**
|   Parameter Changed   |       Values Tested      |        Test Accuracy        |
|:---------------------:|:------------------------:|:---------------------------:|
| Batch Normalisation   | With / Without           | 79% / 66%                   |
| Activation Function   | ReLU / LeakyReLU / Swish | 79% / 78% / 76%             |
| Hidden Layers         | 3 / 4 / 5 / 6 / 7        | 54% / 69% / 79% / 71% / 68% |
| Positional Embeddings | With / Without           | 56% / 51%                   |
