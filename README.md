# 객체인식을 이용한 해양생물 실시간 정보제공 시스템  

## 프로젝트 개요  
- 객체인식을 통한 해양 생물 정보제공 시스템
  - 주제 : 객체인식을 통한 해양 생물 정보 제공 시스템  
  
          모든 사람들이 해양 생물에 대한 지식이 풍부하지 않음.   
          해양 생태계에 대한 다양한 정보 제공
  - 구현내용 : 해양 생물 분류
  
          객체 인식을 통하여 대분류, 소분류해주는 2가지 모델을 만들어 분류함.(YOLOv4모델을 기반으로 구현)
          
## 프로젝트 수행 절차 및 방법
1. Data
- 아쿠아리움 Dataset

![스크린샷_20221211_054631](https://user-images.githubusercontent.com/113493695/206894528-03cedcb2-c006-47ba-a0ed-068af7bc0ed2.png)

- 상어 Dataset

![스크린샷_20221211_054848](https://user-images.githubusercontent.com/113493695/206894602-947fb604-30b0-47f8-9f07-5208c3b37dfe.png)

2. Fish Recognition Model Training
- 아쿠아리움 Dataset "Ignore_threshold: handling (YOLOv4)

![스크린샷_20221211_055124](https://user-images.githubusercontent.com/113493695/206894686-1ddb0435-a701-4c4f-a610-8f96f7052bf4.png)

- 아쿠아리움 Dataset “IoU_threshold” handling (YOLOv4)

![스크린샷_20221211_055235](https://user-images.githubusercontent.com/113493695/206894728-ed1b2d10-72e3-4a0e-970a-e40c5e652d6b.png)

- 아쿠아리움 Dataset (YOLOv5)

![스크린샷_20221211_055405](https://user-images.githubusercontent.com/113493695/206894937-0d6eaf99-602f-403d-8c51-c020a6e016a5.png)

- 아쿠아리움 Dataset (YOLOv6)

![스크린샷_20221211_055850](https://user-images.githubusercontent.com/113493695/206894991-8087d122-bfa0-4012-83e9-2e9d6c6cee9f.png)

- 상어 Datast 추가 이유

![스크린샷_20221211_055952](https://user-images.githubusercontent.com/113493695/206895038-663fb59f-56f9-40c3-ada1-3dbf72ccf527.png)

상어 class의 accuracy가 매우 낮은 것을 확인

- 아쿠아리움 Dataset + 상어 Dataset model handling (YOLOv4)

![스크린샷_20221211_055525](https://user-images.githubusercontent.com/113493695/206895097-76813a34-d363-427e-b2a8-f5afad09c23d.png)

    Anchors_Default : 12, 16, 19, 36, 40, 28, 36, 75, 76, 55, 72, 146, 142, 110, 192, 243, 459, 401  
    After_handling : 10, 13, 16, 30, 33, 23, 30, 61, 62, 45, 59, 119, 116, 90, 156, 198, 373, 326

- 아쿠아리움 Dataset + 상어 Dataset (without Mosaic) (YOLOv4)

![스크린샷_20221211_055558](https://user-images.githubusercontent.com/113493695/206895317-b90d7840-fb18-4805-b0f9-30d04af3fa28.png)

- 어종 객체 인식 모델 결과

![스크린샷_20221211_055614](https://user-images.githubusercontent.com/113493695/206895375-4589a54c-521c-4ccf-a211-a48662ab54c5.png)

3. Shark Recognition Model Training

- 상어(classes 4) Dataset "Ignore_threshold: handling (YOLOv4)

![스크린샷_20221211_055644](https://user-images.githubusercontent.com/113493695/206895450-7bdbcb16-d24c-4d61-b840-837758657dc0.png)

- 상어(classes 4) Dataset “IoU_threshold” handling (YOLOv4)

![스크린샷_20221211_055654](https://user-images.githubusercontent.com/113493695/206895480-eaedbe7e-5612-431c-8a81-6c8364110363.png)

## 프로젝트 수행 결과

- Dataset : 증강 이미지 4700(원본 638)  
- Class : 7 (물고기, 상어, 불가사리, 해파리, 펭귄, 가오리, 바다오리)  
          Dataset이 충분하지 않고 Dataset Balance가 맞지 않았지만 mAP 77% 정도로 나쁘지 않게 나왔다고 판단   

- Class Balance와 Data 양, 해상도 문제르 해결 한다면 사용화 가능한 모델 개발이 가능하다고 판단

- 활용가능 분야
   - 수중활동 보조 장비로서 활용 (다이빙 컴퓨터 or 방수 Mobile Phone 활용) 위험 생물 인식 모델을 추가 개발하여 기존 모델과 병행 사용하면 위험한 해양생물 인식기능을 추가된 수중활동 보조 장비로서 활용가능.  
   - 해양 생태 연구 자료 수집 방법으로 활용 (설치형 카메라 통한 어족자원 조사 등)

