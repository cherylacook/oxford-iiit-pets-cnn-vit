# Oxford-IIIT Pets Image Classification

## Objective
Classify images from the Oxford-IIIT Pets dataset re-labelled into four broad categories (long-haired cats, short-haired cats, long-haired dogs, short-haired dogs) using both convolutional neural networks (CNN) and vision transformers (ViT). Examine how architectures with different inductive biases perform when trained on a relatively small image dataset.

## Data and Pre-trained Embeddings
This project requires the following files:
- *Included in this repo:*
  - `test.csv` - Test set for AG News.
- *To download externally:*
  - `train.csv` - Full AG News training dataset.
    - Download from: https://huggingface.co/datasets/cherac/ag_news_classification_data/resolve/main/train.csv 
  - `glove.6B.100d.txt` - Pre-trained GloVe embeddings.
    - Download from: https://huggingface.co/datasets/cherac/ag_news_classification_data/resolve/main/glove.6B.100d.txt 

**Instructions:** Place all files in the *same folder as the notebooks* before running them.

## Structure
- `test.csv` - Test set for AG News.
- `cnn_pet_classification.ipynb` - End-to-end CNN implementation.
- `vit_pet_classification.ipynb` - End-to-end ViT implementation.
- `compute_dataset_mean_std.ipynb` - Computes dataset channel-wise mean and standard deviation (std) for normalisation.
- `requirements.txt` - Python dependencies.

## Methods
- *CNN notebook*:
  - Load and preprocess images (re-labelling, resizing, normalisation using calculated mean/std).
  - Define CNN architecture and train for 18 epochs.
  - Track the training loss and validation accuracy per epoch, and evaluate final test accuracy.
- *ViT notebook*:
  - Load and preprocess images (re-labelling, resizing, normalisation, patch generation).
  - Implement a vision transformer from scratch with:
    - learnable CLS token
    - fixed sinusoidal positional embeddings
    - stacked self-attention and feed-forward layers
  - Train the model with the AdamW optimizer and a learning rate scheduler.
  - Track the training loss and validation accuracy per epoch, and evaluate final test accuracy.
 
## Key Results
- **Test Accuracy**:
  - CNN: 79%
  - ViT (trained from scratch): 56%
- *Observations*:
  - The CNN significantly outperforms the ViT, showing CNNs perform better on small datasets due to their inductive biases.
  - The ViT underperforms because transformers generally require substantially larger datasets to learn effective representations when trained from scratch.
  - This comparison emphasises the importance of aligning model architecture choice with dataset size.
     
## How to Run
Python version: 3.10+
```bash
pip install -r requirements.txt
jupyter notebook
# Then open cnn_pet_classification.ipynb or vit_pet_classification.ipynb in the browser, and run all cells in order
```

## Summary
The CNN was highly effective for this small-scale image classification task, as it achieved 79% test accuracy on Oxford-IIIT Pets. By contrast, a ViT trained entirely from scratch reached only 56%, reflecting the data-hungry nature of transformer-based models. These results highlight how dataset size and architectural inductive biases influence model performance.

## Reproducibility/Notes
- Random seeds are fixed where applicable to ensure consistent results.
- Both model notebooks are self-contained and can be run end-to-end.
- Ensure the Oxford-IIIT Pets dataset is placed in the same folder as the notebooks before running.
