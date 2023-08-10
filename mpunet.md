#### Multiplanner UNet 

Here are the steps to install mpunet: 

**Step 1:** make an environemnt and activate it. 
```
conda create -n myenv python=3.7

conda activate myenv
```
**Step 2:** clone the git repo:
```
git clone https://github.com/sumit-ai-ml/MultiPlanarUNet.git
```
**Step 3:** install mpunet:
```
pip install -e MultiPlanarUNet
```
_**Now how to use ?**_ 

step 1: Data Preprocessing: 

The dataset should be devided into 3 parts like this:
```
./data_folder/
|- train/
|--- images/
|------ image1.nii.gz
|------ image5.nii.gz
|--- labels/
|------ image1.nii.gz
|------ image5.nii.gz
|- val/
|--- images/
|--- labels/
|- test/
|--- images/
|--- labels/
|- aug/ <-- OPTIONAL
|--- images/
|--- labels/

```
- _the name of image and mask should be same_
- the image format should be either .nii.gz or .nii
