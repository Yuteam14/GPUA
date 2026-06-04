<div align="center">

<h1>Geometry-Preserving Unsupervised Alignment for Heterogeneous Foundation Models</h1>

<div>
    <a target='_blank'>Akang Wang<sup>1</sup></a>&emsp;
    <a target='_blank'>Xili Deng<sup>1</sup></a>&emsp;
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

</div>

<br>
<br> <div align="center">
  <img src="https://akang-wang.github.io/PIAA/main.png" alt="PIAA Architecture" width="90%">
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

## 🚀 Run PIAA
You can easily reproduce the experimental results using the provided bash scripts:
```
bash piaa.sh     # Run SC-CLIP + PIAA only
bash all.sh      # Run SCLIP+PIAA, ITACLIP+PIAA, and SC-CLIP+PIAA
```
## 📊 Main Results
Comparison of the PIAA improvement across different multi-label classification datasets:
| Method       | VOC12 | VOC07 | COCO | NUS  |
| ------------ | ----- | ----- | ---- | ---- |
| SCLIP+PIAA   | 91.4  | 91.7  | 73.0 | 49.2 |
| ITACLIP+PIAA | 92.2  | 92.3  | 74.6 | 49.1 |
| SC-CLIP+PIAA | 92.2  | 92.5  | 73.2 | 50.6 |


## 🙏 Acknowledgement
This project is built upon the foundational work of [SCLIP](https://github.com/wangf3014/SCLIP), [ITACLIP](https://github.com/m-arda-aydn/ITACLIP), and [SC-CLIP](https://github.com/SuleBai/SC-CLIP). We sincerely thank the authors for open-sourcing their great repositories.


## 🏷️ Citation
If you find our work useful in your research, please consider giving a star ⭐ and citing the following paper 📝.
```
@misc{wang2026clsenoughmultilabelrecognition,
      title={[CLS] is Not Enough: Multi-Label Recognition via Patch-Level Inference and Adaptive Aggregation}, 
      author={Akang Wang and Xili Deng and Zhanxuan Hu and Yi Zhao and Yonghang Tai and Huafeng Li},
      year={2026},
      eprint={2605.25821},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2605.25821}, 
}
```
