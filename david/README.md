
# Envirment

```
$ conda remove -n PointPillars --all
$ conda create -n PointPillars python=3.9
$ conda activate PointPillars
$ pip3 install -r requirements.txt -i https://pypi.mirrors.ustc.edu.cn/simple/

$ pip3 install torch==1.8.0+cu111 torchvision==0.9.0+cu111 torchaudio==0.8.0 -f https://download.pytorch.org/whl/torch_stable.html
```



# Test

```
$ python test.py --ckpt pretrained/epoch_160.pth --pc_path=/home/david/dataset/kitti/testing/velodyne/000000.bin

$ python test.py --ckpt pretrained/vic3d_latefusion_inf_pointpillars_596784ad6127866fcfb286301757c949.pth --pc_path=/home/david/dataset/kitti/testing/velodyne/000000.bin

$ python test.py --ckpt pretrained/epoch_160.pth \
        --pc_path /home/david/dataset/kitti/testing/velodyne/000000.bin \ 
        --calib_path dataset/demo_data/val/000134.txt --img_path /home/david/dataset/kitti/testing/image_2/000000.png \ 
        --gt_path dataset/demo_data/val/000134_gt.txt

$ python test.py --ckpt pretrained/epoch_160.pth \
        --pc_path /home/david/dataset/kitti/testing/velodyne/000002.bin \
        --img_path /home/david/dataset/kitti/testing/image_2/000002.png \
        --calib_path /home/david/dataset/kitti/testing/calib/000002.txt


$ python test.py --ckpt pretrained/epoch_160.pth \
        --pc_path /home/david/dataset/dair-kitti/training/velodyne/000000.bin \
        --img_path /home/david/dataset/dair-kitti/training/image_2/000000.jpg \
        --calib_path /home/david/dataset/dair-kitti/training/calib/000000.txt
```




Convert DAIR-V2X to kitti:
https://blog.csdn.net/m0_57273938/article/details/126418351

```

export PYTHONPATH=./

rm -rf /home/david/dataset/dair-kitti/*

python tools/dataset_converter/dair2kitti.py \
        --source-root /home/david/dataset/cooperative-vehicle-infrastructure/infrastructure-side/single-infrastructure-side-example/ \
        --target-root /home/david/dataset/dair-kitti/ \
        --split-path /home/david/dataset/cooperative-vehicle-infrastructure/infrastructure-side/single-infrastructure-side-example/data_info.json \
        --label-type lidar \
        --sensor-view infrastructure \
        --no-classmerge



python tools/dataset_converter/dair2kitti.py \
        --source-root /home/david/dataset/cooperative-vehicle-infrastructure/infrastructure-side/ \
        --target-root /home/david/dataset/dair-kitti/ \
        --label-type lidar \
        --sensor-view infrastructure \
        --no-classmerge
```



