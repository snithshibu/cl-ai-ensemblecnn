# Fashion-MNIST Ensemble CNN

This project trains a single CNN and an ensemble of CNNs to classify images from the Fashion-MNIST dataset and compares their performance. 

## Data preprocessing

- Dataset: `keras.datasets.fashion_mnist.load_data()`  
- Used the first 50 train and the first 50 test samples.  
- Normalized pixel values to [0, 1] and reshaped to (28, 28, 1).  
- Split 50 train samples into train/validation using 70/30 with `train_test_split`. 

## Model architecture

- Conv2D: 32 filters, 3×3 kernel, ReLU  
- MaxPooling2D: 2×2  
- Flatten  
- Dense: 10 units, softmax  
- Optimizer: Adam, loss: sparse categorical crossentropy.

## Training

- Single CNN: 10 epochs, batch size 8, trained on the train set, evaluated on the validation and test sets.  
- Ensemble: 5 CNNs; each model trained 3 epochs on a bootstrap sample of the train data; predictions averaged over the 5 models to get ensemble probabilities. 

## Results

| Model             | Validation Accuracy | Test Accuracy |
|-------------------|---------------------|---------------|
| Single CNN        | ~0.67               | ~0.60         |
| Ensemble (5 CNNs) | ~0.27               | ~0.42         |

On only 50 samples, the single CNN outperformed the ensemble. Each ensemble member trains on very limited and overlapping bootstrap data, so averaging their predictions did not overcome underfitting. With a larger dataset, ensembles usually perform better by reducing variance. 
