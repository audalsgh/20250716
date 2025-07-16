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

**YOLOv8에 이미지, 비디오를 업로드해보는 예제**
- cpu로 하게되면 시간이 오래걸리니 꼭 런타임을 gpu로 선택하자.
<img width="1573" height="719" alt="image" src="https://github.com/user-attachments/assets/ba4044db-e3c5-4138-8bc7-cfde0c1309e0" />

-이미지 업로드 예제부터 실행해보니, 매우 잘 인식된다.
<img width="1258" height="683" alt="image" src="https://github.com/user-attachments/assets/dac28dd8-2cc7-4a31-88dd-c6fdfa34977b" />
<img width="1816" height="614" alt="image" src="https://github.com/user-attachments/assets/136a19c0-0d42-4946-a132-47292760f3a7" />
<img width="1260" height="515" alt="image" src="https://github.com/user-attachments/assets/fe2bb98c-3b8f-401f-9ee9-658022fb66c5" />

