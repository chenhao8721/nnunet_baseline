# nnunet_baseline
### How to install
Using Python 3.9  
cd nnUNet-baseline  
pip install -e .
### How to train a model
### 1.Preparing the dataset：
Datasets must be located in the `nnUNet_raw` folder (which you either define when installing nnU-Net or export/set every 
time you intend to run nnU-Net commands!).
Each segmentation dataset is stored as a separate 'Dataset'. Datasets are associated with a dataset ID, a three digit 
integer, and a dataset name (which you can freely choose): For example, Dataset001_autopet_501 has 'autopet_501' as dataset name and 
the dataset id is 1. Datasets are stored in the `nnUNet_raw` folder。  
Exactly the same as nnunet_v2, please refer to: https://github.com/MIC-DKFZ/nnUNet/blob/master/documentation/

### 2.Importing environment variables
Create three folders: nnUNet_preprocessed (to store processed data),  nnUNet_trained_models (to store trained models),  
and nnUNet_raw (to store the dataset).  

export nnUNet_preprocessed="nnUNet_preprocessed_directory"  
export nnUNet_results="nnUNet_trained_models_directory"  
export nnUNet_raw="nnUNet_raw_directory"
In this competition, the model is located in the following folder:nnUNet_trained_models/Dataset001_autopet_501
### 3.The training command
nnUNetv2_plan_and_preprocess -d 1 -c 3d_fullres -np 8  --verify_dataset_integrity && nnUNetv2_train  1 3d_fullres all.  
Where 1 is the task ID number。

## How to inference
nnUNetv2_predict -i imagesTs -o infer -d 1 -c 3d_fullres -f all  
Where 1 is the task ID number. 'imagesTs' stands for test data, and 'infer' is the inference folder.

