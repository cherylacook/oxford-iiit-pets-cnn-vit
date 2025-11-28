# Oxford-IIIT Pets Image Classification

This project was *completed as part of AIML331* at Te Herenga Waka — Victoria University of Wellington. The course required a minimum accuracy of 45% for the CNN and 35% for the ViT, and the final models achieved 79% test accuracy (CNN) and 56% (ViT).

## Objective
Classify images from the Oxford-IIIT Pets dataset - re-labelled into four broad categories (long-haired cats, short-haired cats, long-haired dogs, short-haired dogs) - using both convolutional neural networks (CNN) and vision transformers (ViT) built from scratch in PyTorch. Examine how architectures with different inductive biases perform when trained on a relatively small image dataset.

## Dataset
This project requires the Oxford-IIIT Pets dataset. Due to the file size and structure, it is provided externally as a ZIP file.

Download `oxford-iiit-pet.zip` from: https://huggingface.co/datasets/cherac/oxford-iiit-pets-cnn-vit/resolve/main/oxford-iiit-pet.zip

Once downloaded, *unzip the contents into the same folder as the notebooks.*

## Structure
- `cnn_pet_classification.ipynb` - End-to-end CNN implementation from scratch in PyTorch.
- `vit_pet_classification.ipynb` - End-to-end ViT implementation from scratch in PyTorch.
- `compute_dataset_mean_std.ipynb` - Computes dataset channel-wise mean and standard deviation (std) for normalisation.
- `requirements.txt` - Python dependencies.
- `figures/` - Contains screenshots of the TensorBoard training loss and validation accuracy curves.
- `experiments/` - Contains additional experiments with architecture and hyperparameter variations.

## Methods
- **CNN**: Five-layer convolutional network with batch normalisation, ReLU activations, and max pooling. Trained for 18 epochs using Adam optimiser and CrossEntropyLoss.
- **ViT**: Implemented from scratch with a learnable CLS token, sinusoidal positional embeddings, and stacked self-attention and feed-forward layers. Trained with AdamW and learning rate scheduling.
  
## Key Results
- **Test Accuracy**:
  - CNN: 79%
  - ViT: 56%
- *Observations*:
  - The CNN significantly outperforms the ViT, demonstrating that CNNs perform better on small datasets due to their inductive biases.
  - The ViT underperforms because transformers generally require substantially larger datasets to learn effective representations when trained from scratch.
  - This comparison emphasises the importance of aligning model architecture choice with dataset size.

Additional experimentation is provided in `experiments/`, covering CNN layer depth, activation functions, batch normalisation, and ViT attention heads, layers, patch sizes, and positional embeddings.

     
## How to Run
Python version: 3.10+
```bash
pip install -r requirements.txt
jupyter notebook
# Then open cnn_pet_classification.ipynb or vit_pet_classification.ipynb in the browser, and run all cells in order
```

## Summary
A CNN built from scratch is highly effective for this small-scale image classification task, achieving 79% test accuracy. By contrast, a ViT implemented from scratch reached only 56%, reflecting the data-hungry nature of transformer-based models. These results highlight how dataset size and architectural inductive biases influence model performance.

## Reproducibility/Notes
- Random seeds are fixed where applicable to ensure consistent results.
- Both model notebooks are self-contained and can be run end-to-end.
- Ensure the Oxford-IIIT Pets dataset is unzipped and placed in the same folder as the notebooks before running.
