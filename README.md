# Pre-trained Neural Models for pliman

[![GitHub Release](https://img.shields.io/github/v/release/NEPEM-UFSC/models?color=blue&label=release)](https://github.com/NEPEM-UFSC/models/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![pliman](https://img.shields.io/badge/R%20Package-pliman-brightgreen)](https://github.com/nepem-ufsc/pliman)

This repository hosts pre-trained Deep Learning models in **ONNX** format used by the [**pliman**](https://github.com/nepem-ufsc/pliman) (Plant Image Analysis) R package for background removal, foreground segmentation, open-vocabulary object detection, zero-shot instance segmentation, monocular 3D depth estimation, self-supervised feature extraction, star-convex polygon detection, and generative super-resolution.

Models are served via **GitHub Releases** to ensure fast, stable, and permanent downloads worldwide without reliance on external or transient third-party hosts.

---

## 📦 Available Models

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
| **`yolo11n`** | `yolo11n.onnx` | 10.2 MB | 640×640 | Real-Time Object Detection (Ultralytics YOLO11 Nano) | Ultra-fast general object detection with bounding boxes (80 COCO classes). |
| **`yolo11n-seg`** | `yolo11n-seg.onnx` | 11.2 MB | 640×640 | Real-Time Instance Segmentation (Ultralytics YOLO11 Nano Seg) | Fast real-time instance segmentation with bounding boxes and masks. |
| **`stardist`** | `stardist-dsb2018.onnx` | 5.6 MB | 256×256 | Star-Convex Object Detection (StarDist DSB 2018) | Star-convex polygon detection for round/overlapping objects, seeds, and cells. |
| **`realesrgan-compact`** | `realesrgan-compact.onnx` | 4.6 MB | 256×256 | Generative 4× Super-Resolution (Real-ESRGAN Compact) | Fast 4× image upscaling with edge preservation and tiled processing. |

---

## 🚀 Usage in `pliman`

In R, models are downloaded automatically on first use or manually via `pliman_download_model()`:

```r
library(pliman)

# Check available models and their download status
pliman_available_models()

# Download specific models (saved to tools::R_user_dir("pliman", "data")/models)
pliman_download_model("u2netp")
pliman_download_model("ben2")
pliman_download_model("grounded-sam")
pliman_download_model("depth-anything-v2")
pliman_download_model("dinov2")
pliman_download_model("yolo11n")
pliman_download_model("yolo11n-seg")
pliman_download_model("stardist")
pliman_download_model("realesrgan-compact")

img <- image_import("leaves.jpg")

# 1. Background removal / foreground segmentation
seg <- image_segment_dl(img, model = "u2netp")

# 2. Text-prompted zero-shot instance segmentation (Grounded-SAM)
res <- image_segment_dl(
  img,
  model = "grounded-sam",
  prompt = "leaf",
  type = "highlight",
  bbox = TRUE,
  engine = "gpu"
)

# 3. Real-time object detection (YOLO11)
boxes <- image_detect_dl(img, model = "yolo11n")

# 4. Real-time instance segmentation (YOLO11-seg)
yolo_seg <- image_segment_dl(img, model = "yolo11n-seg", type = "highlight")

# 5. Star-convex polygon detection for seeds, grains, and cells (StarDist)
stars <- image_stardist_dl(img, type = "segment")

# 6. Monocular 3D depth estimation (Depth Anything V2)
depth <- image_depth_dl(img, col_palette = "viridis")

# 7. Self-supervised feature extraction and semantic PCA mapping (DINOv2)
feats <- image_features_dl(img)

# 8. 4x Generative super-resolution (Real-ESRGAN Compact)
sr_img <- image_superres_dl(img, scale = 4)
```

---

## 📥 Direct Download Links

All model assets can be downloaded directly from GitHub Releases:

```text
https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/<filename>
```

For example:
* `https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/u2netp.onnx`
* `https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/groundingdino-tiny.onnx`
* `https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/sam2.1.encoder.onnx`
* `https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/sam2.1.decoder.onnx`
* `https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/depth-anything-v2-small.onnx`
* `https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/dinov2-vits14.onnx`
* `https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/yolo11n.onnx`
* `https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/yolo11n-seg.onnx`
* `https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/stardist-dsb2018.onnx`
* `https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/realesrgan-compact.onnx`
* `https://github.com/NEPEM-UFSC/models/releases/download/v1.0.0/vocab.txt`

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
* **YOLO11**: Ultralytics (*YOLO11: State-of-the-Art Real-Time Object Detection and Instance Segmentation*, 2024).
* **StarDist**: Schmidt et al. (*Cell Detection with Star-Convex Polygons*, MICCAI 2018).
* **Real-ESRGAN Compact**: Wang et al. (*Real-ESRGAN: Training Real-World Blind Super-Resolution with Pure Synthetic Data*, ICCVW 2021).