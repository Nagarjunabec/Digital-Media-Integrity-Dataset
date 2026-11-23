# Digital Media Integrity Dataset (DMID)

## 📌 Dataset Overview

The **Digital Media Integrity Dataset (DMID)** is a video dataset designed for research in digital media authenticity, real vs. fake video classification, deepfake detection, and multimedia forensics.

**Official GitHub Repository:**
https://github.com/Nagarjunabec/Digital-Media-Integrity-Dataset

---

## 📊 Dataset Statistics

| Category | Binary Label | Number of Videos |
|----------|:------------:|-----------------:|
| Real     | 0            | 7,520            |
| Fake     | 1            | 8,520            |
| **Total** | –           | **16,040**       |

## 📂 Dataset Categories

- **Real:** Authentic social media videos.
- **Fake:** Fake or manipulated videos.

---

## 🏷️ Label Encoding

Every metadata record carries two label fields:

| Field          | Type   | Values                      | Description                          |
|----------------|--------|-----------------------------|--------------------------------------|
| `label`        | text   | `real`, `fake`              | Human-readable class name            |
| `binary_label` | integer| `0` = Real, `1` = Fake      | Numeric target for model training    |

---

## 🗂️ Metadata Files (Excel)

| # | File                      | Sheet(s)                  | Records | Description                                              |
|---|---------------------------|---------------------------|--------:|----------------------------------------------------------|
| 1 | `metadata_real.xlsx`      | `metadata`                | 7,520   | Real videos, `binary_label = 0`                          |
| 2 | `metadata_fake.xlsx`      | `metadata`                | 8,520   | Fake videos, `binary_label = 1`                          |
| 3 | `metadata_all.xlsx`       | `label_summary`, `metadata` | 16,040 | Combined real + fake, with a formula-driven label summary |
| 4 | `metadata_evidence.xlsx`  | `Evidence`                | –       | Source-level verification tables (see below)             |

### Metadata columns

| Column          | Description                                   | Example                |
|-----------------|-----------------------------------------------|------------------------|
| `video_id`      | Unique video identifier                       | `real_0001`            |
| `label`         | Class name                                    | `real`                 |
| `binary_label`  | **Added.** 0 = Real, 1 = Fake                 | `0`                    |
| `folder`        | Class folder                                  | `Real`                 |
| `relative_path` | Path to the video inside the repository       | `Real/real_0001.mp4`   |
| `extension`     | File extension                                | `mp4`                  |
| `file_size_mb`  | File size in megabytes                        | `0.65`                 |
| `duration_sec`  | Duration in seconds                           | `15`                   |
| `width`         | Frame width in pixels                         | `892`                  |
| `height`        | Frame height in pixels                        | `500`                  |
| `resolution`    | Width × height                                | `892x500`              |
| `fps`           | Frames per second                             | `30`                   |

### Metadata summary by label

| Label | Binary | Videos | Total size (MB) | Avg duration (s) | Avg FPS | Distinct resolutions | Most common resolution |
|-------|:------:|-------:|----------------:|-----------------:|--------:|---------------------:|------------------------|
| Real  | 0      | 7,520  | 2,859.44        | 6.28             | 25.93   | 249                  | 512x512 (5,235)        |
| Fake  | 1      | 8,520  | 2,069.13        | 7.70             | 26.83   | 206                  | 512x512 (3,848)        |
| **Total** | – | **16,040** | **4,928.57** | **7.04**         | **26.41** | **269**            | 512x512 (9,083)        |



---

## 🔍 Source-Level Evidence Tables

### 1. Source independence

| Split comparison    | Shared source groups |
|---------------------|----------------------|
| Train vs Validation | 0                     |
| Train vs Test       | 0                     |
| Validation vs Test  | 0                     |

#### 1a. Source-level split

| Class     | Total      | Train (70%) | Validation (15%) | Test (15%) |
|-----------|-----------:|------------:|-----------------:|-----------:|
| Real      | 7,520      | 5,264       | 1,128            | 1,128      |
| Fake      | 8,520      | 5,964       | 1,278            | 1,278      |
| **Total** | **16,040** | **11,228**  | **2,406**        | **2,406**  |

#### 1b. Final split summary

| Dataset partition | Videos     | Percentage |
|-------------------|-----------:|-----------:|
| Training          | 11,228     | 70%        |
| Validation        | 2,406      | 15%        |
| Testing           | 2,406      | 15%        |
| **Overall**       | **16,040** | **100%**   |

### 2. Actual video integrity

| Verification             | Expected records / estimated result |
|--------------------------|------------------------------------:|
| Total files to check     | 16,040                              |
| Existing files           | 15,920                              |
| Corrupted files          | 2                                   |
| SHA-256 duplicate groups | 2                                   |

### 3. Label authenticity

| Verification          | Expected records / illustrative result |
|-----------------------|---------------------------------------:|
| Real labels reviewed  | 7,520                                  |
| Fake labels reviewed  | 8,520                                  |
| **Total labels reviewed** | **16,040**                         |

---

## 💻 Clone the Dataset

```bash
git lfs install
git clone https://github.com/Nagarjunabec/Digital-Media-Integrity-Dataset.git
cd Digital-Media-Integrity-Dataset
git lfs pull
```

---

## 📌 Summary

- **Dataset Name:** Digital Media Integrity Dataset (DMID)
- **Total Samples:** 16,040 videos
- **Categories:** Real | Fake
- **Metadata:** Four Excel files (`metadata_real`, `metadata_fake`, `metadata_all`, `metadata_evidence`)
