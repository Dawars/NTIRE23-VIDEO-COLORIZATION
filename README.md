## [NTIRE 2023 Video Colorization Challenge](https://tianchi.aliyun.com/competition/entrance/532054/rankingList) @ CVPR 2023
## Track 1: Fréchet Inception Distance (FID) Optimization

Please visit [test_NTIRE23_Track_1_FID.py](https://github.com/yyang181/NTIRE23-VIDEO-COLORIZATION/blob/main/BiSTNet-NTIRE2023/test_NTIRE23_Track_1_FID.py) to evaluate our model.

We provide the colorized images [HERE](https://drive.google.com/drive/folders/1jwVKK2IfAp01C6KpuqB3Wcm0uT4yXZBB?usp=share_link), and the reference images used to obtain the results [HERE](https://drive.google.com/drive/folders/1miA49ALEKDxsDlmsdZX38tik9V4ECqES?usp=share_link).

## News

- [2023-12-05] Add inference code using two reference images, see [test_BiSTNet.py](https://github.com/yyang181/NTIRE23-VIDEO-COLORIZATION/blob/main/BiSTNet-NTIRE2023/test_BiSTNet.py).  
- [2023-12-02] Colab demo for BiSTNet is available [![google colab logo](https://camo.githubusercontent.com/84f0493939e0c4de4e6dbe113251b4bfb5353e57134ffd9fcab6b8714514d4d1/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667)](https://colab.research.google.com/drive/1T7-BOpSkd41fNW8bffo6aXSeK_jizsvv#scrollTo=OVMNWEaz2b06).

## :briefcase: Dependencies and Installation

- PyTorch >= 1.8.0 (please do not use 2.1.0)

- CUDA >= 10.2

- mmcv == 1.x

- mmediting == 0.x

- Other required packages

  ```
  # git clone this repository
  git clone https://github.com/yyang181/NTIRE23-VIDEO-COLORIZATION.git
  cd NTIRE23-VIDEO-COLORIZATION
  ```

#### Environment configuration: 

```
cd BiSTNet-NTIRE2023

# create a new anaconda env
conda create -n bistnet python=3.6
conda activate bistnet

# install pytortch
conda install pytorch==1.10.1 torchvision==0.11.2 torchaudio==0.10.1 cudatoolkit=11.3 -c pytorch -c conda-forge

# mmcv install (1.x, please do not use 2.x)
pip install -U openmim
mim install mmcv-full

# install mmediting (0.x, please do not use 1.x)
git clone https://github.com/open-mmlab/mmediting.git
cd mmediting
pip3 install -e .

# install other pip pkgs 
cd .. && pip install -r pip_requirements.txt
```


## :gift: Checkpoints

|  Name   |                             URL                              |                            Script                            |   FID   |   CDC    |
| :-----: | :----------------------------------------------------------: | :----------------------------------------------------------: | :-----: | :------: |
| BiSTNet | [model](https://drive.google.com/drive/folders/1nakixYiDq6qmP4MZw_gbAhtud4a9yz5h?usp=share_link) | [test_NTIRE23_Track_1_FID.py](https://github.com/yyang181/NTIRE23-VIDEO-COLORIZATION/blob/main/BiSTNet-NTIRE2023/test_NTIRE23_Track_1_FID.py) | 21.5372 | 0.001717 |

## :zap: Quick Inference for NTIRE 2023 Video Colorization Challenge

This version is specifically designed for [NTIRE 2023 Video Colorization Challenge](https://tianchi.aliyun.com/competition/entrance/532054/rankingList) @ CVPR 2023. We colorize every 50 frames with two exemplars, see clip *001* for an example. 

- **Download Pre-trained Models**: download a pretrained colorization model from the tabulated links, and put it into the folder `./BiSTNet-NTIRE2023/`, like `./BiSTNet-NTIRE2023/checkpoints` , `./BiSTNet-NTIRE2023/data` and `./BiSTNet-NTIRE2023/models/protoseg_core/checkpoints` .
- **Prepare Testing Data**: You can put the testing images in a folder, like clip *001* at `./demo_dataset`.
  - `demo_dataset/input`: the directory of input grayscale images.
  - `demo_dataset/ref`: the directory of reference images (only `f001.png, f050.png and f100.png` are colorful images).
  - `demo_dataset/output`: the directory to save the colorization results.
- **Test on Images**: 

```
conda activate bistnet && cd BiSTNet-NTIRE2023
CUDA_VISIBLE_DEVICES=0 python test_NTIRE23_Track_1_FID.py
```

For more details please refer to [test_NTIRE23_Track_1_FID.py](https://github.com/yyang181/NTIRE23-VIDEO-COLORIZATION/blob/main/BiSTNet-NTIRE2023/test_NTIRE23_Track_1_FID.py).

## :zap: Quick Inference for BiSTNet version

This version allows arbitrary number of input video frames with two exemplars. See clip *fanghua234* for an example. 

- **Prepare Testing Data**: You can put the testing images in a folder, like *fanghua234* at `./demo_dataset`.

  - `demo_dataset/input`: the directory of input grayscale images.

  - `demo_dataset/ref`: the directory of reference images ( `frame0000.png, frame0150.png`).

  - `demo_dataset/output`: the directory to save the colorization results.

- **Test on Images**: 

```
conda activate bistnet && cd BiSTNet-NTIRE2023
CUDA_VISIBLE_DEVICES=0 python test_BiSTNet.py
```

For more details please refer to [test_BiSTNet.py](https://github.com/yyang181/NTIRE23-VIDEO-COLORIZATION/blob/main/BiSTNet-NTIRE2023/test_BiSTNet.py).

## License

BiSTNet is released under the MIT license, while some methods adopted in this project are with other licenses. Please refer to [LICENSES.md](https://github.com/yyang181/NTIRE23-VIDEO-COLORIZATION/blob/main/BiSTNet-NTIRE2023/LICENSE.md) for the careful check, if you are using our code for commercial matters. Thank [@milmor](https://github.com/milmor) so much for bringing up this concern about license.

## Acknowledgement

Part of our codes are taken from [DeepExemplar](https://github.com/zhangmozhe/Deep-Exemplar-based-Video-Colorization), [RAFT](https://github.com/princeton-vl/RAFT), [HED](https://github.com/sniklaus/pytorch-hed) and [ProtoSeg](https://github.com/tfzhou/ProtoSeg). Thanks for their awesome works.
