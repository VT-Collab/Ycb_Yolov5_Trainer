# Ycb_Yolov5_Trainer
## Installation

### Commands to be executed in order:
1. ```git clone``` [Ycb_Yolov5_Trainer](https://github.com/VT-Collab/Ycb_Yolov5_Trainer.git) (Clone to any folder other than your [Ycb_Dataset_Generator](https://github.com/VT-Collab/Ycb_Dataset_Generator.git) folder)
2. ```cd ./Ycb_Yolov5_Trainer```
3. Setup and install ```Python 3.7.12``` or ```Python 3.8.0``` using [Pyenv](https://realpython.com/intro-to-pyenv/). **CREATE** and **ACTIVATE** a new python environment named '**YCB_Trainer**' running Python 3.7.12 or Python 3.8.0. (This step is required to successfully meet all the requirements)
    * ```pyenv virtualenv 3.7.12 YCB_Trainer``` (Install python and create python virtual environment)
    * (Only for the initial setup) ```pyenv local YCB_Trainer``` (Activate python virtual environment)
    * ```pyenv versions``` (Check if the correct virtual environment with intended python version is active) 
4. ```pip install -r ./Requirements/requirements.txt``` (Installs Ycb_Yolov5_Trainer's requirements)
5. Move/copy your custom dataset generated from following the steps on [Ycb_Dataset_Generator](https://github.com/VT-Collab/Ycb_Dataset_Generator.git) to the current directory.
    * Example: ```mv ../Ycb_Dataset_Generator/custom_dataset .``` OR ```cp ../Ycb_Dataset_Generator/custom_dataset .```
6. ```git clone``` [yolov5](https://github.com/ultralytics/yolov5) (Clones ultralytics's yolov5 repository)
7. ```cd ./yolov5```
8. ```pip install -r requirements.txt``` (Installs ultralytics's yolov5's requirements)
9. Training a model (Transfer learning with ultralytic's pretrained checkpoints - faster & accurate):
   * ```bash
      python ./train.py --img 640 --batch 16 --epochs 500 --data ../custom_dataset/data.yaml --cfg ./models/custom_yolov5s6.yaml --weights 'yolov5s6.pt' --name yolov5s6_results --cache```
    * pretrained weights (more checkpoints available on ultralytics/yolov5 repository): yolov5s6
    ![image](https://user-images.githubusercontent.com/68425706/184452400-b5e9ce22-0f4f-48c5-bbd5-b7164f6ac87c.png)
    * epochs (more number of epochs possible): 500
    * batch (higher number is possible with better hardware)
10. Deploying custom trained model (example):
   * Collab's implementation:
     ```bash
     python ../yolov5Deploy.py live -1 ./runs/train/yolov5s6_results/weights/best.pt --mode 1```
   * Ultralytic's implementation:
     ```bash
     python detect.py --source -1 --weights ./runs/train/yolov5s6_results/weights/best.pt```
