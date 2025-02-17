# ESRGAN (ECCVW'2018)

> [ESRGAN: Enhanced Super-Resolution Generative Adversarial Networks](https://arxiv.org/abs/1809.00219)

> **Task**: Image Super-Resolution

<!-- [ALGORITHM] -->

## Abstract

<!-- [ABSTRACT] -->

The Super-Resolution Generative Adversarial Network (SRGAN) is a seminal work that is capable of generating realistic textures during single image super-resolution. However, the hallucinated details are often accompanied with unpleasant artifacts. To further enhance the visual quality, we thoroughly study three key components of SRGAN - network architecture, adversarial loss and perceptual loss, and improve each of them to derive an Enhanced SRGAN (ESRGAN). In particular, we introduce the Residual-in-Residual Dense Block (RRDB) without batch normalization as the basic network building unit. Moreover, we borrow the idea from relativistic GAN to let the discriminator predict relative realness instead of the absolute value. Finally, we improve the perceptual loss by using the features before activation, which could provide stronger supervision for brightness consistency and texture recovery. Benefiting from these improvements, the proposed ESRGAN achieves consistently better visual quality with more realistic and natural textures than SRGAN and won the first place in the PIRM2018-SR Challenge.

<!-- [IMAGE] -->

<div align=center >
 <img src="https://user-images.githubusercontent.com/7676947/144018578-6bb10830-b5fd-4d14-984e-4d7d85965c20.png" width="400"/>
</div >

## Results and models

Evaluated on RGB channels, `scale` pixels in each border are cropped before evaluation.
The metrics are `PSNR / SSIM` .

|                                      Model                                      | Dataset |  PSNR   |  SSIM  | Training Resources |                                      Download                                       |
| :-----------------------------------------------------------------------------: | :-----: | :-----: | :----: | :----------------: | :---------------------------------------------------------------------------------: |
| [esrgan_psnr_x4c64b23g32_1x16_1000k_div2k](./esrgan_psnr-x4c64b23g32_1xb16-1000k_div2k.py) |  Set5   | 30.6428 | 0.8559 |         1          | [model](https://download.openmmlab.com/mmediting/restorers/esrgan/esrgan_psnr_x4c64b23g32_1x16_1000k_div2k_20200420-bf5c993c.pth) |
| [esrgan_psnr_x4c64b23g32_1x16_1000k_div2k](./esrgan_psnr-x4c64b23g32_1xb16-1000k_div2k.py) |  Set14  | 27.0543 | 0.7447 |         1          | [model](https://download.openmmlab.com/mmediting/restorers/esrgan/esrgan_psnr_x4c64b23g32_1x16_1000k_div2k_20200420-bf5c993c.pth) |
| [esrgan_psnr_x4c64b23g32_1x16_1000k_div2k](./esrgan_psnr-x4c64b23g32_1xb16-1000k_div2k.py) |  DIV2K  | 29.3354 | 0.8263 |         1          | [model](https://download.openmmlab.com/mmediting/restorers/esrgan/esrgan_psnr_x4c64b23g32_1x16_1000k_div2k_20200420-bf5c993c.pth) |
| [esrgan_x4c64b23g32_1x16_400k_div2k](./esrgan_x4c64b23g32_1xb16-400k_div2k.py)  |  Set5   | 28.2700 | 0.7778 |         1          | [model](https://download.openmmlab.com/mmediting/restorers/esrgan/esrgan_x4c64b23g32_1x16_400k_div2k_20200508-f8ccaf3b.pth) |
| [esrgan_x4c64b23g32_1x16_400k_div2k](./esrgan_x4c64b23g32_1xb16-400k_div2k.py)  |  Set14  | 24.6328 | 0.6491 |         1          | [model](https://download.openmmlab.com/mmediting/restorers/esrgan/esrgan_x4c64b23g32_1x16_400k_div2k_20200508-f8ccaf3b.pth) |
| [esrgan_x4c64b23g32_1x16_400k_div2k](./esrgan_x4c64b23g32_1xb16-400k_div2k.py)  |  DIV2K  | 26.6531 | 0.7340 |         1          | [model](https://download.openmmlab.com/mmediting/restorers/esrgan/esrgan_x4c64b23g32_1x16_400k_div2k_20200508-f8ccaf3b.pth) |

## Quick Start

**Train**

<details>
<summary>Train Instructions</summary>

You can use the following commands to train a model with cpu or single/multiple GPUs.

```shell
# cpu train
CUDA_VISIBLE_DEVICES=-1 python tools/train.py configs/esrgan/esrgan_x4c64b23g32_1xb16-400k_div2k.py

# single-gpu train
python tools/train.py configs/esrgan/esrgan_x4c64b23g32_1xb16-400k_div2k.py

# multi-gpu train
./tools/dist_train.sh configs/esrgan/esrgan_x4c64b23g32_1xb16-400k_div2k.py 8
```

For more details, you can refer to **Train a model** part in [train_test.md](/docs/en/user_guides/train_test.md#Train-a-model-in-MMEditing).

</details>

**Test**

<details>
<summary>Test Instructions</summary>

You can use the following commands to test a model with cpu or single/multiple GPUs.

```shell
# cpu test
CUDA_VISIBLE_DEVICES=-1 python tools/test.py configs/esrgan/esrgan_x4c64b23g32_1xb16-400k_div2k.py https://download.openmmlab.com/mmediting/restorers/esrgan/esrgan_x4c64b23g32_1x16_400k_div2k_20200508-f8ccaf3b.pth

# single-gpu test
python tools/test.py configs/esrgan/esrgan_x4c64b23g32_1xb16-400k_div2k.py https://download.openmmlab.com/mmediting/restorers/esrgan/esrgan_x4c64b23g32_1x16_400k_div2k_20200508-f8ccaf3b.pth

# multi-gpu test
./tools/dist_test.sh configs/esrgan/esrgan_x4c64b23g32_1xb16-400k_div2k.py https://download.openmmlab.com/mmediting/restorers/esrgan/esrgan_x4c64b23g32_1x16_400k_div2k_20200508-f8ccaf3b.pth 8
```

For more details, you can refer to **Test a pre-trained model** part in [train_test.md](/docs/en/user_guides/train_test.md#Test-a-pre-trained-model-in-MMEditing).

</details>

## Citation

```bibtex
@inproceedings{wang2018esrgan,
  title={Esrgan: Enhanced super-resolution generative adversarial networks},
  author={Wang, Xintao and Yu, Ke and Wu, Shixiang and Gu, Jinjin and Liu, Yihao and Dong, Chao and Qiao, Yu and Change Loy, Chen},
  booktitle={Proceedings of the European Conference on Computer Vision Workshops(ECCVW)},
  pages={0--0},
  year={2018}
}
```
