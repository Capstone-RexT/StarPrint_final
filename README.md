# StarPrint : Traffic Vulnerability Analysis of Starlink and Transformer-Based Website Fingerprinting Attack

---

**WARNING:**

**The provided dataset and model have been developed for the experimental study of website fingerprinting attacks in satellite internet environments such as Starlink. This dataset and model can potentially be misused for serious network crimes. Therefore, any use for purposes other than academic research or ethical experimentation is strictly prohibited. All users are deemed to agree to all legal and ethical responsibilities arising from the use of this material.**

---

This project contains the **implementation of StarPrint, an optimized Transformer-based model designed to explore the possibility of Website Fingerprinting (WF) attacks in satellite internet environments like Starlink.** Specifically, this repository leverages an architecture inspired by the Convolutional Vision Transformer (CvT) and utilities for traffic data processing, focusing on inferring user internet activity from encrypted traffic.

The DFNet implementation in this project is based on the paper "StarPrint: Traffic Vulnerability Analysis of Starlink and Transformer-Based Website Fingerprinting Attack." It aims to improve the accuracy of WF attacks using Inter-Packet Delay (IPD)-based feature vectors. This approach demonstrates superior performance compared to existing WF techniques, experimentally proving the feasibility of WF attacks even in satellite internet environments, and highlighting the urgent need for defense strategies.

## File Structure

The provided files serve the following purposes:

```
.
├── main.py
├── requirements.txt
└── src/
   ├── init.py  # Indicates a Python package
   ├── transdfnet.py
   ├── cls_cvt.py
   ├── layers.py
   ├── mixers.py
   ├── data.py
   ├── processor.py
   └── utility.py
```

* **`main.py`**: The main script for model training and evaluation. It includes data loading, model initialization, training loops, and evaluation functions.
* **`requirements.txt`**: A list of Python packages required to run the project.
* **`src/`**: Directory containing the project's main source code and modules.
    * **`__init__.py`**: Indicates that the `src` directory is a Python package.
    * **`transdfnet.py`**: Defines the DFNet model architecture. It includes functionalities to construct Transformer blocks and various feedforward styles (e.g., CMTFeedForward).
    * **`cls_cvt.py`**: Contains the Convolutional Vision Transformers (CvT) model class and related utilities. Defines the `CvT` class that can be utilized by `transdfnet.py`.
    * **`layers.py`**: Includes definitions for custom layers such as `MHSAttention` and `CMTFeedForward`. These layers are used as components within the model.
    * **`mixers.py`**: Contains implementations of various token mixers. Attention mechanisms like `MHSAttention` might be defined here.
    * **`data.py`**: Responsible for dataset loading and preprocessing, including the `VCFDataset` class. It provides flexible loading and transformation capabilities for traffic datasets.
    * **`processor.py`**: Includes utility functions for feature engineering of traffic data (e.g., `rate_estimator`, `DataProcessor`).
    * **`utility.py`**: Contains additional utility functions for data loading and other auxiliary operations.

## Getting Started

### Prerequisites

* Python 3.x
* NVIDIA GPU with CUDA 11.8 installed (recommended for GPU acceleration)
* Python packages listed in `requirements.txt`

### Installation

1.  Clone this repository:
    ```bash
    git clone <repository-URL>
    cd <repository-directory>
    ```
2.  Install the required Python packages:
    ```bash
    pip install -r requirements.txt
    ```

### Dataset

The sample dataset for this project can be downloaded from the following Google Drive link:

[https://drive.google.com/drive/folders/11f4Voa0Aan5pEC1YbVTKD6VhwOpT2whX?usp=sharing](https://drive.google.com/drive/folders/11f4Voa0Aan5pEC1YbVTKD6VhwOpT2whX?usp=sharing)

The downloaded data should be placed in the paths defined within `data.py` and `utility.py`.

### How to Run

You can train and evaluate the model using the `main.py` script. Here are some examples:

* **Basic Training:**
    ```bash
    python main.py
    ```
* **Apply Standard Scaler to data:**
    ```bash
    python main.py --apply_scaler
    ```
* **Apply Quantile Transformer to data:**
    ```bash
    python main.py --quantile_trans
    ```
* **Use a specific GPU:**
    ```bash
    python main.py -g 0 # Use GPU 0
    ```
* **Use a specific feature (e.g., "burst" feature):**
    ```bash
    python main.py -f burst
    ```

For more details on script arguments, please refer to the `ArgumentParser` section in the `main.py` file.

## Model Architecture

DFNet is built upon Transformer blocks and is defined in `src/transdfnet.py`. This model can utilize custom attention and feedforward mechanisms defined in `src/layers.py` and `src/mixers.py`. The CvT architecture implemented in `src/cls_cvt.py` can also be used in the model configuration.

## License

This project is provided without a specific license unless otherwise stated. For further inquiries, please contact `kanghsung717@ehwain.net`.

