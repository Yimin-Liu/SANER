# SANER: Switchable Adapter with Non-parametric Enhanced Routing for Person De-Reidentification

🚧 **Code Coming Soon**

This repository contains the official implementation of our CVPR 2026 paper:

**SANER: Switchable Adapter with Non-parametric Enhanced Routing for Person De-Reidentification**

SANER is designed for **Person De-Reidentification (De-ReID)**, which aims to remove the identity information of specified individuals from a trained person Re-ID model while preserving the recognition ability for the remaining identities. Our method introduces a **Switchable Adapter** with **Non-parametric Enhanced Routing** to achieve flexible, efficient, and effective identity forgetting.

---

## News

* The official code will be released soon.
* Pretrained models and configuration files will be provided for different datasets and forgetting settings.

---

## Installation

### 1. Create a Conda Environment

```bash
conda create -n saner python=3.8 -y
conda activate saner
```

### 2. Install Dependencies

Install the required dependencies using the provided script:

```bash
bash requirements.sh
```

---

## Preparation

### 1. Download Pretrained Models

Please download the pretrained Re-ID models and place them under:

```bash
SANER/logs/{dataset}_pretrain/transformer_120.pth
```

Here, `{dataset}` indicates the dataset name and can be:

```bash
market1501
msmt17
```

For example, the expected pretrained model paths are:

```bash
SANER/logs/market1501_pretrain/transformer_120.pth
SANER/logs/msmt17_pretrain/transformer_120.pth
```

The expected directory structure is:

```bash
SANER/
├── logs/
│   ├── market1501_pretrain/
│   │   └── transformer_120.pth
│   └── msmt17_pretrain/
│       └── transformer_120.pth
├── configs/
├── saner_finetune.py
├── requirements.sh
└── README.md
```

The download links for pretrained models will be released soon.

---

## Running SANER

We provide configuration files for different datasets and forgetting settings.

The numbers `25` and `50` indicate the number of identities to be forgotten.

---

### Market-1501

#### Forgetting 25 Identities

```bash
python saner_finetune.py \
  --config_file ./configs/DeReIDMarket/exp_lora_25.yml
```

#### Forgetting 50 Identities

```bash
python saner_finetune.py \
  --config_file ./configs/DeReIDMarket/exp_lora_50.yml
```

---

### MSMT17

#### Forgetting 25 Identities

```bash
python saner_finetune.py \
  --config_file ./configs/DeReIDMSMT/exp_lora_25.yml
```

#### Forgetting 50 Identities

```bash
python saner_finetune.py \
  --config_file ./configs/DeReIDMSMT/exp_lora_50.yml
```

---

## Configuration

All experimental settings are specified in the YAML configuration files under:

```bash
configs/
├── DeReIDMarket/
│   ├── exp_lora_25.yml
│   └── exp_lora_50.yml
└── DeReIDMSMT/
    ├── exp_lora_25.yml
    └── exp_lora_50.yml
```

You can modify the configuration files to change:

* Dataset name and path
* Pretrained model path
* Number of forgotten identities
* Training hyperparameters
* Adapter settings
* Evaluation protocols

---

## Dataset Preparation

Please prepare the person Re-ID datasets following the standard format used in common Re-ID benchmarks.

The expected dataset structure is:

```bash
datasets/
├── Market-1501/
│   ├── bounding_box_train/
│   ├── bounding_box_test/
│   └── query/
└── MSMT17/
    ├── bounding_box_train/
    ├── bounding_box_test/
    └── query/
```

Please make sure the dataset paths are correctly specified in the corresponding configuration files.

---

## Main File Structure

```bash
SANER/
├── configs/                 # Configuration files for different datasets and forgetting settings
├── logs/                    # Pretrained models and training logs
│   ├── market1501_pretrain/ # Pretrained model for Market-1501
│   │   └── transformer_120.pth
│   └── msmt17_pretrain/     # Pretrained model for MSMT17
│       └── transformer_120.pth
├── saner_finetune.py        # Main script for SANER fine-tuning
├── requirements.sh          # Dependency installation script
└── README.md
```

---

## Citation

If you find this repository useful for your research, please cite our paper:

```bibtex
@inproceedings{zhang2026saner,
  title={SANER: Switchable Adapter with Non-parametric Enhanced Routing for Person De-Reidentification},
  author={Zhang, Yongle and others},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  year={2026}
}
```

---

## Acknowledgement

This codebase is built upon widely used person Re-ID and parameter-efficient fine-tuning frameworks. We sincerely thank the authors of these open-source projects for their valuable contributions to the community.

---

## License

The license will be released together with the code.

