# ⚽ Enhanced Football Player Tracking System (Colab + Drive)

An advanced object tracking system for football videos, built on **YOLOv8**, custom **re-identification networks**, **Kalman filters**, and **Hungarian assignment**. Designed entirely for **Google Colab** using **Google Drive integration**, it ensures players retain consistent IDs even during occlusion or re-entry.

---
>Note: Resource & Source code (Notebook) can be found in [Project folder on Google Drive](https://drive.google.com/drive/folders/1szBJ0ipeNwlAqlVpOjWmbF9ItF4v2i14?usp=sharing)

## 🧩 Project Highlights

- 🎯 YOLOv8 for accurate player & ball detection  
- 🧠 Re-ID with CNN + attention-based feature extractor  
- 🎯 Kalman Filter for motion prediction  
- 🔁 Hungarian Algorithm for ID association  
- 🔄 Multi-frame feature averaging for robust identity persistence  
- 🟡 Color-based team consistency boosting  
- 📦 Fully runs on Google Colab, no local setup needed  

---

## 🔧 Setup (Colab + Google Drive)

### Folder Structure (Inside Google Drive)

```
/My Drive/
└── Stealth Intern Project/
    ├── 15sec_input_720p.mp4       # Input video
    ├── best.pt                    # YOLOv8 fine-tuned weights
    ├── output_id_track05.mp4      # Output video (auto-generated)
```

---

## 🚀 Running the System in Colab
The [Project folder on Google Drive](https://drive.google.com/drive/folders/1szBJ0ipeNwlAqlVpOjWmbF9ItF4v2i14?usp=sharing) contains a google colab notebook called "`Task2.ipynb`" which contains a single cell with all the code at one place, before running it please do set-up your a folder in your google drive with any name, for the sake of this project I am using the root folder name as `Stealth Intern Project` and it contains:
- `best.pt` (model provided for assignment)
- `15sec_input_720p.mp4` (the relevent video clip, the `input`)
Rest files are auto generated.
```python
ROOT_DIR = '/content/gdrive/My Drive/Stealth Intern Project' #here enter the path to your drive folder location
VIDEO_PATH = f'{ROOT_DIR}/15sec_input_720p.mp4'
MODEL_PATH = f'{ROOT_DIR}/best.pt' #model should be inside that folder
OUTPUT_PATH = f'{ROOT_DIR}/output_id_track05.mp4' #if desired, change the output file name

process_enhanced_video(VIDEO_PATH, MODEL_PATH, OUTPUT_PATH)
```

Once set-up run the cell in google colab.
The output video will be saved back to your Google Drive inside the same folder. In my case it saved as `output_id_track05.mp4`.

---

## 📄 Project Report

### 🎯 Approach & Methodology

- **Detection**: YOLOv8 model trained to detect `player` and `ball`
- **Re-ID**: Custom CNN with attention extracts unique 128D features
- **Motion Prediction**: Kalman Filter estimates player location across frames
- **Association**: Hungarian matching based on appearance + motion + color
- **Color Encoding**: Dominant jersey color boosts team-aware tracking
- **Track Recovery**: IDs preserved across occlusions or frame exits

---

### 🔍 Techniques Tried

| Technique                | Outcome                                      |
|--------------------------|----------------------------------------------|
| Cosine similarity        | Worked, but struggled on overlap             |
| Kalman Filter            | Boosted robustness under occlusion           |
| Hungarian Algorithm      | Cleaned up ID switching                      |
| Color-based filtering    | Helped team-based disambiguation             |
| Feature averaging        | Reduced jitter and noise in embedding space  |

---

### ❗ Challenges Faced

- YOLO occasionally missed small players or returned overlapping detections (tried improving this by adding Kalman filter and Hungarian Algorithm)
- Re-ID failure when players wore similar kits and had blurry bounding boxes

---

## 📂 Output Sample (output_id_track05.mp4 file)

✅ Every player is assigned a consistent `Player ID`  
✅ IDs persist even after leaving & re-entering the frame  
✅ Ball is detected and outlined separately  
✅ Frame-by-frame stats (active tracks, progress bar) included

---

## 📁 File Overview

| File/Folder                 | Purpose                                |
|----------------------------|----------------------------------------|
| `15sec_input_720p.mp4`     | Input football video                   |
| `best.pt`                  | YOLOv8 model trained on ball/players   |
| `output_id_track05.mp4`    | Final output video with player IDs     |

---

## 👤 Author

**Vibhor Shukla**  
> Engineering student passionate about computer vision, real-world AI, and high-performance systems.  
> Built this project during the **Stealth Internship Application Process**.

---

## 📜 License

This project is MIT licensed — use it, remix it, and share improvements.
