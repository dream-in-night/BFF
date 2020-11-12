## BFF R-CNN: Balanced Feature Fusion for Object Detection ##
**usage：** 

1.install mmdetection

2.put mmdet and config folder under mmdetection，and replace the __init__.py.

3.run with config/BFF.py


**使用方法：** 

1.安装mmdetection

2.将mmdet与config文件复制到对应文件夹，覆盖init文件.

3.config文件选择BFF.py运行

Overview of BFF, It consists of three parts: a, b and c are feature fusion from
the two ends to the center and then to each layer; The red line is recursive
FPN, the feature is returned by B back to the backbone, extracted and then added
to c by FPN; d and f is Multilevel Region of Interest Features Extraction
(MRoIE).

The architecture of Recursive Feature Pyramid (RFP) in our model, 1 is both end
to center feature fusion method, 2 is center to multi-layer feature fusion
method. We extract the feature of the network by reusing backbone.

Experiment on lisa traffic signe dataset and coco dataset

Table 1 Module-wise ablation analysis on Lisa Traffic Sign Dataset

| Method                  | *mAP* | *AP50* | *AP75* | *APs* | *APm* | *APl* |
|-------------------------|-------|--------|--------|-------|-------|-------|
| Baseline                | 65.2  | 76.1   | 74.8   | 66.8  | 71.0  | 70.5  |
| BFP                     | 63.9  | 75.9   | 74.0   | 63.4  | 71.2  | 77.9  |
| BiFPN                   | 58.4  | 70.9   | 69.8   | 55.4  | 65.1  | 83.5  |
| BiFPN\*2                | 49.2  | 59.9   | 58.4   | 49.1  | 56.6  | 78.5  |
| NFPN (ours)             | 66.1  | 77.5   | 75.8   | 65.9  | 72.1  | 75.7  |
| MRoIE + NFPN (ours)     | 67.4  | 78.8   | 77.5   | 68.0  | 74.3  | 76.0  |
| NFPN\*2+ MRoIE (ours)   | 66.0  | 78.1   | 76.4   | 66.2  | 72.5  | 80.7  |
| NFPN +RFP+ MRoIE (ours) | 67.8  | 79.0   | 77.7   | 68.4  | 74.0  | 81.1  |

Table 2 Compared with the Faster RCNN on MS COCO datasets

| Method                                | *mAP* | *AP50* | *AP75* | *APs* | *APm* | *APl* |
|---------------------------------------|-------|--------|--------|-------|-------|-------|
| Baseline                              | 37.4  | 58.1   | 40.4   | 21.2  | 41.0  | 48.1  |
| PANet                                 | 37.5  | 58.6   | 40.8   | 21.5  | 41.0  | 48.6  |
| BEtM(ours)                            | 38.1  | 58.4   | 41.3   | 21.1  | 41.6  | 49.6  |
| BEtM + MRoIE(ours)                    | 39.3  | 60.2   | 42.8   | 23.3  | 42.9  | 50.6  |
| BFF (ours)                            | 39.5  | 60.2   | 42.6   | 23.1  | 42.7  | 50.6  |
| BFF +AWS (ours)                       | 39.6  | 60.1   | 42.6   | 23.4  | 43.3  | 51.5  |
| BFF +AWS and SENet[23] in neck (ours) | 39.5  | 59.8   | 42.4   | 23.4  | 43.5  | 51.4  |

Table 3 Compared experiments apply BFF to other networks

| Method                               | *mAP* | *AP50* | *AP75* | *APs* | *APm* | *APl* |
|--------------------------------------|-------|--------|--------|-------|-------|-------|
| Baseline                             | 37.4  | 58.1   | 40.4   | 21.2  | 41.0  | 48.1  |
| Libra-RCNN                           | 38.7  | 59.9   | 42.0   | 22.5  | 41.1  | 48.7  |
| Grid RCNN                            | 40.4  | 58.5   | 43.6   | 22.7  | 43.9  | 53.0  |
| Guided Anchoring                     | 39.6  | 58.7   | 43.4   | 21.2  | 43.0  | 52.7  |
| GRoIE                                | 37.5  | 59.2   | 40.6   | 22.3  | 41.5  | 47.8  |
| Libra-RCNN + BFF (ours)              | 39.5  | 59.4   | 43.0   | 22.8  | 42.8  | 51.3  |
| Grid RCNN + BFF (ours)               | 40.7  | 59.7   | 43.8   | 24.2  | 44.7  | 52.7  |
| Guided Anchoring + BFF (ours)        | 40.6  | 59.5   | 44.1   | 23.2  | 44.2  | 54.0  |
| GRoIE + BFF (ours)                   | 40.7  | 61.1   | 43.7   | 23.4  | 44.8  | 53.2  |
| Guided Anchoring+ GRoIE + BFF (ours) | 40.9  | 60.4   | 44.7   | 23.9  | 44.2  | 53.7  |

