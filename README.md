# NeuralHeadAvator

This is the official PyTorch implementation of the final project of COMP8536.

## 1. Datasets
Please follow the instructions in [Video-preprocessing](https://github.com/AliaksandrSiarohin/video-preprocessing) to download and preprocess the datasets. In this project, we only use the VoxCelab dataset.

## 2. Training

To train the netowrk, run
```shell script
CUDA_VISIBLE_DEVICES=0,1,2,3 python train.py --exp_path <EXP_PATH> --exp_name <EXP_NAME>
```
You should adjust the device numbers in `CUDA_VISIBLE_DEVICES`. Tensorboard log and checkpoints will be saved in `<EXP_PATH>/<EXP_NAME>/log` and `<EXP_PATH>/<EXP_NAME>/chekcpoints` respectively.

To continue from a checkpoint, run
```shell script
CUDA_VISIBLE_DEVICES=0,1,2,3 python train.py --exp_path <EXP_PATH> --exp_name <EXP_NAME> --resume_ckpt <CHECKPOINT_PATH>
```
The path of the checkpoint should be provided in `<CHECKPOINT_PATH>`

## 3. Evaluation
To obtain L_1 and LPIPS results, put checkpoints under `./checkpoints` and run
```shell script
CUDA_VISIBLE_DEVICES=0 python evaluation.py --dataset <DATASET> --save_path <SAVE_PATH>
```
Generated videos will be save under `<SAVE_PATH>`.

## 4. Demo
Download pre-trained checkpoints from [Google Drive](https://drive.google.com/file/d/1va7e9ZJZVKUkmB_z49G10pODnH9aSv1X/view?usp=share_link) and put it in `./checkpoints`. You should rename it as `vox.pt`.

Several demo source images and driving videos are provided in `./data`. 
You can run the following commands to generate demo videos. The results will be saved in `./res`.
```shell script
CUDA_VISIBLE_DEVICES=0 python run_demo.py --source_path <SOURCE_PATH> --driving_path <DRIVING_PATH>
```
`<SOURCE_PATH>`  is the source image, `<DRIVING_PATH>`  is the driving video

For example 
```shell script
CUDA_VISIBLE_DEVICES=0 python run_demo.py --source_path ./data/vox/taylor.png --driving_path ./data/vox/driving2.mp4
```

## Acknowledgement
Part of the code is adapted from [LIA](https://github.com/wyhsirius/LIA). We thank authors for their contribution to the community.
