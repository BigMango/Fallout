# 官方

```
ultralytics/cfg/models
|-- README.md
|-- rt-detr
|   |-- rtdetr-l.yaml                   # 百度的 RT-DETR 目标检测模型（L 规格），使用的后处理模块为 Detect，使用的预测特征图为 P3, P4, P5
|   |-- rtdetr-x.yaml                   # 百度的 RT-DETR 目标检测模型（X 规格），使用的后处理模块为 Detect，使用的预测特征图为 P3, P4, P5
|   |-- rtdetr-resnet101.yaml           # Backbone 使用 ResNet101 的 RE-DETR 目标检测模型，使用的后处理模块为 Detect，使用的预测特征图为 P3, P4, P5
|   `-- rtdetr-resnet50.yaml            # Backbone 使用 ResNet50  的 RE-DETR 目标检测模型，使用的后处理模块为 Detect，使用的预测特征图为 P3, P4, P5
|-- v3
|   |-- yolov3.yaml                     # YOLOv3 目标检测模型，使用的后处理模块为 Detect，使用的预测特征图为 P3, P4, P5
|   |-- yolov3-tiny.yaml                # YOLOv3 目标检测模型（Tiny 规格），使用的后处理模块为 Detect，💡  使用的预测特征图为 P4, P5，从原来擅长“小中大”目标变为“中大”目标
|   `-- yolov3-spp.yaml                 # 加入 SPP 的 YOLOv3 目标检测模型，使用的后处理模块为 Detect，使用的预测特征图为 P3, P4, P5
|-- v5
|   |-- yolov5.yaml                     # YOLOv5 目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Detect，使用的预测特征图为 P3, P4, P5
|   `-- yolov5-p6.yaml                  # YOLOv5-p6 目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Detect，💡  使用的预测特征图为 P3, P4, P5, P6，加强对大目标的检测能力
|-- v6
|   `-- yolov6.yaml                     # YOLOv6 目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Detect，使用的预测特征图为 P3, P4, P5
|-- v8
|   |-- yolov8.yaml                     # YOLOv8 目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Detect，使用的预测特征图为 P3, P4, P5
|   |-- yolov8-p2.yaml                  # YOLOv8 目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Detect，使用的预测特征图为 P2, P3, P4, P5，增加对小目标的检测能力
|   |-- yolov8-p6.yaml                  # YOLOv8 目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Detect，使用的预测特征图为 P3, P4, P5, P6，增加对大目标的检测能力
|   |-- yolov8-ghost.yaml               # YOLOv8 目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Detect，使用的卷积是 GhostConv 和 C3Ghost，使用的预测特征图为 P3, P4, P5
|   |-- yolov8-ghost-p2.yaml            # YOLOv8 目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Detect，使用的卷积是 GhostConv 和 C3Ghost，使用的预测特征图为 P2, P3, P4, P5，增加了对小目标的检测能力
|   |-- yolov8-ghost-p6.yaml            # YOLOv8 目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Detect，使用的卷积是 GhostConv 和 C3Ghost，使用的预测特征图为 P3, P4, P5, P6，增加了对大目标的检测能力
|   |-- yolov8-cls.yaml                 # YOLOv8 分类模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Classify
|   |-- yolov8-cls-resnet50.yaml        # YOLOv8 分类模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Classify，使用的 Backbone 为 ResNet50
|   |-- yolov8-cls-resnet101.yaml       # YOLOv8 分类模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Classify，使用的 Backbone 为 ResNet101
|   |-- yolov8-seg.yaml                 # YOLOv8 分割模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Segment，使用的预测特征图为 P3, P4, P5
|   |-- yolov8-seg-p6.yaml              # YOLOv8 分割模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Segment，使用的预测特征图为 P3, P4, P5, P6，增加对大目标的分割能力
|   |-- yolov8-obb.yaml                 # YOLOv8 旋转目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 OBB，使用的预测特征图为 P3, P4, P5
|   |-- yolov8-pose.yaml                # YOLOv8 关键点/人体姿态估计模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Pose，使用的预测特征图为 P3, P4, P5
|   |-- yolov8-pose-p6.yaml             # YOLOv8 关键点/人体姿态估计模型（可选规格有：n、s、m、l、x），使用的后处理模块为 Pose，使用的预测特征图为 P3, P4, P5, P6，增加对大目标的估计能力
|   |-- yolov8-rtdetr.yaml              # YOLOv8 加上 RT-DETR 的目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 RTDETRDecoder，使用的预测特征图为 P3, P4, P5
|   |-- yolov8-world.yaml               # YOLOv8 加上 YOLO-World 的目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 WorldDetect，head 部分与 YOLOv8 差异较大，使用的预测特征图为 P3, P4, P5，❌ 不支持导出为 ONNX，mAP 低于 YOLOv8-Worldv2
|   `-- yolov8-worldv2.yaml             # 🌟  YOLOv8 加上 YOLO-World 的目标检测模型（可选规格有：n、s、m、l、x），使用的后处理模块为 WorldDetect，head 部分与 YOLOv8 差异较大，与 YOLOv8-World 也有一些区别，使用的预测特征图为 P3, P4, P5，✅ 支持导出为 ONNX，mAP 高于 YOLOv8-World
`-- v9
    |-- yolov9c.yaml                    # YOLOv6 目标检测模型（规格为 C，t->s->m->c->e），使用的后处理模块为 Detect，使用的预测特征图为 P3, P4, P5
    `-- yolov9e.yaml                    # YOLOv6 目标检测模型（规格为 E，t->s->m->c->e），使用的后处理模块为 Detect，使用的预测特征图为 P3, P4, P5
    |-- yolov9c-seg.yaml                # YOLOv6 分割模型（规格为 C，t->s->m->c->e），使用的后处理模块为 Segment，使用的预测特征图为 P3, P4, P5
    `-- yolov9e-seg.yaml                # YOLOv6 分割模型（规格为 E，t->s->m->c->e），使用的后处理模块为 Segment，使用的预测特征图为 P3, P4, P5

```

## 命令行工具
```
yolo TASK MODE ARGS
```
[YOLO最全标注教学-分类、检测、分割、关键点、OBB旋转框](https://www.bilibili.com/video/BV1NTsEeEED7)
* Task
```
* 检测(detect)
* 分割(segment)
* 分类(classify)
* 姿势(pose)
* 旋转目标(OBB)
```



obb

train
val
predict
export
track
benchmark
