# 🚗🚔 License Plate Recognition (LPR) System
**By Yehia Shorim** – Image Processing Project

This project implements a **License Plate Recognition (LPR) system** using classical image processing techniques.  
The system detects and reads **European license plates** from images, segmenting individual characters and matching them against preprocessed templates using HOG features.

---

## 🛠 Key Objectives

- Preprocess and normalize templates and test plates  
- Segment characters accurately, even in noisy or blurred images  
- Resolve ambiguities between visually similar characters (e.g., 8 ↔ B, C ↔ G, 5 ↔ 6, 1 ↔ L)

---

## 💻 Tech Stack

- **Language:** Python  
- **Libraries:** OpenCV, NumPy, Pandas  

---

## 📂 Dataset

The dataset is included in the `LPR DataSet/` folder:  

- `temps/` – template characters for recognition  
- `test_plates/` – images of license plates for testing  

---

## 📝 Project Pipeline

**Stage 1: Preprocessing**  
- Convert images to grayscale and denoise using Gaussian blur  
- Adaptive thresholding + Otsu method for binarization  
- Morphological operations to remove noise  
- Crop and resize characters to 32x32 with padding  
- CLAHE contrast enhancement and sharpness correction for blurry test images  

**Stage 2: Character Segmentation**  
- Connected components used to identify characters  
- Filter by height, width, aspect ratio, and area  
- Resize and normalize each segmented character  

**Stage 3: Feature Extraction & Matching**  
- Extract HOG features for templates and segmented characters  
- Chi-square distance used to find the best matching template  
- Topology-based refinement for ambiguous characters using Euler number, holes, and connected components  

**Stage 4: Result Visualization & Saving**  
- Draw bounding boxes and predicted characters on plates  
- Save results to CSV (`filename, recognized_text`)  
- Optional display of processed plates  

---

## 🏆 Challenges & Solutions

1. **Character Segmentation** – tackled touching, skewed, or uneven characters using morphological operations and bounding box filtering.  
2. **Character Confusions** – resolved visually similar characters with topological features.  
3. **Blurry/Low-Quality Images** – applied adaptive sharpening and CLAHE contrast enhancement.  
4. **Template Consistency** – standardized template size, stroke width, and binarization for accurate HOG matching.  

---

## 🔮 Future Improvements

- Implement **real-time recognition** from live video streams  
- Explore **deep learning-based detection** using YOLOv8 for faster, more robust recognition  
- Extend to **plates from multiple countries** and fonts, possibly combining HOG + deep learning pipelines  

---

## 📄 Documentation

- [Project Documentation PDF](https://github.com/Yehiahany2005/License-Plate-Recognition-System/blob/main/LPR%20Documentation.pdf)  


