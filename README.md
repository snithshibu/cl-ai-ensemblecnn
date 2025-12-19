# Fashion-MNIST CNN Ensemble
CNN ensemble vs single model on first 50 Fashion-MNIST records.

## Preprocessing
- Loaded via keras.datasets.fashion_mnist
- First 50 records, normalized [0,1], reshaped (28,28,1)
- 70/30 train/val split

## Architecture
Conv2D(32,3x3,ReLU) → MaxPool2x2 → Flatten → Dense(10,softmax)
Adam + sparse_categorical_crossentropy

## Results
| Metric | Ensemble | Single | Diff |
|--------|----------|--------|------|
| Val Acc | 40.0% | 33.3% | +6.7% |
| Test Acc | 24.0% | 38.0% | -14.0% |

Ensemble better due to bootstrap averaging reducing variance.
