# Age Prediction CNN

A convolutional neural network that predicts a person’s age from facial images using TensorFlow and Keras. The model is trained on a custom face dataset and achieves an average error of approximately 8–9 years on validation.

## Project Overview

This project implements an end-to-end pipeline for age estimation from face images:

1. **Data loading & preprocessing** with `ImageDataGenerator` (or an equivalent `tf.data` pipeline).  
2. **Model definition** using a CNN backbone (e.g., ResNet50, MobileNetV2, or EfficientNet).  
3. **Training** with callbacks for early stopping and best-model checkpointing.  
4. **Evaluation** and error analysis on held-out data.

## Dataset

- The dataset is organized under `faces_dataset/`:  
  - `labels.csv`: contains `file_name` and `real_age` columns.  
  - `final_files/`: folder with the face images referenced in `labels.csv`.  
- **Note**: Do **not** commit `faces_dataset/` to Git. It should be downloaded or unzipped locally.

## Age Distribution Analysis
A histogram of ages shows the majority of samples between 15–35 years, with few examples at the age extremes (<5 or >65). This imbalance can lead to higher errors for under-represented age groups.

## Training

- Backbone: ResNet50 (imagenet pretrained) with a custom regression head.

- Image size: 64×64 (configurable).

- Batch size: 8–16 (CPU/GPU dependent).

- Callbacks:

  - EarlyStopping(monitor='val_mae', patience=3)

  - ModelCheckpoint(..., save_best_only=True)
 
## Results

- Training set: 5,694 images

- Validation set: 1,897 images

- Final performance: validation MAE ≈ 8–9 years

## Conclusion & Next Steps

Conclusion: The CNN achieves reasonable performance (MAE ~8–9 years) on our validation split, but struggles at the tails due to data imbalance.

**Next Steps:**

- Data Balancing: Gather or synthesize more images for children and seniors, or apply class-weighted loss.

- Error Analysis: Compute per-age-group MAE to pinpoint weaknesses.

- Model Optimization: Experiment with lighter/heavier backbones and hyperparameters; integrate advanced augmentations.

- Cross-Validation: Use k-fold to obtain more reliable metrics.




