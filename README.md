# 18일차

## 1. 어제 17일차에 주셨던 ImageNet 물체인식 라이브러리 코드 분석 (CNN 필요없음)
<img width="1413" height="792" alt="image" src="https://github.com/user-attachments/assets/e917b6a8-19d1-4f8d-9112-4a073203f3c0" /><br>
역시 200줄 이상의 긴 코드고, 주석을 달아가며 공부해야한다.

<img width="1630" height="802" alt="image" src="https://github.com/user-attachments/assets/691ed75c-596c-4b68-8846-fe3b3d56adda" /><br>
메인함수중 3번째, 여러 파일을 업로드하는 함수를 사용했고, 매 파일마다 시각화하는 부분을 추가했음.

## 2. Ultralytics (울트라리틱스)의 YOLO
교수님의 필기 정리본 링크
[Ultralytics_v8.md](https://github.com/jetsonmom/6.23_automobility_lesson/blob/main/Ultralytics_v8.md)

[Ultralytics 사이트의 YOLO 설명](https://docs.ultralytics.com/ko/models/yolov8/#performance-metrics)

YOLOv8의 스몰, 미디엄, 엑스라지까지 성능요약, fps가 가장 중요. 크게 차이난다! 엑스라지는 colab에선 못할것.<br>
YOLOv8을 회사들이 많이 쓰고있고, 더 높은 버전을 쓸수도 있다.
<img width="837" height="506" alt="image" src="https://github.com/user-attachments/assets/1bfe0c89-cc34-4938-af7f-0f8414806d43" /><br>

| 자주쓰이는 용어 | 설명 |
|------|------|
| backbone | 이미지에서 특징을 추출하는 역할을 하는 CNN 구조 (ex: CSPDarknet, EfficientNet 등) |
| head | 추출된 특징을 바탕으로 객체의 클래스와 위치를 예측하는 부분 |
| image size (imgsz=640) | 입력 이미지의 해상도. 작을수록 속도 빠름, 크면 정확도↑ |
| batch size | 한 번에 처리할 이미지 수. GPU 메모리에 따라 조절 필요 |
| labels | 라벨 정보 파일 (클래스 번호, bounding box 좌표 등이 포함된 .txt 파일) |
| class | 탐지하려는 객체의 종류. ex) 사람, 자동차, 자전거 등 |
| train.py, val.py, predict.py | 각각 학습, 검증, 추론을 수행하는 스크립트 |
| epochs | 전체 데이터를 몇 번 반복해서 학습할지 정함 |
| lr 또는 learning rate | 가중치를 업데이트할 때 변화량 정도. 너무 크면 발산, 너무 작으면 느림 |
| augmentation | 데이터 다양화를 위한 랜덤 회전, 확대 등 (→ 일반화 성능 향상) |
| overfitting | 학습 데이터에 너무 맞춰져서 새로운 데이터에 성능이 떨어지는 현상 |
| conf (confidence) | 객체가 맞을 확률 ex) conf=0.25 이상만 표시 |
| iou (Intersection over Union) | 예측 박스와 실제 박스의 겹치는 정도. 값이 높을수록 정확 |
| NMS (Non-Maximum Suppression) | 겹치는 박스 중 가장 확신 높은 것만 남기고 제거 |
| runs/detect/predict | 추론 결과 이미지/영상이 저장되는 기본 경로 |

```python
model = YOLO("yolov8n.pt")  # 모델 로드
results = model("input.mp4", save=True, conf=0.3, iou=0.5)
```
매개변수 설명                      
- conf : 최소 신뢰도. 낮추면 더 많은 객체 감지하지만 오탐 많아짐
- iou : NMS에서 겹침 허용 정도
- save=True : 결과 이미지 또는 영상 저장 여부
- save_txt=True : 예측 좌표 `.txt` 파일로 저장

## YOLOv8에 이미지, 비디오를 업로드해보는 예제
<img width="785" height="330" alt="image" src="https://github.com/user-attachments/assets/769096e7-6c2b-4dad-a459-eed03baeaece" />

- cpu로 하게되면 시간이 오래걸리니 꼭 런타임을 gpu로 선택하자.
<img width="1573" height="719" alt="image" src="https://github.com/user-attachments/assets/ba4044db-e3c5-4138-8bc7-cfde0c1309e0" />

- 라이브러리 설치시 YOLOv8, v11이 같이 설치된다.
<img width="859" height="243" alt="image" src="https://github.com/user-attachments/assets/a7fb8dc5-d251-42e1-ba70-66b38479566e" />

- COCO8 데이터셋도 인터넷에서 설치되는중.
<img width="1313" height="255" alt="image" src="https://github.com/user-attachments/assets/0c0f9ff7-f811-4d07-9f23-963944df579b" />

- COCO8 예제 데이터셋으로 10회 Epoch 훈련 후, coco8.yaml 경로에 저장
<img width="1576" height="696" alt="image" src="https://github.com/user-attachments/assets/d18a9340-3aef-4bf6-9e31-a4a916e7f66a" />

- 이미지 업로드하여 실행해보니, 신호등의 경우 82퍼센트로 매우 잘 인식된다.
<img width="1258" height="683" alt="image" src="https://github.com/user-attachments/assets/dac28dd8-2cc7-4a31-88dd-c6fdfa34977b" />
<img width="1816" height="614" alt="image" src="https://github.com/user-attachments/assets/136a19c0-0d42-4946-a132-47292760f3a7" />
<img width="1260" height="515" alt="image" src="https://github.com/user-attachments/assets/fe2bb98c-3b8f-401f-9ee9-658022fb66c5" />

- 추론 결과가 담긴 BoxF1_curve, BoxP_curve 등의 파일 내부를 이해하고 발표해야할수도 있다.
<img width="296" height="787" alt="image" src="https://github.com/user-attachments/assets/42ebc3cc-4611-4388-a957-ace01f921a9b" />
<img width="818" height="572" alt="image" src="https://github.com/user-attachments/assets/d9fefc2a-d87b-476c-8436-7061681d3c4e" />

- args.yaml 파일 내부도 중요하다.
<img width="174" height="504" alt="image" src="https://github.com/user-attachments/assets/498076a4-45f6-47f3-ac9f-74fc6ed83d3b" />

- result.png 도 중요하다.
<img width="816" height="474" alt="image" src="https://github.com/user-attachments/assets/09fdd296-476c-47b4-85c9-d8df2ca2d1c0" />

- 다운받은 COCO 데이터셋을 확인해볼수있고, 모델이 라벨링할때 샘플로 쓰이는 사진들이다.
<img width="292" height="543" alt="image" src="https://github.com/user-attachments/assets/02d620d7-3b40-4b35-85de-0061202d9541" />
<img width="818" height="721" alt="image" src="https://github.com/user-attachments/assets/61da57e8-1b80-4a38-920d-6d7b041079a5" />

- val_batch0_labels.jpg, train_vatch0.jpg 내부엔 샘플사진을 받고 모델이 라벨링해둔 것들을 살펴볼수있다.
<img width="812" height="809" alt="image" src="https://github.com/user-attachments/assets/5ac5c510-1b94-466a-8b6e-9f2e13df80f0" />
