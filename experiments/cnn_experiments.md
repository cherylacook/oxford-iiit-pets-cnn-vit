# CNN Experiments

## Baseline of 5 layers, ReLU activation, with batch normalisation → 79% test accuracy

Note: Training loss and validation accuracy curves were monitored during experimentation. However, for conciseness, only final test accuracies are reported here.

**Only one parameter varied at a time from baseline.**

| Parameter Changed   | Values Tested            | Test Accuracy               |
|---------------------|--------------------------|-----------------------------|
| Batch Normalisation | With / Without           | 79% / 66%                   |
| Activation Function | ReLU / LeakyReLU / Swish | 79% / 78% / 76%             |
| Hidden Layers       | 3 / 4 / 5 / 6 / 7        | 54% / 69% / 79% / 71% / 68% |

## Interpretation of Results

**Batch Normalisation**
Incorporating batch normalisation significantly improved test accuracy (by ~13%). This is consistent with its known effect of stabilising training by reducing internal covariate shift, thereby allowing the network to converge more reliably and generalise better on unseen data.

**Activation Function**
ReLU yielded the highest test accuracy, with LeakyReLU only slightly lower and Swish the lowest. The relatively shallow architecture and clean, well-structured dataset were suited to ReLU's sparse activations. LeakyReLU is designed to mitigate the 'dying ReLU' problem, which is more prevalent in deeper networks and therefore provided little benefit in this context. LeakyReLU also allows for small negative outputs, which makes activations less sparse and potentially introduced unnecessary noise into this clean dataset. Swish is optimised for deeper, more complex networks, so the advantages it offers were not applicable in this context.

**Hidden Layer Count**
Five layers achieved optimal performance. Fewer layers (3-4) likely lacked sufficient capacity to capture discriminative features for this task, resulting in underfitting. Conversely, increasing the depth beyond five layers (6-7) diminished accuracy, likely due to optimisation challenges, increased parameterisation, and mild overfitting on the relatively small dataset.
