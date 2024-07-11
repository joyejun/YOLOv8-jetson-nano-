# YOLOv8을 사용해 Jetson Nano에서 동영상 속 사람과 사물 인식

## 참고 링크
[YOLOv8 Jetson4GB GitHub Repository](https://github.com/jetsonmom/yolov8_jetson4GB)

## 환경 설정
- **JetPack 버전:** 4.6.1
- **권장 Python 버전:** 3.8

> **주의:** 이 프로그램은 Jetson Nano를 이용해 YOLOv8을 다운받아야 하므로 Python 버전을 3.8로 설정하는 것을 추천합니다.

### Archiconda3 설치
먼저 Archiconda3를 설치합니다:
```bash
./Archiconda3-0.2.3-Linux-aarch64.sh

### conda 설정
다음 명령어를 차례대로 실행해줍니다.

conda env list
conda activate base
jetson_release

Python 3.8 가상 환경 생성
base가 아닌 native 환경에서 아래 명령어를 실행해야 하므로 conda deactivate를 먼저 실행한 후, 다음 명령어를 실행합니다:

conda create -n yolo python=3.8 -y
conda env list
conda activate yolo


PyTorch 및 TorchVision 설치
yolo 가상환경으로 진입한 후 다음을 설치합니다:

pip install -U pip wheel gdown
gdown https://drive.google.com/uc?id=1hs9HM0XJ2LPFghcn7ZMOs5qu5HexPXwM
gdown https://drive.google.com/uc?id=1m0d8ruUY8RvCP9eVjZw4Nc8LAwM8yuGV

sudo apt-get install libopenblas-base libopenmpi-dev
sudo apt-get install libomp-dev
pip install torch-1.11.0a0+gitbc2c6ed-cp38-cp38-linux_aarch64.whl
pip install torchvision-0.12.0a0+9b5a3fe-cp38-cp38-linux_aarch64.whl
python -c "import torch; print(torch.__version__)"

numpy  설치

conda install numpy

Python에 들어가서 PyTorch와 TorchVision을 import한 다음 아래 과정을 수행합니다:

(yolo) dli@dli:~$ python
>>> import torch
>>> import torchvision
>>> print(torch.__version__)
>>> print(torchvision.__version__)
>>> print("cuda used", torch.cuda.is_available())
cuda used True

git clone https://github.com/Tory-Hwang/Jetson-Nano2
(yolo) dli@dli:~$ cd Jetson-Nano2/
(yolo) dli@dli:~/Jetson-Nano2$ cd V8
(yolo) dli@dli:~/Jetson-Nano2/V8$ pip install ultralytics
(yolo) dli@dli:~/Jetson-Nano2/V8$ pip install -r requirements.txt
(yolo) dli@jdli:~/Jetson-Nano2/V8$ pip install ffmpeg-python
(yolo) dli@dli:~/Jetson-Nano2$ sudo apt install tree
(yolo) dli@jdli:~/Jetson-Nano2$ tree -L 2

이때 그냥 실행하면 화면이 보이지 않으므로 brtsp= False로 변경해 주고 실행해야 합니다.

