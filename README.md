# Evalita 2026 Challenge GSI:Detect

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Jupyter](https://img.shields.io/badge/jupyter-FFFFFF?style=for-the-badge&logo=jupyter&logoColor=ffdd54)

> Implementation of a dual-stage NLP framework for the EVALITA 2026 GSI:detect task, integrating continuous intensity regression [0,1] and multi-class classification of gender stereotypes across social and behavioral dimensions.
<br>Challenge link: [GSI (Detecting Gender Stereotypes)](https://gsi-d-evalita.fbk.eu/participate)

## 📖 **Context**

This project was developed for the **Natural Language Processing** examination of Prof. **Roberto Pirrone**, during the **2025/2026** Academic Year at the **Università degli Studi di Palermo**, **Computer Engineering (LM-32, 2035)** course.

## 👥 **Authors**
_Andrea Spinelli - Gabriele Bova - Vincenzo Zizzo_

## 🛠️ **Technologies Used**

*   **Languages:** Python
*   **Other:** Git

## 🚀 **Installation and Startup**

To run this project, you will need Python and the required libraries. The setup involves creating an environment and running the analysis script.

### Prerequisites

*   **Python** 3.8 or higher.
*   **Required libraries**: indicated in the requirements.txt file
*   **Git** (to clone the repository).

### Instructions

**Important:**: All steps should be performed within a Python environment (e.g., Conda or venv) to ensure compatibility. The core logic of the project is contained within three sequential Jupyter Notebooks.

1. **Clone the Repository**
    Open your terminal or command prompt and clone the repository to your local machine.
    ```bash
    git clone https://github.com/A-rgonaut/LM-32_Evalita_2026_Challenge_GSI_Detect.git
    cd LM-32_Evalita_2026_Challenge_GSI_Detect
    ```

2. **Libraries**
    Install the required dependencies to run the notebooks and the models.
    ```bash
    pip install -r requirements.txt
    ```

3. **Data Preparation**
    Run the first notebook to handle data loading, cleaning, and initial exploration. This step ensures the EVALITA 2026 datasets are correctly formatted for the models.
    - pre_processing.ipynb

4. **Main Task: Regression**
    Execute this notebook to train and evaluate the model focused on quantifying the intensity of gender stereotypes. It outputs a continuous score in the range [0, 1].
    - maintask.ipynb

5. **Sub-task: Classification**
    Run the final notebook to perform the multi-class classification. This model categorizes detected stereotypes into specific classes (Role, Personality, Competence, Physical, Sexual, Relational).
    - subtask.ipynb

## ✨ **Key Features**

This project presents a comprehensive pipeline for Detecting Gender Stereotypes in Italian (GSI-D), leveraging the **EVALITA 2026** dataset. The methodology relies on a state-of-the-art Transformer-based architecture (`BERT`), applied distinctively to solve both regression and classification tasks through advanced Transfer Learning strategies.

1. **Advanced Social Media Preprocessing**
    * This module implements a robust cleaning pipeline specifically designed for raw social media text (Italian tweets/comments).
    * **Normalization**: It handles HTML entities, standardizes anomalous typographic symbols, and anonymizes user mentions (`@user`) and URLs to prevent bias.
    * **Emoji & OOV Analysis**: Includes a dedicated analysis of Out-Of-Vocabulary (OOV) tokens, extracting and preserving emojis (e.g., 🤡, 🤣) which are crucial for detecting sarcasm and implicit stereotypes in short texts.

2. **Stereotype Intensity Estimation (Regression - Main Task)**
    * This model quantifies the *intensity* of the stereotype (score 0-1) using a **Neural Regressor** built on top of `dbmdz/bert-base-italian-xxl-cased`.
    * **Custom Architecture**: Instead of using the standard `[CLS]` token, it implements a **Weighted Mean Pooling** strategy on the last hidden states to capture the semantic context of the entire sentence. The pooling output feeds into a custom fully-connected head with BatchNorm and Dropout.
    * **Hybrid Training Strategy**: The project utilizes `skorch` to perform a systematic Grid Search, comparing two paradigms: **Feature Extraction** (frozen BERT weights) vs. **Full Fine-Tuning** (end-to-end optimization), validating performance via Stratified K-Fold.

3. **Stereotype Categorization (Classification - Subtask)**
    * This module addresses the multi-class problem of identifying the specific type of stereotype (e.g., *role*, *body*, *intellect*).
    * **Imbalance Handling**: To tackle the highly unbalanced dataset, the loss function is weighted using **Inverse Class Frequencies** (`compute_class_weight`), forcing the model to pay more attention to minority classes.
    * **Evaluation & Explainability**: The pipeline includes a detailed error analysis using Confusion Matrices and per-class Precision/Recall metrics, allowing for a granular understanding of where the model confuses subtle stereotype categories.