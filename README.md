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
  <a target="_blank" href="https://arxiv.org/pdf/2606.04385"><img src="https://img.shields.io/badge/arXiv-2606.04385-b31b1b.svg" alt="arXiv Paper"/></a>
  <a href="https://github.com/Yuteam14/GPUA/"><img src="https://img.shields.io/badge/Project-Homepage-blue.svg" alt="Project Homepage"></a>

</div>


</div>

## 🛠️ Setup

```
# create conda env
conda create -y --name GPUA python=3.10.0
conda activate GPUA

# install packages
pip install torch==2.6.0+cu118 torchvision==0.21.0+cu118 torchaudio==2.6.0+cu118 --index-url https://download.pytorch.org/whl/cu118
pip install -r requirements.txt
```

## 📂 Dataset Preparation
For image datasets, please follow the instruction of CoOp here: [DATASETS.md](https://github.com/KaiyangZhou/CoOp/blob/main/DATASETS.md)

## 🚀 Run GPUA
### Zero-Shot Classification Setting

Run the following script to reproduce the zero-shot classification results:
```
NitersCaltech101=1000
NitersDescribableTextures=1000
NitersEuroSAT=100
NitersFood101=200
NitersFGVCAircraft=1000
NitersOxfordFlowers=100
NitersOxfordPets=100
NitersStanfordCars=1000
NitersSUN397=100
NitersImageUCF101=200
NitersImageNet=200
FEATURES_PATH="saved_features"
DATASET_PATH=""
DATASET_NAME="ImageUCF101"

python main.py --model-type dinov2 --use-template \
    --save-path $FEATURES_PATH --n-iters 200 \
    --config config_files/cfg_image.yaml \
    RNG_SEED 1 MODEL.VIZ_BACKBONE ViT-B/16 \
    DATA.DATASET_NAME $DATASET_NAME DATA.DATA_PATH $DATASET_PATH DATA.N_SHOT 16
```
First, set `DATASET_PATH` to the correct path of the folder containing all the image datasets, then run the command above.

- The example command is configured for `ImageNet`. To evaluate on a different dataset, simply change `DATA.DATASET_NAME`.
- To reproduce the exact results reported in the paper, make sure to also update `--n-iters` to the value corresponding to the selected dataset.
- You can change `MODEL.VIZ_BACKBONE` to use a different visual backbone (currently `ViT-B/16` is provided).
- Modify `DATA.N_SHOT` to control the number of support examples per class.

By default, the code runs in the **16-shot** setting (`DATA.N_SHOT=16`).

- `DATA.N_SHOT=0`: use all available training samples for each class.
- `DATA.N_SHOT=1, 4, 8, ...`: evaluate the corresponding few-shot setting.
- `DATA.N_SHOT=16`: the default setting used in our experiments.

