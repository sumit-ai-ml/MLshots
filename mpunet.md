#### Multiplanner UNet 

Multiplanner UNet is an advanced version of UNet for 3d medical image segmentation, that is amazing librarty is created by: Mathias Perslev, Erik Dam, Akshay Pai, and Christian Igel. if you want to know more about this, please take : https://doi.org/10.1007/978-3-030-32245-8_4

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

**step 1: Data Preprocessing:** 

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
_**Please Note:**_
- The **name** of image and mask should be same. 
- The image and mask format should be either ```.nii.gz or .nii```
- Also make sure Images should be arrays of dimension 4 with the first 3 corresponding to the image dimensions and the last the channels dimension (e.g. [256, 256, 256, 3] for a 256x256x256 image with 3 channels).
- Label maps should be identically shaped in the first 3 dimensions and have a single channel (e.g. [256, 256, 256, 1])

**Step 3: Initialize the project:**
- Make sure you are in the same directory in which the ```data_folder``` directory is, then run this command:

  ```mp init_project --name my_project --data_dir ./data_folder```
  
- ```init_project``` prepares a Multi-Planar model. However, note that a 3D model is also supported, which can be selected by specifying the --model=3D flag (default=---model=MultiPlanar).

**Step 3: Training:**
- After running above command you will see the another directory with ```data_folder``` named: ```my_project```. Now run this command to inside the ```my_project``` folder to intialize the training:

  ```mp train --num_GPUs=2   # Any number of GPUs (or 0)```

- After this completes run this command:

  ```mp train_fusion --num_GPUs=2```

- The trained model can now be evaluated on the testing data in data_folder/test by invoking:

  ```mp predict --num_GPUs=2 --out_dir predictions```

 
