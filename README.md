<div align="center">

<h1>Geometry-Preserving Unsupervised Alignment for Heterogeneous Foundation Models</h1>

<div>
    <a target='_blank'>Shuwen Yu<sup>1</sup></a>&emsp;
    <a target='_blank'>Zhanxuan Hu<sup>1, ✉</sup></a>&emsp;
    <a target='_blank'>Yi Zhao<sup>1</sup></a>&emsp;
    <a target='_blank'>Yonghang Tai<sup>1</sup></a>&emsp;  
    <a target='_blank'>Huafeng Li<sup>2</sup></a>&emsp;        
</div>
<div>
    <sup>1</sup>Yunnan Normal University&emsp; 
    <sup>2</sup>Kunming University of Science and Technology&emsp;
</div>
<div>
    <h3>ICML 2026</h3>
</div>

<div align="center">
  <a target="_blank" href="https://arxiv.org/abs/2605.25821"><img src="https://img.shields.io/badge/arXiv-2605.25821-b31b1b.svg" alt="arXiv Paper"/></a>
  <a href="https://akang-wang.github.io/PIAA/"><img src="https://img.shields.io/badge/Project-Homepage-blue.svg" alt="Project Homepage"></a>
  <a href="https://openreview.net/forum?id=sKOTyhXscD&noteId=yDs8dnAwWB"><img src="https://img.shields.io/badge/OpenReview-View-f7b500.svg" alt="OpenReview"></a>

</div>


</div>
## 🛠️ Setup

```
# create conda env
conda create -y --name PIAA python=3.10.0
conda activate PIAA

# install packages
pip install torch==2.7.1 torchvision==0.22.1 torchaudio==2.7.1 --index-url https://download.pytorch.org/whl/cu118
pip install -r requirements.txt
```

## 📂 Dataset Preparation
Download each dataset from the official website ([PASCAL VOC 2007](http://host.robots.ox.ac.uk/pascal/VOC/voc2007/), [PASCAL VOC 2012](http://host.robots.ox.ac.uk/pascal/VOC/voc2012/), [COCO 2014](https://cocodataset.org/#download), [NUS-WIDE](https://github.com/NExTplusplus/NUS-WIDE)) and put them under local directory like `/PIAA` .
The structure of the dataset directory should be organized exactly as follows:
```
PIAA/
├── data/                               
│   ├── pascal/
│   │   └── VOCdevkit/
│   │       ├── VOC2007/
│   │       │   └── JPEGImages/         
│   │       └── VOC2012/
│   │           └── JPEGImages/         
│   │
│   ├── coco/
│   │   ├── train2014/                  
│   │   └── val2014/                    
│   │
│   └── nuswide/
│       └── Flickr/
│           ├── actor/
│           └── administrative_assistant/
│
├── learn.py
├── test.py
└── ...                   
```

