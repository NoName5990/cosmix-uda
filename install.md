## cosmix安装流程：
    1、首先创建环境，用pip安装cu111的torch和torchvision并切换到相应的环境
        1) conda create -n cosmix python=3.8
        2) pip install torch==1.8.0+cu111 torchvision==0.9.0+cu111 torchaudio==0.8.0 -f https://download.pytorch.org/whl/torch_stable.html
        3) conda activate cosmix
    2、git克隆MinkowskiEngine后，cd然后用conda本地安装的方式进行安装:
        1)git clone https://github.com/NVIDIA/MinkowskiEngine.git
        2)cd MinkowskiEngine
        3)python setup.py install --blas_include_dirs=${CONDA_PREFIX}/include --blas=openblas
    3、pip安装open3d
    4、pip安装pytorch-lighting==1.4.1，可能会卸载掉torch，重新安回来即可
    5、pip安装后续的wandb和tqdm

    6、有个坑就是jaccard_score函数，它是通过from sklearn.metrcis import jaccard_score导入的，但是有的版本不支持zero_division=-1，手动进行文件复制的，通过替换/userHome/xzy/.conda/envs/cosmix/lib/python3.8/site-packages/sklearn文件夹