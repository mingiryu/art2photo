# art2photo
art2photo utilizes CycleGAN to generate artistic images from a real photos and vice versa. The arts are from Wikiart and the pictures are from Flickr with landscape tags.

![epoch007_real_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch007_real_A.png)
![epoch007_real_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch007_real_B.png)

![epoch007_fake_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch007_fake_B.png)
![epoch007_fake_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch007_fake_A.png)

## Setting up Google Cloud Platform
1. Create a new project and add a VM instance of "Deep Learning VM".
2. Request increase in quotas for "GPUs (all regions)" to at least 1. Quotas can be found in "IAM & admin". 
3. Select (2vCPUs, 13 GB memory), (1 x NVIDIA Tesla K80), (30GB SSD persistent disk)
4. Checkbox "Allow HTTP traffic" and "Allow HTTPS traffic" for Visdom server.
5. Optionally, add Firewall rule with "tcp:8097" and convert IP address to static. These options can be found in "VPC network".

## Procedure
- SSH into the VM through gcloud
```
gcloud compute ssh --project art2photo --zone us-west1-b pytorch-vm -- -L 8080:localhost:8080
```
-  Update system
```
sudo apt update && apt upgrade
```
- Clone CycleGAN
```
git clone https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix
```
- Install repository requirements
```
pip install -r requirements --user
```
- Install Visdom
```
pip install visdom --user
```
- Run Visdom server in the background
```
nohup python -m visdom.server
```
- Download datasets
```
bash ./datasets/download_cyclegan_dataset.sh datasets
```
- Start training
```
python3 train.py --dataroot ./datasets/art2photo/ --name art2photo_cyclegan --model cycle_gan --gpu_ids 0 --batch_size 4
```
- Continue training
```
python3 train.py --dataroot ./datasets/art2photo/ --name art2photo_cyclegan --model cycle_gan --gpu_ids 0 --batch_size 4 --continue_train
```

## Training (2 Weeks)

![newplot](https://github.com/mingir2/art2photo/blob/master/newplot.png)

|||
|---|---|
|Real_A|Real_B|
|Fake_B|Fake_A|

### Epoch 001

![epoch001_real_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch001_real_A.png)
![epoch001_real_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch001_real_B.png)

![epoch001_fake_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch001_fake_B.png)
![epoch001_fake_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch001_fake_A.png)

### Epoch 005

![epoch005_real_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch005_real_A.png)
![epoch005_real_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch005_real_B.png)

![epoch005_fake_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch005_fake_B.png)
![epoch005_fake_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch005_fake_A.png)

### Epoch 010

![epoch010_real_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch010_real_A.png)
![epoch010_real_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch010_real_B.png)

![epoch010_fake_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch010_fake_B.png)
![epoch010_fake_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch010_fake_A.png)

### Epoch 015

![epoch015_real_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch015_real_A.png)
![epoch015_real_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch015_real_B.png)

![epoch015_fake_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch015_fake_B.png)
![epoch015_fake_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch015_fake_A.png)

### Epoch 020

![epoch020_real_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch020_real_A.png)
![epoch020_real_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch020_real_B.png)

![epoch020_fake_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch020_fake_B.png)
![epoch020_fake_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch020_fake_A.png)

### Epoch 025

![epoch025_real_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch025_real_A.png)
![epoch025_real_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch025_real_B.png)

![epoch025_fake_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch025_fake_B.png)
![epoch025_fake_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch025_fake_A.png)

### Epoch 035

![epoch035_real_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch035_real_A.png)
![epoch035_real_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch035_real_B.png)

![epoch035_fake_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch035_fake_B.png)
![epoch035_fake_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch035_fake_A.png)

### Epoch 040

![epoch040_real_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch040_real_A.png)
![epoch040_real_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch040_real_B.png)

![epoch040_fake_B.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch040_fake_B.png)
![epoch040_fake_A.png](https://github.com/mingir2/art2photo/blob/master/art2photo_cyclegan/web/images/epoch040_fake_A.png)
