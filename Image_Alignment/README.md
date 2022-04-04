# Image Alignment

## Contents
  - [Dataset](#Dataset)
  - [Dependencies](#Dependencies)
  - [Semantic Segmentation](#Semantic-Segmentation)
  - [Mixed Perspective-Polar Mapping](#Mixed-Perspective-Polar-Mapping)
  - [Dual Conditional Generative Adversarial Nets](#Dual-Conditional-Generative-Adversarial-Nets)
  - [Evaluation](#Evaluation)
  - [Acknowledgments](#Acknowledgments)

## Dataset

* CVUSA：[https://github.com/viibridges/crossnet](https://github.com/viibridges/crossnet)
* CVACT：[https://github.com/Liumouliu/OriCNN](https://github.com/Liumouliu/OriCNN)

## Dependencies
This code requires PyTorch 1.0.0 and python 3.6.9+. 

Please install dependencies by
```
pip install -r requirements.txt (for pip users)
```

## Semantic Segmentation
After unzipping the dataset, we adopt [RefineNet](https://github.com/guosheng/refinenet) trained on CityScapes dataset for generating semantic maps and use them as training data in our experiments.

Please download the dataset CVUSA after semantic segmentation from google drive: [Training sample set for ablation study](https://drive.google.com/file/d/1KGAEbWL3q9Fi5axzaf_CROp92KZ_PVjS/view?usp=sharing), [Test sample set](https://drive.google.com/file/d/1_BZ1D5Jw0CFjLlPXRURhRRWJLms_M3Ho/view?usp=sharing).

## Mixed Perspective-Polar Mapping

Go to the [data](https://github.com/TianXiaoYang-UESTC/SMDT-PyTorch/tree/main/Image_Alignment/data) folder.

Run `python data_prearation.py`.

## Dual Conditional Generative Adversarial Nets

### Models

Download the model trained from [pretrained model](https://drive.google.com/file/d/1-ChbRTJ-we8xVkhiPoMza08VZ0Ik0UPm/view?usp=sharing). 
Unzip the file to checkpoints/

Our trained models for CVUSA and CVACT will be available soon. [Trained models]()


### Train
* CVUSA

```
python train.py
--dataroot YOUR_DATASET_PATH --name SMDT_CVUSA --model SMDT --netG unet_afl_v5 --netD fpd --ngf 64 --ndf 64 --norm instance --direction AtoB --lambda_L1 100 --lambda_L1_seg 100 --dataset_mode panoaligned --preprocess none --gan_mode vanilla --gpu_ids 3 --batch_size 1 --niter 15 --niter_decay 15 --save_epoch_freq 15 --display_id 1 --display_port 8097 --display_ncols 0 --display_freq 20 --display_winsize 1024 --loop_count 1 --alpha 0.5 0.5 0.5 0.5 0.5 --verbose
```

* CVACT

```
python train.py
--dataroot YOUR_DATASET_PATH --name SMDT_CVACT --model SMDT --netG unet_afl_v5 --netD fpd --ngf 64 --ndf 64 --norm instance --direction AtoB --lambda_L1 100 --lambda_L1_seg 100 --dataset_mode panoaligned --preprocess none --gan_mode vanilla --gpu_ids 3 --batch_size 1 --niter 15 --niter_decay 15 --save_epoch_freq 15 --display_id 1 --display_port 8097 --display_ncols 0 --display_freq 20 --display_winsize 1024 --loop_count 1 --alpha 0.5 0.5 0.5 0.5 0.5 --verbose
```

### Test
* CVUSA

```
python test.py --dataroot YOUR_DATASET_PATH --results_dir RESULTS_WHERE_WILL_BE_SAVE --name SMDT_CVUSA --model SMDT --netG unet_afl_v5 --netD fpd --ngf 64 --ndf 64 --direction AtoB --epoch latest --dataset_mode panoaligned --norm instance --preprocess none --num_test 10000000 --eval --loop_count 1 --alpha 0.5 0.5 0.5 0.5 0.5 --gpu_ids 3
```

* CVACT

```
python test.py --dataroot YOUR_DATASET_PATH --results_dir RESULTS_WHERE_WILL_BE_SAVE --name SMDT_CVACT --model SMDT --netG unet_afl_v5 --netD fpd --ngf 64 --ndf 64 --direction AtoB --epoch latest --dataset_mode panoaligned --norm instance --preprocess none --num_test 10000000 --eval --loop_count 1 --alpha 0.5 0.5 0.5 0.5 0.5 --gpu_ids 3
```

## Evaluation
We adopt Prediction Accuracy, Inception Score, KL Score, SSIM, PSNR, and SD for evaluation of all the involved methods. Please refer to [Evaluation](https://github.com/TianXiaoYang-UESTC/SMDT-PyTorch/tree/main/Image_Alignment/evaluation) for more details.

## Acknowledgment
This source code of Semantic Segmentation is by [RefineNet](https://github.com/guosheng/refinenet).
