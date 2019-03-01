# art2photo
art2photo utilizes CycleGAN to generate artistic drawing from a real photo and vice versa. The arts images are from Wikiart and the real photos are from Flickr with landscape tags.

![epoch007_real_A.png](https://github.com/mingir2/art2photo_model/blob/master/art2photo_cyclegan/web/images/epoch007_real_A.png)
![epoch007_real_B.png](https://github.com/mingir2/art2photo_model/blob/master/art2photo_cyclegan/web/images/epoch007_real_B.png)

![epoch007_fake_B.png](https://github.com/mingir2/art2photo_model/blob/master/art2photo_cyclegan/web/images/epoch007_fake_B.png)
![epoch007_fake_A.png](https://github.com/mingir2/art2photo_model/blob/master/art2photo_cyclegan/web/images/epoch007_fake_A.png)

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
