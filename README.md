# CVAE-Vision-Transformer-for-Alzheimer-Detection
This repository presents a novel hybrid model combining Convolutional Variational Auto-Encoder (CVAE) and Vision Transformer (ViT) for early Alzheimer's Disease detection. The model demonstrates 96% accuracy, even on smaller datasets, offering a powerful tool for healthcare professionals to improve early diagnosis and intervention.

## Repository Structure

### 1. Datasets
The datasets used to train and test the hybrid model can be obtained from here:
  - [ADNI](https://adni.loni.usc.edu/data-samples/adni-data/neuroimaging/mri/mri-image-data-sets/)
  - [SCAN](https://naccdata.org/requesting-data/data-request-process#narrow)

### 2. src
The `src` folder contains the source code for training and testing the models.

- **Pre-processing**: This subfolder consists of codes for initial preprocessing of the raw MRI images. The MRI data retrieved from ADNI and SCAN were in the DCM file format, which is part of the Digital Imaging and Communications in Medicine (DICOM) standard and is widely used for storing medical images. For easy access and viewing, all the samples were converted from dcm to jpg format using pydicom and Pillow Python libraries.

- **Training**: This subfolder contains the codes for traing and testing the proposed CVAE-ViT hybrid model, along with three other benchmark models. The benchmark models were used to evaluate the effectiveness of the proposed method. First model uses the raw MRI images directly as ViT inputs, second model passes the latent space representations generated from the CVAE encoder into the ViT, third model uses reconstructed MRIs from the CVAE as ViT inputs, and the fourth model, which is the proposed method, feeds both latent space representations and reconstructed images from CVAE into the ViT. For better comparison, the CVAE was trained for 100 epochs and the ViT was trained for 400 epochs in all four models. The four models were evaluated and compared based on the following metrics:
  - Accuracy
  - Precision
  - Recall (Sensitivity)
  - F1-score
  - Specificity
  - Area Under the Receiver Operating Characteristic Curve (AUC-ROC)
  - Confusion Matrix


## Getting Started

### Prerequisites
Ensure you have the following software installed:
- Python 3.x
- Jupyter Notebook
- Required Python packages (see `requirements.txt`)

If you do not have Jupyter Notebook installed, you can set it up using Anaconda. Follow the instructions [here](https://docs.anaconda.com/anaconda/install/) to install Anaconda, which includes Jupyter Notebook.

### Installation
Clone the repository to your local machine:
```sh
git clone https://github.com/MShakiba-Research/CVAE-Vision-Transformer-for-Alzheimer-Detection.git
cd CVAE-Vision-Transformer-for-Alzheimer-Detection
```

### Setting Up the Environment
Create a virtual environment and install the required packages:
```sh
pip install -r requirements.txt
```

### Training
To train and test the models, open the Jupyter notebooks located in the src/Training folder and run the corresponding models. Several Python libraries including NumPy, Pandas and Matplotlib are used for further data preprocessing, analysis and visualization. The dataset is divided into train (70%), validation (15%) and test (15%) sets, and the model is trained using the training set. Following the training process, the model will output the results for all the performance metrics for the test dataset.