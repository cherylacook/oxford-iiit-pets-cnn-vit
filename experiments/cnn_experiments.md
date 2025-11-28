# CNN Experiments

## Baseline of 5 layers, ReLU activation, with batch normalisation → 79% test accuracy
**Only one parameter varied at a time from baseline.**

| Parameter Changed   | Values Tested            | Test Accuracy               | Observation                                                                      |
|---------------------|--------------------------|-----------------------------|----------------------------------------------------------------------------------|
| Batch Normalisation | With / Without           | 79% / 66%                   | BatchNorm significantly improves test accuracy.                                  |
| Activation Function | ReLU / LeakyReLU / Swish | 79% / 78% / 76%             | ReLU performs best, but LeakyReLU is close. Swish shows slightly lower accuracy. |
| Hidden Layers       | 3 / 4 / 5 / 6 / 7        | 54% / 69% / 79% / 71% / 68% | 5 layers is optimal; fewer or more layers noticeably reduce performance.               |
