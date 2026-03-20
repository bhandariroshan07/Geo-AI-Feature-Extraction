# Cotton Patch Prediction (Geo-AI)

This folder contains the necessary resources to perform cotton field feature extraction using Deep Learning and Raster imagery.

---

## Required Files for Prediction

To run the prediction successfully, you must have these three files in your local folder:

### 1. The AI Model (`final_cotton.h5`)
* **Source:** Already included in this GitHub folder.
* **Description:** Pre-trained model (20 MB) for cotton segmentation.

### 2. The Test Image (Raster .tif)
* **Source:** **Download Externally** (Due to large file size).
* **Download Link:** 🔗 **[Direct Download: Test Image Zip]([https://drive.google.com/uc?export=1GfBpXrhqpsxBcch00szlu9OcVHTAQ9uV](https://drive.google.com/uc?export=download&id=1GfBpXrhqpsxBcch00szlu9OcVHTAQ9uV&confirm=t))**
* **Instruction:** Extract the `.zip` file after downloading and move the `.tif` file into this folder.

### 3. The Prediction Notebook (`pCotton_segmentation_with_test_data`)
* **Source:** Already included in this GitHub folder.
* **Description:** Python notebook containing the code to load the model and process the image.

---

## 📂 Local Folder Structure

Before running the code, ensure your local directory is organized as follows:

```text
your_folder_in_your_computer/
├── final_cotton.h5          <-- (Already here)
├── Cotton_segmentation_with_test_data.ipynb    <-- (Already here)
├── test_raster_image.tif    <-- (Extracted from your Zip download)
