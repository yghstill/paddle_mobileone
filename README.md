# paddle_reparameterization
PaddlePaddle implementation of Re-parameterization. This repo is built on the basis of [PaddleClas](https://github.com/PaddlePaddle/PaddleClas) framework.

## Benchmark

| Model | Acc Top1 | Download |
| ----- | -------- | -------- |
| MobileOne-S0 | 70.30 | [Link](https://pan.baidu.com/s/1c6mhRyVKiLrf4H4lbwpS-g)  extract:`3him` |

- MobileOne refers to the [paper](https://arxiv.org/abs/2206.04040)

## Prepare

- Install dependencies
```
pip install -r requirements.txt
```

- Prepare Dataset

Download [ImageNet1k](http://www.image-net.org/challenges/LSVRC/2012/)

## Training
- Single card training
```
python train.py -c  configs/MobileOne/MobileOne.yaml
```

- Distributed multi-card training
```
CUDA_VISIBLE_DEVICES=0,1,2,3 python3.7 -m paddle.distributed.launch --log_dir=log --gpus 0,1,2,3 tools/train.py -c configs/MobileOne/MobileOne.yaml
```
## Evaluation

```
python eval.py -c  configs/MobileOne/MobileOne.yaml
```

## Export

```
python3.7 export_model.py -c configs/MobileOne/MobileOne_S0.yaml -o Global.pretrained_model=mobileone_s0 -o Global.save_inference_dir=outpu
```
