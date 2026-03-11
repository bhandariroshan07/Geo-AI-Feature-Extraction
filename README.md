# Geo-AI Feature Extraction

This repository explores the intersection of Deep Learning and Remote Sensing. By leveraging **Semantic Segmentation**, the project automates the extraction of complex features from aerial and satellite imagery, focusing specifically on urban infrastructure and precision agriculture.

---

## Core Methodology: Semantic Segmentation
In Geospatial AI, we move beyond simple object detection (bounding boxes) to **Semantic Segmentation**. This process involves pixel-level classification, where every pixel in a satellite image is categorized. This allows for:
* **Geometric Precision:** Capturing the exact shape and area of features.
* **Boundary Integrity:** Differentiating between touching objects, such as adjacent buildings or overlapping field boundaries.

---

## 1. Building Footprint Extraction (NAIP)
**Objective:** Identification of residential and commercial structures from high-resolution aerial data.

* **Data Source:** NAIP high-resolution imagery processed into $256 \times 256$ patches.
* **Spectral Depth:** Utilized a **4-channel input (RGB + Near-Infrared)**. The NIR channel is critical for distinguishing between non-photosynthetic roofing materials and surrounding vegetation.
* **Model Architecture:** A custom **U-Net** enhanced with Batch Normalization and Dropout layers to ensure the model remains robust against urban shadows and varied architectural styles.
* **Optimization:** Trained on 1,748 image-mask pairs using a **Hybrid BCE + Dice Loss**. This combination helps the model converge effectively despite the class imbalance between building pixels and background.
* **Performance:** Achieved a **Validation IoU of 0.88**, resulting in highly accurate geometric footprints.
* **Visual Insight:**
    ![Building Detection](Results/Building%20Detection/Visualization_on_test/viz_sample_11.png)

---

## 🌿 2. Cotton Crop Identification (Sentinel-2)
**Objective:** Mapping cotton field boundaries using multi-spectral satellite constellations.

* **Data Source:** Sentinel-2 imagery ($256 \times 256$ patches).
* **Spectral Depth:** Leveraged **RGB + Near-Infrared** bands to isolate the unique spectral signatures of cotton foliage against soil backgrounds.
* **Model Architecture:** Custom **U-Net** designed for high-sensitivity feature extraction in agricultural contexts.
* **Training Strategy:** Developed on 1,597 samples using a 70/20/10 split. The workflow utilized `ReduceLROnPlateau` and `EarlyStopping` to fine-tune the learning rate and prevent overfitting during the final stages of convergence.
* **Performance:** Achieved a **Validation IoU of 0.93**, demonstrating exceptional sensitivity to irregular field patches and narrow boundaries.
* **Visual Insight:**
    ![Cotton Detection](Results/Cotton%20Detection/Visualization_on_test/viz_sample_143.png)

---

## 📊 Key Performance Indicators
For Geo-AI tasks, we focus on the most meaningful metrics for spatial accuracy:
1.  **Intersection over Union (IoU):** Our primary metric, measuring the spatial "overlap" between predictions and ground truth.
2.  **F1-Score:** Used to ensure a balance between Precision (not misidentifying features) and Recall (capturing all features).
3.  **Hybrid Loss:** Utilized to maintain "clean" boundaries, ensuring the masks aren't just accurate in count, but accurate in shape.

---

## 🛠️ Tech Stack
* **Frameworks:** TensorFlow, Keras
* **Geospatial Libraries:** GDAL, OSR, Rasterio
* **Image Processing:** OpenCV, NumPy, PIL
* **Environment:** Google Colab (GPU Accelerated)

---

## 📂 Repository Structure
```text
Geo-AI-feature-extraction/
├── Building_Detection_final.ipynb   # Building segmentation pipeline
├── Cotton_Detection_final.ipynb     # Cotton identification pipeline
├── README.md                        # Project documentation
└── results/                         # Visualization & performance assets
    ├── Building Detection/
    │   └── test_visualization.png   # Model output (NAIP)
    └── Cotton Detection/
        └── test_visualization.png   # Model output (Sentinel-2)
