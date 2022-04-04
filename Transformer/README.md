# Transformer

### Dataset

* CVUSA：[https://github.com/viibridges/crossnet](https://github.com/viibridges/crossnet)
* CVACT：[https://github.com/Liumouliu/OriCNN](https://github.com/Liumouliu/OriCNN)

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