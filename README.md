# CartoonGAN-Test-Pytorch-Torch
Pytorch and Torch testing code of [CartoonGAN](http://openaccess.thecvf.com/content_cvpr_2018/CameraReady/2205.pdf) `[Chen et al., CVPR18]`. With the released pretrained [models](http://cg.cs.tsinghua.edu.cn/people/~Yongjin/Yongjin.htm) by the authors, I made these simple scripts for a quick test.

## Getting started

- Unix-based OS
- NVIDIA GPU (optional, can bypass with `--gpu -1` option)


1. Run `pip install -r requirements.txt`
2. Create a `test_img` dir to put input files and a `test_output` dir for output files.

## Pytorch

The original pretrained models are Torch `nngraph` models, which cannot be loaded in Pytorch through `load_lua`. So I manually copy the weights (bias) layer by layer and convert them to `.pth` models. 

- Download the converted models:

```
sh pretrained_model/download_pth.sh
```

- For testing:

```
python test.py --input_dir YourImgDir --style Hosoda --gpu 0
```

## Torch

Working with the original models in Torch is also fine. I just convert the weights (bias) in their models from CudaTensor to FloatTensor so that `cudnn` is not required for loading models.

- Download the converted models:

```
sh pretrained_model/download_t7.sh
```

- For testing:

```
th test.lua -input_dir YourImgDir -style Hosoda -gpu 0
```

## Note

- The training code should be similar to the popular GAN-based image-translation frameworks and thus is not included here.

## Acknowledgement

- Many thanks to the authors for this cool work.

- Part of the codes are borrowed from [DCGAN](https://github.com/soumith/dcgan.torch), [TextureNet](https://github.com/DmitryUlyanov/texture_nets), [AdaIN](https://github.com/xunhuang1995/AdaIN-style) and [CycleGAN](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix).

