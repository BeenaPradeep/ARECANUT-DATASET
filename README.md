# Arecanut Disease Detection Field Image Dataset (6-Class)

## Abstract
This dataset contains field images of arecanut (Areca catechu L.) collected for developing and evaluating deep-learning models for automatic disease detection. Images were captured in arecanut plantations in Karnataka, India (Chikkamagaluru district). In total, the dataset comprises approximately 300 RGB images. All images were taken under natural field conditions using drone, handheld digital camera, and smartphone cameras, covering a range of illumination, backgrounds, and viewpoints to reflect realistic farm scenarios. Each image is manually assigned to one of six classes based on visible symptoms on leaves or nuts: Healthy leaf, Healthy nut, Fruit rot, Bud rot, Yellow leaf, and Ring spot.

## Classes (6)
- healthy_leaf
- healthy_nut
- fruit_rot
- bud_rot
- yellow_leaf
- ring_spot

> Note: If your files/folders use different spellings (e.g., “yellow leaf disease” or “mahali/fruit rot”), keep them consistent everywhere (folders + CSV).

## Recommended dataset layout
```
arecanut-disease-dataset/
  README.md
  DATA_DICTIONARY.md
  LICENSE.txt
  CITATION.txt
  images/
    <class_name>/*.jpg
  annotations/
    labels.csv
    metadata.csv          # optional
    splits.csv            # optional
```

## Required annotation file: annotations/labels.csv
Minimum columns:
- image_id
- file_path
- class_label

Optional columns (recommended):
- split (train/val/test)
- site (e.g., Chikkamagaluru)
- capture_device (drone / smartphone / digital_camera + model)
- capture_date (YYYY-MM-DD)
- notes

## How to load (example)
### Folder-per-class loading (torchvision ImageFolder)
If images are arranged as `images/<class_name>/*.jpg`:

```python
from torchvision import datasets, transforms

tfm = transforms.Compose([
    transforms.Resize((256, 256)),
    transforms.ToTensor(),
])

ds = datasets.ImageFolder("images", transform=tfm)
print(ds.classes)
```

### CSV-driven loading
Use `annotations/labels.csv` when you want explicit splits or metadata. Load the CSV and read images from `file_path`.

## Data collection summary
- Location: Chikkamagaluru district, Karnataka, India
- Capture conditions: natural field environments (variable illumination, backgrounds, viewpoints)
- Capture platforms: drone, handheld digital camera, smartphone cameras
- Labeling: manually assigned to one of six classes based on visible symptoms

## Contact
- Maintainer: [BEENA K, VTU]
- Contact email: [binakantharaj@gmail.com]
- Version: v1.0
- Last updated: 2025-12-16
