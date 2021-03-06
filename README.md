# Swin-Unet
In this work swin-net transformer is used for sementic segmentation of Polyp Dataset for Computer Aided Gastrointestinal Disease Detection.
The data set can be downloaded from the link given below 
```
https://datasets.simula.no/kvasir-seg/
```
The rest of the repo. is divided as follows
1. Requirements
2.  Data Prepration
3. Traning and Inference 
4. Results 

## Requirements
The main library requirements for this projects are as follows 
* **Tensorflow**
* **Matplotlib**
* **Opencv**

The complete requirements can be installed using the following set of commands 

```
cd Swin-unet/
conda create  -n <environment -name> python==3.7.4
conda activate <environment-name>
pip install -r requirements.txt
```
## Data Prepration 
Download the data from * "https://datasets.simula.no/kvasir-seg/" and extract the data folder. Make a folder name "data" inside Swin-unet folder and copy images and mask from kvasir-seg folder inside data folder then run the following commands.
```
python preprocess.py

```
This code  will preprocess data and convert it in to png mask folder with the name " masks_png".
## Training and Inferene 
This work genrates a swin-unet model from scratch. However, it can save checkpoint, resume traning , test on data and perform infrence on a dataset.
Please follow the following set of commands 

### Train
```
python Swin_UNET_128.py  --data=<data set path>--class=< number of classes>  --inps= < Train, test, Resume>  --b_s=< batch size> --e=< Epoch> --p= < patience>  --model_dir= < Check_Point>
Example Command
python Swin_UNET_128.py  --data=./data --class=2 --inps=train --b_s=16 --e=10 --p=10 --model_dir='./checkpoint/'



```
### Test
```
python Swin_UNET_128.py  --data=<data> --class=< number of classes>  --inps= < train, test, resume> --model_dir='./checkpoint/'
Example Command
python Swin_UNET_128.py  --data=./data --class=2 --inps=test --model_dir='./checkpoint/'

```
### Resume 
```
python Swin_UNET_128.py  --data=<data set path>--class=< number of classes>  --inps= < Train, test, Resume>  --b_s=< batch size> --e=< Epoch> --p= < patience>  --model_dir= < Check_Point>

Example Command

python Swin_UNET_128.py  --data=./data --class=2 --inps=resume --b_s=16 --e=10 --p=10 --model_dir='./checkpoint/'

```
### Infer
```
python Swin_UNET_128.py  --data=< data for infrence > --class=2 --inps=< test, train, resume, infer> --model_dir=< checkp point>

python Swin_UNET_128.py  --data=./data --class=2 --inps=infer --model_dir='./checkpoint/'

```



## Results
The prediction accuracy, latency , Flops, size on disk and the number  of parameter are shown in the following table 
| Model         | Parameters | Accuracy | Latency(sec)   | Size on Disk (MB)| Flops |
|---------------|-------------|----------|----------------|------------------|-------|
| Swin-unet     | 3,783,510   | 0.836    |  0.0004        |        38.89     |0.681 G|


The visual results of this work are shown in the following figure where first column shows the  ground truth sample images. The second coulmn shows their respective predictions . The third coulmn shows the error. between the predicted and the ground truth. 
![Alt text](./Results.png?raw=true "Title")

