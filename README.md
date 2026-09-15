# Pre-trained Neural Models for pliman

[![GitHub Release](https://img.shields.io/github/v/release/NEPEM-UFSC/models?color=blue&label=release)](https://github.com/NEPEM-UFSC/models/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![pliman](https://img.shields.io/badge/R%20Package-pliman-brightgreen)](https://github.com/nepem-ufsc/pliman)

This repository hosts pre-trained Deep Learning models in **ONNX** format used by the [**pliman**](https://github.com/nepem-ufsc/pliman) (Plant Image Analysis) R package for background removal, foreground segmentation, open-vocabulary object detection, zero-shot instance segmentation, monocular 3D depth estimation, self-supervised feature extraction, star-convex polygon detection, generative super-resolution, human pose estimation, and image classification.

Models are served via **GitHub Releases** and **Hugging Face** to ensure fast, stable, and permanent downloads worldwide.

---

## 📦 Available Models

### Foundation & Specialized Models

| Model | Filename | Size | Input Size | Task / Architecture | Description |
| :--- | :--- | :---: | :---: | :--- | :--- |
| **`u2netp`** | `u2netp.onnx` | 4.4 MB | 320×320 | Salient Object Detection (U2-Net Portable) | Ultra-lightweight and fast, ideal for quick runs on CPU. |
| **`silueta`** | `silueta.onnx` | 42.1 MB | 320×320 | Compact Matting (U2-Net variant) | High accuracy with low latency for edge & CPU execution. |
| **`u2net`** | `u2net.onnx` | 167.8 MB | 320×320 | Salient Object Detection (U2-Net Full) | Classic robust multi-scale salient object segmentation. |
| **`rmbg-1.4`** | `rmbg-1.4.onnx` | 168.0 MB | 1024×1024 | Background Removal (BRIA AI RMBG 1.4) | High-accuracy foreground segmentation on 1024×1024 images. |
| **`isnet-general-use`** | `isnet-general-use.onnx` | 170.4 MB | 1024×1024 | Boundary Matting (DIS / IS-Net) | Crisp contours; excellent for complex leaf borders and lesions. |
| **`birefnet-lite`** | `birefnet-lite.onnx` | 213.6 MB | 1024×1024 | Dichotomous Image Segmentation (BiRefNet Lite) | High-resolution bilateral reference network for fine structures. |
| **`ben2`** | `ben2.onnx` | 212.6 MB | 1024×1024 | Boundary-Aware Extraction (BEN2 Base) | Crisp sub-pixel boundaries; excellent on leaves, seeds and roots. |
| **`withoutbg`** | `withoutbg.onnx` | 433.4 MB | 448×448 | Depth-Aware Matting (ConvNeXt + DepthAnything) | Robust open-weights matting with depth guidance. |
| **`sam2.1`** (encoder) | `sam2.1.encoder.onnx` | 104.4 MB | 1024×1024 | Foundation Segmentation (Meta AI SAM 2.1 Hiera-Tiny) | Image feature extraction backbone for promptable segmentation. |
| **`sam2.1`** (decoder) | `sam2.1.decoder.onnx` | 15.8 MB | Dynamic | Mask Decoder (Meta AI SAM 2.1) | Generates crisp instance masks from bounding box prompts. |
| **`grounding-dino`** | `groundingdino-tiny.onnx` | 194.4 MB | 800×800 | Open-Vocabulary Object Detection (Grounding DINO) | Text-prompted zero-shot bounding box detector. |
| **`vocab`** | `vocab.txt` | 0.2 MB | — | BERT Vocabulary | Tokenizer vocabulary used for Grounding DINO text prompts. |
| **`sam3.1`** | `sam3.1.onnx` | 868.1 MB | 1024×1024 | Concept-driven Segmentation (SAM 3.1) | Next-generation foundation image segmentation model. |
| **`rmbg-2.0`** | `rmbg-2.0.onnx` | 976.9 MB | 1024×1024 | Next-Gen Matting (BRIA AI RMBG 2.0 / BiRefNet) | State-of-the-art background removal for high-detail inputs. |
| **`depth-anything-v2`** | `depth-anything-v2-small.onnx` | 94.5 MB | 518×518 | Monocular Depth Estimation (Depth Anything V2 Small) | Dense relative 3D depth estimation from a single image. |
| **`dinov2`** | `dinov2-vits14.onnx` | 84.4 MB | 518×518 | Vision Foundation Model (Meta AI DINOv2 ViT-S/14) | Self-supervised dense patch embeddings & semantic PCA mapping. |
| **`stardist`** | `stardist-dsb2018.onnx` | 5.6 MB | 256×256 | Star-Convex Object Detection (StarDist DSB 2018) | Star-convex polygon detection for round/overlapping objects, seeds, and cells. |
| **`realesrgan-compact`** | `realesrgan-compact.onnx` | 4.6 MB | 256×256 | Generative 4× Super-Resolution (Real-ESRGAN Compact) | Fast 4× image upscaling with edge preservation and tiled processing. |

### YOLO26 Suite ([zwh20081/yolo26-onnx](https://huggingface.co/zwh20081/yolo26-onnx))

| Model | Filename | Size | Input Size | Task / Architecture | Description |
| :--- | :--- | :---: | :---: | :--- | :--- |
| **`yolo26n`** | `yolo26n.onnx` | 9.5 MB | 640×640 | Real-Time Object Detection (YOLO26 Nano) | End-to-end 80 COCO classes object detection; ultra-fast CPU inference. |
| **`yolo26s`** | `yolo26s.onnx` | 36.5 MB | 640×640 | Real-Time Object Detection (YOLO26 Small) | Balanced real-time object detector. |
| **`yolo26m`** | `yolo26m.onnx` | 78.2 MB | 640×640 | Real-Time Object Detection (YOLO26 Medium) | Medium-size high-accuracy object detector. |
| **`yolo26l`** | `yolo26l.onnx` | 95.0 MB | 640×640 | Real-Time Object Detection (YOLO26 Large) | High-capacity object detection. |
| **`yolo26x`** | `yolo26x.onnx` | 212.9 MB | 640×640 | Real-Time Object Detection (YOLO26 XLarge) | Maximum precision object detector for complex scenes. |
| **`yolo26n-seg`** | `yolo26n-seg.onnx` | 10.7 MB | 640×640 | Real-Time Instance Segmentation (YOLO26 Nano Seg) | Fast instance segmentation with continuous bilinear mask interpolation. |
| **`yolo26s-seg`** | `yolo26s-seg.onnx` | 40.0 MB | 640×640 | Real-Time Instance Segmentation (YOLO26 Small Seg) | Balanced instance segmentation. |
| **`yolo26m-seg`** | `yolo26m-seg.onnx` | 90.2 MB | 640×640 | Real-Time Instance Segmentation (YOLO26 Medium Seg) | High-precision instance masks and morphological metrics. |
| **`yolo26l-seg`** | `yolo26l-seg.onnx` | 107.1 MB | 640×640 | Real-Time Instance Segmentation (YOLO26 Large Seg) | Large-capacity instance segmentation. |
| **`yolo26x-seg`** | `yolo26x-seg.onnx` | 240.0 MB | 640×640 | Real-Time Instance Segmentation (YOLO26 XLarge Seg) | Highest fidelity instance segmentation and boundary precision. |
| **`yolo26n-pose`** | `yolo26n-pose.onnx` | 11.6 MB | 640×640 | Real-Time Pose Estimation (YOLO26 Nano Pose) | 17 COCO anatomical keypoints and skeleton limb connections. |
| **`yolo26s-pose`** | `yolo26s-pose.onnx` | 39.9 MB | 640×640 | Real-Time Pose Estimation (YOLO26 Small Pose) | Balanced speed/precision keypoint detection. |
| **`yolo26m-pose`** | `yolo26m-pose.onnx` | 82.6 MB | 640×640 | Real-Time Pose Estimation (YOLO26 Medium Pose) | Medium pose estimation model. |
| **`yolo26l-pose`** | `yolo26l-pose.onnx` | 99.4 MB | 640×640 | Real-Time Pose Estimation (YOLO26 Large Pose) | Large-capacity pose estimation model. |
| **`yolo26x-pose`** | `yolo26x-pose.onnx` | 220.0 MB | 640×640 | Real-Time Pose Estimation (YOLO26 XLarge Pose) | Maximum accuracy pose estimation for challenging poses and occlusion. |
| **`yolo26n-cls`** | `yolo26n-cls.onnx` | 10.8 MB | 224×224 | Image Classification (YOLO26 Nano Cls) | Fast 1,000-class ImageNet classification with Softmax probabilities. |
| **`yolo26s-cls`** | `yolo26s-cls.onnx` | 25.7 MB | 224×224 | Image Classification (YOLO26 Small Cls) | Balanced ImageNet classification. |
| **`yolo26m-cls`** | `yolo26m-cls.onnx` | 44.4 MB | 224×224 | Image Classification (YOLO26 Medium Cls) | High accuracy ImageNet classification. |
| **`yolo26l-cls`** | `yolo26l-cls.onnx` | 53.9 MB | 224×224 | Image Classification (YOLO26 Large Cls) | Large ImageNet classification model. |

---

## 🚀 Usage in `pliman`

In R, models can be loaded directly from this directory or downloaded via `pliman_download_model()`:

```r
library(pliman)

# Set model directory (or pass dir = "D:/Desktop/models" to any function)
models_dir <- "D:/Desktop/models"

# Check available models and their download status
pliman_available_models(dir = models_dir)

img <- image_import("leaves.jpg")

# 1. Background removal / foreground segmentation
seg <- image_segment_dl(img, model = "u2netp", dir = models_dir)

# 2. Text-prompted zero-shot instance segmentation (Grounded-SAM)
res <- image_segment_dl(
  img,
  model = "grounded-sam",
  prompt = "leaf",
  type = "highlight",
  bbox = TRUE,
  dir = models_dir
)

# 3. Real-time object detection (YOLO26)
boxes <- image_detect_dl(img, model = "yolo26n", dir = models_dir)

# 4. Real-time instance segmentation (YOLO26-seg)
yolo_seg <- image_segment_dl(img, model = "yolo26n-seg", type = "highlight", dir = models_dir)

# 5. Real-time human pose estimation (YOLO26-pose)
pose_res <- image_pose_dl(img, model = "yolo26n-pose", dir = models_dir)

# 6. Image classification (YOLO26-cls, Top-5 ImageNet classes)
top_cls <- image_classify_dl(img, model = "yolo26n-cls", top_k = 5, dir = models_dir)

# 7. Star-convex polygon detection for seeds, grains, and cells (StarDist)
stars <- image_stardist_dl(img, type = "segment", dir = models_dir)

# 8. Monocular 3D depth estimation (Depth Anything V2)
depth <- image_depth_dl(img, col_palette = "viridis", dir = models_dir)

# 9. Self-supervised feature extraction and semantic PCA mapping (DINOv2)
feats <- image_features_dl(img, dir = models_dir)

# 10. 4x Generative super-resolution (Real-ESRGAN Compact)
sr_img <- image_superres_dl(img, scale = 4, dir = models_dir)
```

---

## 📥 Direct Download Links

### GitHub Releases
All foundational model assets can be downloaded directly from GitHub Releases:
```text
https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/<filename>
```

### Hugging Face (YOLO26 Suite)
The YOLO26 suite is hosted on Hugging Face:
```text
https://huggingface.co/zwh20081/yolo26-onnx/resolve/main/<filename>
```
For example:
* `https://huggingface.co/zwh20081/yolo26-onnx/resolve/main/yolo26n.onnx`
* `https://huggingface.co/zwh20081/yolo26-onnx/resolve/main/yolo26n-seg.onnx`
* `https://huggingface.co/zwh20081/yolo26-onnx/resolve/main/yolo26n-pose.onnx`
* `https://huggingface.co/zwh20081/yolo26-onnx/resolve/main/yolo26n-cls.onnx`

---

## 📜 Acknowledgments & References

These ONNX weights originate from the following foundational works:
* **U2-Net**: Qin et al. (*U2-Net: Going Deeper with Nested U-Structure for Salient Object Detection*, PR 2020).
* **IS-Net / DIS**: Xue et al. (*Highly Accurate Dichotomous Image Segmentation*, ECCV 2022).
* **BiRefNet**: Zheng et al. (*Bilateral Reference for High-Resolution Dichotomous Image Segmentation*, CAAI AIR 2024).
* **RMBG 1.4 & 2.0**: BRIA AI (Commercial and open-weights background removal models).
* **BEN2**: Prama LLC (*Boundary-aware Extraction Network*).
* **withoutBG**: withoutBG Open Weights (*DepthAnythingV2 + ConvNeXt*).
* **Segment Anything 2.1 (SAM 2.1)**: Ravi et al., Meta AI (*SAM 2: Segment Anything in Images and Videos*, 2024).
* **Grounding DINO**: Liu et al. (*Grounding DINO: Marrying DINO with Grounded Pre-Training for Open-Set Object Detection*, 2023).
* **Depth Anything V2**: Yang et al. (*Depth Anything V2: A More Capable Foundation Model for Monocular Depth Estimation*, 2024).
* **DINOv2**: Oquab et al., Meta AI (*DINOv2: Learning Robust Visual Features without Supervision*, TMLR 2024).
* **YOLO26**: zwh20081 / YOLO Community (*End-to-End YOLO26 ONNX Models for Detection, Segmentation, Pose, and Classification*, [Hugging Face](https://huggingface.co/zwh20081/yolo26-onnx)).
* **StarDist**: Schmidt et al. (*Cell Detection with Star-Convex Polygons*, MICCAI 2018).
* **Real-ESRGAN Compact**: Wang et al. (*Real-ESRGAN: Training Real-World Blind Super-Resolution with Pure Synthetic Data*, ICCVW 2021).
