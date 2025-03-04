[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/fEFF99tU)
[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=17022589&assignment_repo_type=AssignmentRepo)

# Detection of Back-Transitions from H Mode to L Mode in a Tokamak

## Description

In a tokamak, plasma confinement modes describe different states of stability and energy retention. The two primary modes are Low (L) mode, characterized by lower confinement, and High (H) mode, where the plasma retains heat more effectively. Typically, a plasma discharge begins in L mode and may transition into H mode.

This project focuses on detecting the back-transition from H mode to L mode, a phenomenon where the plasma returns to a lower confinement state. The objective is to identify these transitions, analyze their characteristics, and provide insights into the conditions leading to these events.

---

## Requirements

To run this project, ensure that the following libraries and their specific versions are installed. You can install them using the provided `requirements.txt` file or manually as needed.

### Libraries and Versions

1. **Python Version**:  
   - **`python==3.8.18`**: This project is compatible with Python 3.8.

2. **Numerical Computation**:  
   - **`numpy==1.23.5`**: Essential for fast numerical operations, array manipulations, and mathematical computations.  
   - **`scipy==1.10.0`**: Provides advanced scientific computations and statistics.  

3. **Data Manipulation and Parallel Computing**:  
   - **`dask==2.12.0`**: Handles large datasets with parallelized computations.  
   - **`distributed==2.12.0`**: Enables distributed task scheduling for parallel processing.  

4. **Visualization**:  
   - **`matplotlib==3.7.2`**: Creates detailed plots and visualizations, including confusion matrices.  
   - **`seaborn==0.13.2`**: Enhances visualization with high-level statistical graphs.  

5. **Deep Learning**:  
   - **`torch==2.2.2`**: Core library for building and training neural networks with PyTorch.  
   - **`torchvision==0.17.2`**: Provides image datasets and pre-trained models for computer vision tasks.  
   - **`torchaudio==2.2.2`**: Offers utilities for working with audio data.  
   - **`tensorflow==2.12.0`**: Another deep learning framework used for advanced neural network training.  
   - **`keras==2.12.0`**: High-level deep learning API for building neural networks with TensorFlow.

6. **Hyperparameter Optimization**:  
   - **`optuna==4.1.0`**: Automated hyperparameter optimization for improving model performance.

7. **Machine Learning Metrics and Evaluation**:  
   - **`sklearn==1.2.2`**: Includes utilities for preprocessing, metrics, and classification models.

8. **Other Libraries**:  
   - **`xgboost==2.1.3`**: Boosted decision trees for tabular data classification tasks.  
   - **`ipywidgets==8.1.5`**: Provides interactive widgets for Jupyter notebooks.  
   - **`SQLAlchemy==2.0.36`**: Used for database interactions.  

### Installation Instructions

Run the following command to install all required libraries:

```bash
pip install -r requirements.txt
```
---

## Data Directory Requirement

This repository requires a folder named `3_4_LH_HL_data` to store the necessary data files. Due to the size of the data and to ensure the confidentiality of the lab's work, this folder is not included in the repository and is excluded from version control as specified in the [.gitignore](./.gitignore) file.  

To maintain confidentiality and avoid storage issues, **no data files should be pushed to the repository**. Please manually create the `3_4_LH_HL_data` folder in your local copy of the repository and ensure all data files remain untracked by Git.

---

## Data Division: Selected and Excluded Experiments

To ensure the quality and usability of our dataset, we divided the experiments into **selected** and **excluded** groups:

- **Excluded Experiments**:  
  A total of **35 experiments** were excluded as they lacked a significant number of features required for our models. Additionally, experiments missing **feature DML**, which is essential for our models, were also excluded.  

- **Selected Experiments**:  
  The remaining experiments with sufficient features were designated as **usable data** for training and evaluating our models.

In the future, experiments missing a small number of features could be included by applying imputation techniques to fill in the gaps using data from the rest of the dataset.

**Note**: The code provided in `data_exploration_features_selection` to perform this data division is only relevant if you have access to the raw dataset. It creates two separate folders:

- `selected_experiments/` for usable data.
- `excluded_experiments/` for non-usable data.

