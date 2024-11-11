# Yolov8_colab_image
<b> 사진 하나를 다운로드 받아서 1.jpg로 저장한 후 yolov8에서 이미지 detect를 하는 과정


``` bash
%pip install ultralytics opencv-python-headless matplotlib

from google.colab import files

uploaded = files.upload()
filename = next(iter(uploaded))

!mkdir -p /content/sample_data
!mv {filename} /content/sample_data/{filename}

from ultralytics import YOLO
from IPython.display import Image, display

model = YOLO('yolov8n.pt')

image_path = '/content/sample_data/1.jpg'

results = model.predict(image_path)

first_result = results[0]
first_result.save()
saved_image_path = '/content/results_1.jpg'
display(Image(saved_image_path))
```
![results_1](https://github.com/user-attachments/assets/992284b9-95c0-4ae5-902f-cdda1cd485d3)
