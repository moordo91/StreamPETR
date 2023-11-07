# Dataset path
```sh
/raid/datasets/NuScenes/nuscenes/
```

# Creating *.pkl
But I didn't use this command, because I downloaded files from the github.
```sh
python3.8 tools/create_data_nusc.py --root-path /raid/datasets/NuScenes/nuscenes --out-dir /raid/datasets/NuScenes/nuscenes --extra-tag nuscenes2d --version v1.0
```

# Training
```sh
CUDA_VISIBLE_DEVICES=3 PORT=30500 tools/dist_train.sh projects/configs/StreamPETR/stream_petr_r50_flash_704_bs2_seq_24e.py 1 --work-dir work_dirs/stream_petr_r50_flash_704_bs2_seq_24e/
```

# Modified File Table

- 기존 path를 새로운 path로 수정함  
- 몇몇 test 코드(tests/data/\*), converter 코드 및 visualize 등은 그대로 유지
- Before의 '.' 유무에 대해서 고민해볼 것

| File | LN | Before | After |
|:---|:---:|:---|:---|
|nus-3d.py|10|'data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|nus-mono3d.py|2|'data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|centerpoint_01voxel_second_secfpn_4x8_cyclic_20e_nus.py|24|'data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|centerpoint_02pillar_second_secfpn_4x8_cyclic_20e_nus_novelo.py|31|'data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|centerpoint_02pillar_second_secfpn_4x8_cyclic_20e_nus.py|25|'data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|centerpoint_0075voxel_second_secfpn_4x8_cyclic_20e_nus.py|29|'data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|mask_rcnn_r50_fpn_coco-2x_1x_nus-2d.py|13|'./data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|상동|14|'data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|focal_petrv1_r50_flash_704_24e.py|142|'./data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|petrv1_r50_flash_704_24e.py|122|'./data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|repdetr3d_vov_800_bs2_seq_24e.py|143|'./data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|stream_petr_r50_flash_704_bs1_8key_2grad_24e.py|148|'./data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|stream_petr_r50_flash_704_bs2_seq_24e.py|152|'./data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|stream_petr_r50_flash_704_bs2_seq_90e.py|152|'./data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|stream_petr_r50_flash_704_bs2_seq_428q_nui_24e.py|154|'./data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|stream_petr_r50_flash_704_bs2_seq_428q_nui_60e.py|154|'./data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|stream_petr_vov_flash_800_bs2_seq_24e.py|148|'./data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|
|stream_petr_r50_704_bs2_seq_428q_nui_speed_test.py|154|'./data/nuscenes/'|'/raid/datasets/NuScenes/nuscenes/'|

# Error Log
```sh
FileNotFoundError: [Errno 2] No such file or directory: './data/nuscenes/samples/CAM_FRONT/n008-2018-09-18-12-53-31-0400__CAM_FRONT__1537290001612404.jpg'
```

# Softlink
