# Yolov8_colab_image
<b> 사진 하나를 다운로드 받아서 1.jpg로 저장한 후 yolov8에서 이미지 detect를 하는 과정
     이 코드는 YOLOv8을 사용하여 이미지에서 객체를 감지하는 Google Colab 코드입니다. 한 줄씩 설명해드리겠습니다:

%pip install ultralytics opencv-python-headless matplotlib
1. 필요한 라이브러리들을 설치합니다
ultralytics (YOLO 모델용)
opencv-python-headless (이미지 처리용)
matplotlib (시각화용)

2. Google Colab에서 파일 업로드 기능을 사용합니다
사용자가 파일을 업로드하면 그 파일의 이름을 가져옵니다

from google.colab import files
uploaded = files.upload()
filename = next(iter(uploaded))


3. sample_data 디렉토리를 만듭니다
업로드된 파일을 이 디렉토리로 이동시킵니다

!mkdir -p /content/sample_data
!mv {filename} /content/sample_data/{filename}


4.
from ultralytics import YOLO
from IPython.display import Image, display

YOLO 모델을 사용하기 위한 import
결과를 표시하기 위한 display 기능을 import

5.
model = YOLO('yolov8n.pt')

YOLOv8 nano 모델을 로드합니다
'yolov8n.pt'는 사전 훈련된 모델 파일입니다

6.
image_path = '/content/sample_data/1.jpg'

분석할 이미지의 경로를 지정합니다

7.
results = model.predict(image_path)

지정된 이미지에 대해 객체 감지를 수행합니다

8.
first_result = results[0]
first_result.save()

첫 번째 결과를 가져와서 저장합니다
결과 이미지에는 감지된 객체가 박스로 표시됩니다

9.
saved_image_path = '/content/results_1.jpg'
display(Image(saved_image_path))

저장된 결과 이미지의 경로를 지정하고
결과 이미지를 화면에 표시합니다


10. 이 코드의 주요 목적은:

이미지를 업로드하고
YOLO 모델을 사용해 이미지 내의 객체들을 감지하고
감지된 객체들이 표시된 결과 이미지를 보여주는 것입니다


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
