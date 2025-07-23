# 👁️ Face Detection and Tracking with TensorFlow

This project builds a face detection and tracking model using custom-labeled images and TensorFlow/Keras. It uses OpenCV for webcam input and labelme for annotation.

---

## 🚀 Setup Instructions

### 1. Create a Virtual Environment

```bash
python -m venv facenv
facenv\Scripts\activate   # On Windows
# Or
source facenv/bin/activate  # On macOS/Linux

pip install tensorflow==2.10.0
pip install opencv-python==4.6.0.66
pip install labelme==5.2.1
pip install matplotlib==3.5.3
pip install albumentations==1.3.0
pip install numpy==1.23.5
```

3. Folder Setup

Create the following folder structure manually:

<img width="718" height="898" alt="image" src="https://github.com/user-attachments/assets/61f583b1-98d1-4c75-ac6a-0f9c8516e797" />

🧠 Dataset Preparation
🏷️ Step 1: Label Images with LabelMe

    Launch LabelMe using:

labelme

Once open:

    Go to File → Change Output Directory and select: data/labels

    Go to Edit → Create Rectangle

    Draw a rectangle around the face

    Enter any class name (e.g., face) and save

Each image will generate a corresponding .json file in data/labels/.

🗂️ Step 2: Organize Images

    Place all ~90 original images in data/images.

    Manually copy the images into:

    data/Train/images → ~63 images
    data/Test/images  → ~14 images
    data/Val/images   → ~13 images

    🚫 Do not copy labels/ into Train/Test/Val – label mapping is handled via code.

📁 Step 3: Augmentation Folder Setup

Create the following structure under aug_data/:

    aug_data/
      ├── Train/images + labels
      ├── Test/images + labels
      └── Val/images + labels

These folders will be automatically filled using the augmentation code in the notebook. No need to manually place images here.

📷 Webcam Configuration

The script uses your webcam to track faces in real-time using:

cap = cv2.VideoCapture(0)

    0 is your default camera ID (usually laptop cam)

    If nothing shows or errors occur, test with other IDs: 1, 2, etc.

    Use trial and error to find your working device index

🚀 Model Training & Execution

    Open and run all cells in FaceDetection.ipynb.

        Covers data loading, preprocessing, augmentation, model creation, training, and webcam detection.

    After training, the model is saved as facetracker.h5.

    You can then test the real-time face detection using the webcam interface at the end of the notebook.

    Exit the webcam window by pressing Q.

✅ Tips & Best Practices

    Ensure no other app is using the webcam while running detection.

    Label data with consistency to boost model accuracy.

    Try training in short cycles and iterate quickly with a small dataset (~90 images is a good start).

📦 Requirements Summary
    📦 Requirements Summary
        Library	Version
        Python	3.9.4
        TensorFlow	2.10
        NumPy	1.23.5
        OpenCV-Python	4.6.0.66
        Albumentations	1.3.1
        Matplotlib	Latest
        LabelMe	Latest

    ⚡ Ensure compatible CUDA 11.2 and cuDNN 8.1 for GPU acceleration.

📮 Contributions

Feel free to open issues or pull requests to improve this project. Feedback and enhancements are welcome!
