# Transformer

## Contents
  - [Dataset](#Dataset)
  - [Train](#Train)
  - [Test](#Test)

### Dataset

* CVUSA：[https://github.com/viibridges/crossnet](https://github.com/viibridges/crossnet)
* CVACT：[https://github.com/Liumouliu/OriCNN](https://github.com/Liumouliu/OriCNN)

### Models

Pretrained model Download (Google's Official Checkpoint)

* R50+ViT-B_16 [pretrained model](https://console.cloud.google.com/storage/browser/vit_models/imagenet21k;tab=objects?pageState=(%22StorageObjectListTable%22:(%22f%22:%22%255B%255D%22))&prefix=&forceOnObjectsSortingFiltering=false)

Our trained models for CVUSA and CVACT will be available soon

* [Trained models]()

### Train
* CVUSA

```
python train.py --name CVUSA --dataset CVUSA --pretrained_dir YOUR_PRETRAINED_MODEL --output_dir MODEL_WHERE_WILL_BE_SAVE --dataset_dir YOUR_DATASET_PATH --learning_rate 1e-4 --weight_decay 0.03
```

* CVACT

```
python train.py --name CVACT --dataset CVACT --pretrained_dir YOUR_PRETRAINED_MODEL --output_dir MODEL_WHERE_WILL_BE_SAVE --dataset_dir YOUR_DATASET_PATH --learning_rate 1e-4 --weight_decay 0.03
```

### Test
* CVUSA

```
python test.py --name CVUSA --dataset CVUSA --output_dir MODEL_WHERE_WILL_BE_SAVE --dataset_dir YOUR_DATASET_PATH
```

* CVACT

```
python test.py --name CVACT --dataset CVACT --output_dir MODEL_WHERE_WILL_BE_SAVE --dataset_dir YOUR_DATASET_PATH
```