# Official BGF-YOLO
This is the source code for the paper, "BGF-YOLO: Enhanced YOLOv8 with Multiscale Attentional Feature Fusion for Brain Tumor Detection", of which I am the first author.

## Model
The model configuration (i.e., network construction) file is bgf-yolo.yaml in the directory [./models/bgf](https://github.com/mkang315/BGF-YOLO/blob/main/models/bgf).

The hyperparameter setting file is default.yaml in the directory [./yolo/cfg/](https://github.com/mkang315/BGF-YOLO/blob/main/yolo/cfg).

##### Installation
Install requirements.txt in a Python>=3.8.0 environment, including PyTorch>=1.8.
```
pip install -r requirements.txt  # install
```

##### Training CLI
```
python yolo/bgf/detect/train.py
```

#### Testing CLI

```
python yolo/bgf/detect/predict.py
```

## Evaluation
We trained and evaluated BGF-YOLO on the dataset [Br35H :: Brain Tumor Detection 2020](https://www.kaggle.com/datasets/ahmedhamada0/brain-tumor-detection). The .txt format annotations in the file [dataset-Br35H.zip](https://github.com/mkang315/BGF-YOLO/blob/main/dataset-Br35H.zip) are coverted from original json format.

| Model | Precision | Recall | mAP<sub>50</sub> | mAP<sub>50:95</sub> |
| :-------: | :-------: | :-------: | :-------: | :-------: |
| [RT-DETR-X](https://github.com/ultralytics/ultralytics/tree/main/ultralytics/cfg/models/rt-detr) | 0.825 | 0.770 | 0.870 | 0.597 |
| [Co-DETR with Swin L (36 Epochs, DETR Augmentation)](https://github.com/Sense-X/Co-DETR) | – | – | 0.941 | 0.609 |
| [YOLOv9-E](https://github.com/WongKinYiu/yolov9) | **0.927** | 0.869 | 0.919 | 0.630 |
| [YOLOv10-X](https://github.com/THU-MIG/yolov10) | 0.916 | 0.808 | 0.880 | 0.603 |
| **BGF-YOLO (Ours)** | 0.919 | **0.926** | **0.974** | **0.653** |

## Generalizability in External Validation
We conducted additional experimental validation on a different domain using the [COVID-19 facemask detection dataset](https://www.kaggle.com/datasets/andrewmvd/face-mask-detection). The table below consistently shows the superior detection performance of our method compared to YOLOv8x. This indicates the generalizability of our method to other domains of object detection.

| Model | Precision | Recall | mAP<sub>50</sub> | mAP<sub>50:95</sub> |
| :-------: | :-------: | :-------: | :-------: | :-------: |
| YOLOv8x | 0.866 | 0.773 | 0.802 | 0.494 |
| **BGF-YOLO (Ours)** | 0.847 | 0.764 | **0.820** | **0.504** |

<!--
## Suggested Citation
Our manuscript has been uploaded on [arXiv](https://arxiv.org/abs/2309.12585). Please cite our paper if you use code from this repository:
> Plain Text

- *IEEE* Style</br>
M. Kang, C.-M. Ting, F. F. Ting, and R. C.-W. Phan, "Bgf-yolo: Enhanced yolov8 with multiscale attentional feature fusion for brain tumor detection," arXiv:2309.12585 [cs.CV], Jun. 2023.</br>

- *Nature* Style</br>
Kang, M., Ting, C.-M., Ting, F. F. & Phan, R. C.-W. BGF-YOLO: enhanced YOLOv8 with multiscale attentional feature fusion for brain tumor detection. Preprint at https://arxiv.org/abs/2309.12585 (2023).</br>

- *Springer* Style</br>
Kang, M., Ting, C.-M., Ting, F. F., Phan, R.C.-W.: BGF-YOLO: enhanced YOLOv8 with multiscale attentional feature fusion for brain tumor detection. arXiv preprint [arXiv:2309.12585](https://arxiv.org/abs/2309.12585) (2023)</br>
-->
## License
BGF-YOLO is released under the GNU Affero General Public License v3.0 (AGPL-3.0). Please see the [LICENSE](https://github.com/mkang315/BGF-YOLO/blob/main/LICENSE) file for more information.

## Copyright Notice
Many utility codes of our project base on the codes of [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics), [GiraffeDet](https://github.com/damo-cv/GiraffeDet), [DAMO-YOLO](https://github.com/tinyvision/DAMO-YOLO), and [BiFormer](https://github.com/rayleizhu/BiFormer) repositories.