For confidentiality reasons, the dataset itself (`3_4_LH_HL_data/`) cannot be provided. Please refer to the [Data Directory Requirement](#data-directory-requirement) section for details on setting up your local environment.

---

## Features

This project includes a preprocessing function for handling plasma shot data to ensure
clean and standardized input for analysis.

### Feature Sets

- Two predefined feature combinations are available for flexibility:
  - **features1**: Includes plasma-related parameters such as `Wtot`, `DML`, `FIR_LIDs`, `IPLA` and density/temperature profiles (`Te_rho_z1` to `Te_rho_z67` and `Ne_rho_z1` to `Ne_rho_z67`).
  - **features2**: Includes plasma-related parameters such as `Wtot`, `DML`, `FIR_LIDs`, `IP` and density/temperature profiles (`Te_rho_z1` to `Te_rho_z67` and `Ne_rho_z1` to `Ne_rho_z67`).
- FFT Option for `Halpha13` that allows optional Fast Fourier Transform (FFT) of the `Halpha13` signal for frequency-domain analysis and replaces the original `Halpha13` with its **FFT** components.

#### Time Window and Steps Customization

- It is possible to **customize the time window (`tw`)** and **number of steps** used for the model training and evaluation.  
- These parameters are detailed in the corresponding model notebooks:
  - **`BI_LSTM.ipynb`**
  - **`UNI_LSTM.ipynb`**

You can adjust the time window to test the model's sensitivity and test how it impacts the results.

### Data Cleaning and Interpolation

Linear interpolation is performed to fill missing values.
`dropna` is applied to remove any remaining incomplete rows.

### Absolute Value Transformation

IP and IPLA features are transformed to ensure all values are non-negative.

### Time Column Handling

Missing values in the time column are filled using forward and backward filling.

---

## Files and Directory Structure

Below is the structure of the project, with directories and files described:

```plaintext
📂 3_4_LH_HL_data/                            # Directory containing raw data files for LH-HL transitions.
📂 features_PCA/                              # Contains results from PCA feature selection.
📂 models/                                    # Saved trained models.
📂 plots/                                     # General directory for plots generated during analysis.
📂 plots_results/                             # Confusion matrices and other result-specific visualizations.

📄 .gitignore                                 # Files/directories excluded from git tracking.
📄 4_HL_prediction.ipynb                      # First notebook provided to understand how to open, visualize, 
                                              and explore the data.  
📄 BI_LSTM.ipynb                              # Notebook containing the final implementation of BI-LSTM.
📄 BI_LSTM_preproccesed.ipynb                 # BI-LSTM with preprocessed data.
📄 data_exploration_features_selection.ipynb  # Data exploration and feature selection analysis.
📄 data_exploration.ipynb                     # Initial data exploration notebook.
📄 DigitalEthicsCanvas2024.pdf                # Digital ethics considerations for the project.
📄 HL_times_sel.json                          # HL transition times for selected shots.
📄 HL_times.json                              # HL transition times for all shots.
📄 model_results.md                           # Markdown file summarizing model results.
📄 preprocessing_functions.py                 # Python script with preprocessing functions.
📄 preprocessing.ipynb                        # Notebook for data preprocessing steps.
📄 requirements.txt                           # List of all required libraries and versions.
📄 summary_feature_sel.md                     # Summary of feature selection process.
📄 UNI_LSTM.ipynb                             # Notebook for training and evaluating the UNI-LSTM model.
```

**Note**: For confidentiality reasons, we cannot provide the contents of the `3_4_LH_HL_data/` directory.  

---

## Results

To summarize our different results, the table below presents the performance of our two models  
(BI_LSTM and UNI_LSTM) on the test set using various combinations of features (`features0` and `features1` as mentioned in [Feature Sets section](#feature-sets)) and preprocessing options (with or without FFT).

| **Model**        | **Features Combination** | **FFT Applied** | **F1 Score** |
|-------------------|--------------------------|-----------------|-------------|
| **BI_LSTM**      | Features 0               | No              | 0.7163      |
| **BI_LSTM**      | Features 0               | Yes             | 0.6547      |
| **BI_LSTM**      | Features 1               | No              | 0.5928      |
| **BI_LSTM**      | Features 1               | Yes             | 0.6634      |
| **UNI_LSTM**     | Features 0               | No              | 0.5699      |
| **UNI_LSTM**     | Features 0               | Yes             | 0.5145      |
| **UNI_LSTM**     | Features 1               | No              | 0.5631      |
| **UNI_LSTM**     | Features 1               | Yes             | 0.4828      |

### Observations

1. **BI_LSTM** achieved its best performance with `features0` and no FFT, yielding an **F1 Score of 0.7163**.  
2. **UNI_LSTM** had its highest F1 score (**0.5699**) using `features0` without FFT.  
3. The application of FFT generally led to a decrease in F1 score for both models.  

---

## Acknowledgments

We would like to express our gratitude to:

- **Alessandro Pau** for giving us the opportunity to work in this lab and gain valuable experience.

The PhD students for their support in helping us understand the data, preprocess it effectively and build our models:

- **Svantner Jean-Pierre Thomas**
- **Cristina Venturini**
- **Yoeri Poels**

We greatly appreciate their time, expertise and guidance throughout this project. :)

---

## Digital Ethics

We performed an Ethical Risk Assessment using the [Digital Ethics Canvas](https://www.epfl.ch/education/educational-initiatives/cede/training-and-support/digital-ethics/a-visual-tool-for-assessing-ethical-risks/the-digital-ethics-canvas-how-to/), a risk assessment grid with a series of questions that guide you in the analysis of software-specific ethical risks. The risks and mitigations that we identified with the guide of the canvas can be found in the file [DigitalEthicsCanvas2024.pdf](./DigitalEthicsCanvas2024.pdf), and the analysis of the risk of interpretability is exposed in the report.

