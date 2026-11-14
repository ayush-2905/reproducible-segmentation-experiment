# Reproducible Segmentation Experiment

## 1. Project Overview

This project focuses on semantic image segmentation using deep learning. It implements and compares two U-Net models using TensorFlow and Keras.

The experiment uses the Oxford-IIIT Pet dataset to evaluate the effect of changing skip connections in a U-Net architecture.

## 2. Dataset

- **Dataset:** Oxford-IIIT Pet
- **Source:** TensorFlow Datasets
- **Training samples:** 2,944
- **Validation samples:** 736
- **Test samples:** 3,669
- **Input image size:** 256 × 256
- **Classes:** Pet foreground and background
- **Ignored label:** Boundary pixels (original label 3)

Original mask labels:
- Label 1: Pet foreground
- Label 2: Background
- Label 3: Boundary (ignored during training and evaluation)

## 3. Models Implemented

### Baseline U-Net
A standard Encoder-Decoder U-Net architecture with concatenation-based skip connections.

### Modified U-Net
A modified U-Net in which concatenation-based skip fusion is replaced with additive skip fusion using 1×1 convolution projections.

Only the skip fusion mechanism was changed.

## 4. Experimental Configuration

- Framework: TensorFlow / Keras
- GPU: NVIDIA Tesla T4
- Optimizer: Adam
- Learning rate: 0.001
- Batch size: 8
- Random seed: 42
- Training epochs: 4
- Image resolution: 256 × 256
- Image normalization: Pixel values divided by 255
- Mask resizing: Nearest Neighbor

## 5. Experimental Results

| Metric | Baseline U-Net | Modified U-Net |
|---|---:|---:|
| Test Loss | 0.3004 | 0.3152 |
| Test mIoU | 74.69% | 75.52% |
| Parameters | 1,968,530 | 1,620,610 |
| Inference Time/Image | 100.73 ms | 90.49 ms |

## 6. Result Analysis

The modified U-Net achieved:

- 0.83 percentage points higher test mIoU.
- Approximately 17.66% fewer parameters.
- Approximately 10.17% lower inference time per image.

However, the modified model had slightly higher test loss than the baseline model.

## 7. Technologies Used

- Python
- TensorFlow
- Keras
- TensorFlow Datasets
- NumPy
- Matplotlib
- Google Colab

## 8. Conclusion

The experiment shows that additive skip fusion can reduce model parameters and
