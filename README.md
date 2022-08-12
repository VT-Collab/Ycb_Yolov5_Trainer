# Ycb_Yolov5_Trainer
## Installation

### Commands to be executed in order:
1. ```git clone``` [Ycb_Yolov5_Trainer](https://github.com/VT-Collab/Ycb_Yolov5_Trainer.git) (Clone to any folder other than your [Ycb_Dataset_Generator](https://github.com/VT-Collab/Ycb_Dataset_Generator.git) folder)
2. ```cd ./Ycb_Yolov5_Trainer```
4. Setup and install ```Python 3.7.12``` or ```Python 3.8.0``` using [Pyenv](https://realpython.com/intro-to-pyenv/). **CREATE** and **ACTIVATE** a new python environment named '**YCB_Trainer**' running Python 3.7.12 or Python 3.8.0. (This step is required to successfully meet all the requirements)
    * ```pyenv virtualenv 3.7.12 YCB_Trainer``` (Install python and create python virtual environment)
    * (Only for the initial setup) ```pyenv local YCB_Trainer``` (Activate python virtual environment)
    * ```pyenv versions``` (Check if the correct virtual environment with intended python version is active) 
3. ```pip install -r ./Requirements/requirements.txt``` (Installs Ycb_Yolov5_Trainer's requirements)
4. Move/copy your custom dataset generated from following the steps on [Ycb_Dataset_Generator](https://github.com/VT-Collab/Ycb_Dataset_Generator.git) to the current directory.
    * Example: ```mv ../Ycb_Dataset_Generator/custom_dataset .``` OR ```cp ../Ycb_Dataset_Generator/custom_dataset .```
5. ```git clone``` [yolov5](https://github.com/ultralytics/yolov5) (Clones ultralytics's yolov5 repository)
6. ```cd yolov5```
7. ```pip install -r requirements.txt``` (Installs ultralytics's yolov5's requirements)
8. Training the model:
* ```python ./train.py --img 640 --batch 16 --epochs 500 --data ../custom_dataset/data.yaml  --cfg ./models/custom_yolov5s6.yaml --weights 'yolov5s6.pt' --name yolov5s6_results --cache```
    * pretrained weights (more options available): yolov5s6
    * epochs (more number of epochs possible): 500
    * batch (higher number is possible with better hardware)
9. Deploying with ultralytic's implementation (example):
* ```python detect.py --source -1 --weights ./runs/train/yolov5s6_results/weights/best.pt```

![image](https://user-images.githubusercontent.com/68425706/184452394-d01beb14-67d3-45e5-b8fd-cb5d36e6c683.png)
![image](https://user-images.githubusercontent.com/68425706/184452400-b5e9ce22-0f4f-48c5-bbd5-b7164f6ac87c.png)

### Possible changes needed to run the notebook:
* Packages import configuration can be different different machines:
![image](https://user-images.githubusercontent.com/68425706/184435407-15dcaf1a-8c89-4be3-82e6-d56b3e73d640.png)

### Custom dataset generation config:
* You can change the name of the custom dataset, number of images generated per split, andd add new split.
![image](https://user-images.githubusercontent.com/68425706/184442187-a4640d8c-4c72-4046-a4b1-b0de7be340c2.png)

### Resize dataset images
* Recommended image sizes: ```640x640``` OR ```416x416```
![image](https://user-images.githubusercontent.com/68425706/184442086-41e810f8-a338-437e-ab8b-ccf11fcc835a.png)

