# YOLOv8-jetson-nano-를 사용해 동영상속 사람과 사물을 인식 시키기 

참고링크 : https://github.com/jetsonmom/yolov8_jetson4GB

#jetpack 4.6.1
#이 프로그램은 jetson-nano를 이용해 yolov8을 다운 받아야 함으로 python 버전을 3.8로 하는 것을 추천한다. 


먼저 archiconda3를 다운 시켜준다. 
 ./Archiconda3-0.2.3-Linux-aarch64.sh 

그 다음 
conda env list 
conda activate base   #conda deactivate 
jetson_relase 
를 차래대로 작성한다.


그 다음은 파이썬 3.8 가상 환경을 만들 차례이다. 
이때 base가 아닌 native 환경에서 아래 명령어를 실행해야 하므로 conda deactivate 를 실행하고 
아래 명령어를 실행한다. 

conda create -n yolo python=3.8 -y 
conda env list 

conda activate yolo 
#yolo 가상환경으로 진입해 pythorch, torchvosion을 설치한다. 

 pip install -U pip wheel gdown
 gdown https://drive.google.com/uc?id=1hs9HM0XJ2LPFghcn7ZMOs5qu5HexPXwM
 gdown https://drive.google.com/uc?id=1m0d8ruUY8RvCP9eVjZw4Nc8LAwM8yuGV

 sudo apt-get install libopenblas-base libopenmpi-dev
sudo apt-get install libomp-dev
pip install torch-1.11.0a0+gitbc2c6ed-cp38-cp38-linux_aarch64.whl
pip install torchvision-0.12.0a0+9b5a3fe-cp38-cp38-linux_aarch64.whl
python -c "import torch; print(torch.__version__)"

넘파이를 설치한다. 
conda install numpy 

이제 python에 들어가 pytorch 와 torchvision을 import 해준 다음 아래 과정을 수행한다. 

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
(yolo) dli@jdli:~/Jetson-Nano2$treee -L 2



이때 그냥하면 화면이 보이지 않아서 brtsp= False 로 변경해 주고 실행 시켜야 한다. 



