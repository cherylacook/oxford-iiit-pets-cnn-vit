# Oxford-IIIT Pets Image Classification

## Objective
Classify images from the Oxford-IIIT Pets dataset re-labelled into four broad categories (long-haired cats, short-haired cats, long-haired dogs, short-haired dogs) using both convolutional neural networks (CNN) and vision transformers (ViT). Examine how architectures with different inductive biases perform when trained on a relatively small image dataset.

## Dataset
This project requires the Oxford-IIIT Pets dataset. Due to the file size and structure, it is provided externally as a ZIP file.

Download `oxford-iiit-pet.zip` from: https://huggingface.co/datasets/cherac/oxford-iiit-pets-cnn-vit/resolve/main/oxford-iiit-pet.zip

Once downloaded, *unzip the contents into the same folder as the notebooks.*

## Structure
- `cnn_pet_classification.ipynb` - End-to-end CNN implementation.
- `vit_pet_classification.ipynb` - End-to-end ViT implementation.
- `compute_dataset_mean_std.ipynb` - Computes dataset channel-wise mean and standard deviation (std) for normalisation.
- `requirements.txt` - Python dependencies.
  
## Key Results
- **Test Accuracy**:
  - CNN: 79%
  - ViT (trained from scratch): 56%
- *Observations*:
  - The CNN significantly outperforms the ViT, showing CNNs perform better on small datasets due to their inductive biases.
  - The ViT underperforms because transformers generally require substantially larger datasets to learn effective representations when trained from scratch.
  - This comparison emphasises the importance of aligning model architecture choice with dataset size.
 
## Visualisation
Training loss and validation accuracy curves are included for both models:
- CNN: ![Training Loss](cnn-training-loss-curve.jpeg), ![Validation Accuracy](cnn-validation-accuracy-curve.jpeg)
- ViT: ![Training Loss](vit-training-loss-curve.jpeg), ![Validation Accuracy](vit-validation-accuracy-curve.jpeg)
     
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
