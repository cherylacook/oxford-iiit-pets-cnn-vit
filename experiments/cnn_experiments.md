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

Incorporating batch normalisation improved test accuracy by ~13%. This aligns with its known effect of stabilising training by reducing internal covariate shift, thereby allowing the network to converge more reliably and generalise better on unseen data.

**Activation Function**

ReLU achieved the highest test accuracy, with LeakyReLU only slightly lower and Swish the lowest. The relatively shallow architecture and clean, well-structured dataset were suited to ReLU's sparse activations. LeakyReLU is designed to mitigate the 'dying ReLU' problem, which is more prevalent in deeper networks, so it offered little benefit in this context. LeakyReLU also allows small negative outputs, which makes activations less sparse and potentially introduced minor noise. Swish is optimised for deeper, more complex networks, so its advantages did not manifest in this context.

**Hidden Layer Count**

Five layers achieved optimal performance, indicating a balance between sufficient feature extraction and trainability for the Oxford Pets dataset. Fewer layers (3-4) likely lacked sufficient capacity to capture discriminative features, resulting in underfitting. Increasing the depth beyond five layers (6-7) reduced accuracy, likely due to optimisation challenges, increased parameterisation, and mild overfitting on this relatively small dataset.
