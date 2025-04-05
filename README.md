# Audio-Spoofing-Detection

This project implements an audio deepfake detection system, addressing the requirements and detecting audio spoofs.

## Installation

To set up the project:

1.  **Clone the repository:**

    ```bash
    git clone [https://github.com/tarun02-git/Audio-Spoofing-Detection.git](https://github.com/tarun02-git/Audio-Spoofing-Detection.git)
    ```

2.  **Create and activate a conda environment (Recommended):**

    ```bash
    conda create --name rawnet_anti_spoofing python=3.13.0
    conda activate rawnet_anti_spoofing
    ```

3.  **Install PyTorch:**

    ```bash
    conda install pytorch
    ```

4.  **Install other dependencies:**

    ```bash
    pip install torch numpy soundfile joblib tensorboardX pyyaml
    ```

    * Alternatively, please refer to `requirements.txt` and manually install all dependencies according to your system versions.

## Implementation

### Dataset

* **Used Dataset:** ASVspoof 2019 (LA)

* Download and extract all the files in your system.

* **Dataset Setup:**

    * Set up your dataset using `dataset_util.py`, which defines the custom PyTorch dataset.

    * **Database Path:** Configure the `--database_path` argument in `main.py` to point to the root directory of your ASVspoof 2019 LA dataset.

    * **Protocols Path:** Configure the `--protocols_path` argument in `main.py` to point to the directory containing the protocol files.

### Training

* Refer to `main.py`, `model.py`, and `testing.py` for the training implementation. You can either use these files directly or copy and paste the provided code into your system.

## Testing

To test your model on the ASVspoof 2019 LA evaluation set:

```bash
python main.py --track=logical --loss=CCE --is_eval --eval --model_path='/path/to/your/your_best_model.pth' --eval_output='eval_CM_scores.txt'

Markdown

# Audio-Spoofing-Detection

This project implements an audio deepfake detection system, addressing the requirements and detecting audio spoofs.

## Installation

To set up the project:

1.  **Clone the repository:**

    ```bash
    git clone [https://github.com/tarun02-git/Audio-Spoofing-Detection.git](https://github.com/tarun02-git/Audio-Spoofing-Detection.git)
    ```

2.  **Create and activate a conda environment (Recommended):**

    ```bash
    conda create --name rawnet_anti_spoofing python=3.13.0
    conda activate rawnet_anti_spoofing
    ```

3.  **Install PyTorch:**

    ```bash
    conda install pytorch
    ```

4.  **Install other dependencies:**

    ```bash
    pip install torch numpy soundfile joblib tensorboardX pyyaml
    ```

    * Alternatively, please refer to `requirements.txt` and manually install all dependencies according to your system versions.

## Implementation

### Dataset

* **Used Dataset:** ASVspoof 2019 (LA)

* Download and extract all the files in your system.

* **Dataset Setup:**

    * Set up your dataset using `dataset_util.py`, which defines the custom PyTorch dataset.

    * **Database Path:** Configure the `--database_path` argument in `main.py` to point to the root directory of your ASVspoof 2019 LA dataset.

    * **Protocols Path:** Configure the `--protocols_path` argument in `main.py` to point to the directory containing the protocol files.

### Training

* Refer to `main.py`, `model.py`, and `testing.py` for the training implementation. You can either use these files directly or copy and paste the provided code into your system.

## Testing

To test your model on the ASVspoof 2019 LA evaluation set:

```bash
python main.py --track=logical --loss=CCE --is_eval --eval --model_path='/path/to/your/your_best_model.pth' --eval_output='eval_CM_scores.txt'
To compute scores on the development set of ASVspoof 2019:

Bash

python main.py --track=logical --loss=CCE --eval --model_path='/path/to/your/best_model.pth' --eval_output='dev_CM_scores.txt'


## Arguments

--eval: Enables evaluation mode.

--model_path: Path to the model checkpoint.

--eval_output: Path to save the evaluation results.

## Model Configuration


The model architecture is configured in the model_config_RawNet2.yaml file. You can modify the parameters in this file to experiment with different model configurations.

## Code Description


dataset_util.py: Defines a custom PyTorch Dataset class (ASVDataset) for loading and processing the ASVspoof 2019 LA dataset.

model.py: Implements the RawNet model architecture, including Sinc convolutions, residual blocks, GRUs, and attention mechanisms.

train.py: Implements the training and evaluation pipeline, including data loading, model training, evaluation, and logging.

model_config_RawNet2.yaml: Contains the configuration parameters for the RawNet model.

Implementation Details

**RawNet Architecture:**

 The model uses Sinc convolutions for initial feature extraction, followed by residual blocks, GRUs, and attention mechanisms for further feature learning and classification.

**Data Preprocessing:**

 Audio sequences are padded to a fixed length and converted to PyTorch tensors.

**Training:**

 The model is trained using the Adam optimizer and cross-entropy loss with class weights to handle class imbalance (RawNet).

**Evaluation:**

 The evaluation script generates an evaluation file in the format expected by the ASVspoof evaluation scripts.

## Results

The training and evaluation results are logged using TensorBoardX and saved to the specified output files.

## Contact

For any query regarding this repository, please contact:

Tarun Agarwal

Tarun112agarwal@gmail.com
