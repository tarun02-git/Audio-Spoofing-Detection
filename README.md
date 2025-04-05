# Audio-Spoofing-Detection
This document outlines the research, implementation, and analysis for an audio deepfake detection system, addressing the requirements and detecting the spoofs.

 **INSTALLATION**
 
First, clone the repository locally, create and activate a conda environment, and install the requirements :

$ git clone 
$ conda create --name rawnet_anti_spoofing python=3.13.0
$ conda activate rawnet_anti_spoofing
$ conda install pytorch
$ pip install torch numpy soundfile joblib tensorboardX pyyaml

For installing requirements, please refer requiremnets.txt and manually install all the dependencies according to your system versions.

**IMPLEMENTATION**

**DATASET:** 

USED IS ASV-SPOOF2019(LA).

Download and extract all the files in your system.

First set up for your dataset using **dataset_util.py** which defines the custom py torch dataset.

* **Database Path:** Configure the '--database_path' argument in 'main.py' to point to the root directory of your ASVspoof 2019 LA dataset.

* **Protocols Path:** Configure the '--protocols_path' argument in 'main.py' to point to the directory containing the protocol files.

**FOR TRAINING**

Refer main.py , model.py and testing.py or copy paste the provided code in your system.

**Testing**

To test your own model on the ASVspoof 2019 LA evaluation set:

python main.py --track=logical --loss=CCE --is_eval --eval --model_path='/path/to/your/your_best_model.pth' --eval_output='eval_CM_scores.txt'

If you would like to compute scores on the development set of ASVspoof 2019 simply run:

python main.py --track=logical --loss=CCE --eval --model_path='/path/to/your/best_model.pth' --eval_output='dev_CM_scores.txt'

**Arguments:**

--eval: Enables evaluation mode.
--model_path: Path to the model checkpoint.
--eval_output: Path to save the evaluation results.

**Model Configuration**

The model architecture is configured in the model_config_RawNet2.yaml file. You can modify the parameters in this file to experiment with different model configurations.

**Code Description**

dataset_util.py: Defines a custom PyTorch Dataset class (ASVDataset) for loading and processing the ASVspoof 2019 LA dataset.

model.py: Implements the RawNet model architecture, including Sinc convolutions, residual blocks, GRUs, and attention mechanisms.

train.py: Implements the training and evaluation pipeline, including data loading, model training, evaluation, and logging.

model_config_RawNet2.yaml: Contains the configuration parameters for the RawNet model.

**Implementation Details**

RawNet Architecture: The model uses Sinc convolutions for initial feature extraction, followed by residual blocks, GRUs, and attention mechanisms for further feature learning and classification.

Data Preprocessing: Audio sequences are padded to a fixed length and converted to PyTorch tensors.

Training: The model is trained using the Adam optimizer and cross-entropy loss with class weights to handle class imbalance (Rawnet).

Evaluation: The evaluation script generates an evaluation file in the format expected by the ASVspoof evaluation scripts.

**Results**

The training and evaluation results are logged using TensorBoardX and saved to the specified output files.

**Contact**

For any query regarding this repository, please contact:
Tarun Agarwal.
Tarun112agarwal@gmail.com

