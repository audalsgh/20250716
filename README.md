# 18일차

## 1. 0716 ImageNet 물체인식 라이브러리 코드 분석 (CNN 필요없음)
<img width="1413" height="792" alt="image" src="https://github.com/user-attachments/assets/e917b6a8-19d1-4f8d-9112-4a073203f3c0" /><br>
역시 200줄 이상의 긴 코드고, 주석을 달아가며 공부해야한다.

<img width="1630" height="802" alt="image" src="https://github.com/user-attachments/assets/691ed75c-596c-4b68-8846-fe3b3d56adda" /><br>
메인함수중 3번째, 여러 파일을 업로드하는 함수를 사용했고, 매 파일마다 시각화하는 부분을 추가했음.

## 2. YOLO와 Ultralytics (울트라리틱스)
교수님의 필기 정리본 링크
[Ultralytics_v8.md](https://github.com/jetsonmom/6.23_automobility_lesson/blob/main/Ultralytics_v8.md)

<img width="837" height="506" alt="image" src="https://github.com/user-attachments/assets/1bfe0c89-cc34-4938-af7f-0f8414806d43" /><br>
YOLOv8의 스몰, 미디엄, 엑스라지까지 성능요약, fps가 가장 중요. 크게 차이난다! 엑스라지는 colab에선 못할것.<br>
YOLOv8을 회사들이 많이 쓰고있고, 더 높은 버전을 쓸수도 있다.<br>

### YOLOv8에 이미지, 비디오를 업로드해보는 예제
- cpu로 하게되면 시간이 오래걸리니 꼭 런타임을 gpu로 선택하자.
<img width="1573" height="719" alt="image" src="https://github.com/user-attachments/assets/ba4044db-e3c5-4138-8bc7-cfde0c1309e0" />

- 이미지 업로드 예제부터 실행해보니, 매우 잘 인식된다.
<img width="1258" height="683" alt="image" src="https://github.com/user-attachments/assets/dac28dd8-2cc7-4a31-88dd-c6fdfa34977b" />
<img width="1816" height="614" alt="image" src="https://github.com/user-attachments/assets/136a19c0-0d42-4946-a132-47292760f3a7" />
<img width="1260" height="515" alt="image" src="https://github.com/user-attachments/assets/fe2bb98c-3b8f-401f-9ee9-658022fb66c5" />

- BoxF1_curve, BoxP_curve 등의 파일 내부를 이해하고 발표해야할수도 있다.
<img width="296" height="787" alt="image" src="https://github.com/user-attachments/assets/42ebc3cc-4611-4388-a957-ace01f921a9b" />
<img width="818" height="572" alt="image" src="https://github.com/user-attachments/assets/d9fefc2a-d87b-476c-8436-7061681d3c4e" />

- args.yaml 파일 내부도 중요하다.
<img width="174" height="504" alt="image" src="https://github.com/user-attachments/assets/498076a4-45f6-47f3-ac9f-74fc6ed83d3b" />

- result.png 도 중요하다.
<img width="816" height="474" alt="image" src="https://github.com/user-attachments/assets/09fdd296-476c-47b4-85c9-d8df2ca2d1c0" />

- COCO 데이터셋을 확인해볼수있고, 모델이 라벨링할때 샘플로 쓰이는 사진들이다.
<img width="292" height="543" alt="image" src="https://github.com/user-attachments/assets/02d620d7-3b40-4b35-85de-0061202d9541" />
<img width="818" height="721" alt="image" src="https://github.com/user-attachments/assets/61da57e8-1b80-4a38-920d-6d7b041079a5" />

- val_batch0_labels.jpg, train_vatch0.jpg 내부엔 샘플사진을 받고 모델이 라벨링해둔 것들을 살펴볼수있다.
<img width="812" height="809" alt="image" src="https://github.com/user-attachments/assets/5ac5c510-1b94-466a-8b6e-9f2e13df80f0" />
<img width="817" height="453" alt="image" src="https://github.com/user-attachments/assets/8acf32c1-1907-42e3-8f6f-0d5b870f8477" />
