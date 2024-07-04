# DocLayNet YOLO
Document Layout Detection with YOLOv8n based on the DocLayNet Dataset

## Dataset & Setup

Install dependencies.
```bash
pip install -r requirements.txt
```
Download the DocLayNet dataset and convert to YOLO format.
```bash
cd doclaynet-yolo
wget https://codait-cos-dax.s3.us.cloud-object-storage.appdomain.cloud/dax-doclaynet/1.0.0/DocLayNet_core.zip
mkdir datasets
mv DocLayNet_core.zip datasets/
cd datasets/ && unzip DocLayNet_core.zip && rm DocLayNet_core.zip
cd ../
python convert_dataset.py
```
Add <code>data.yaml</code> to <code>datasets</code> and change <code>path</code> if necessary.
Also change <code>data.yaml</code> path in <code>train.py</code> if necessary: 
```python
datasets: str = "{./datasets/data.yaml}",
```
## Predict

```python
from ultralytics import YOLO

model = YOLO("{path-to-your-model}")
pred = model("{path-to-image}")
print(pred)
```
