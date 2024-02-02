# 골연령 예측 프로젝트 / BoneAge Prediction Project
소아/청소년의 왼손 X-ray 사진을 이용해서 뼈 나이를 예측

## 개발 환경
python colab jupyter tensorflow pytorch ...

## 프로젝트 설명
소아/청소년의 왼손 X-ray 이미지 데이터를 활용하여 골연령을 예측합니다. 왼쪽 손목과 손가락 관절 X-ray를 ROI(Region Of Interest)로 Object Detection 하여 골 연령을 예측합니다. 예측된 골연령과 질병관리청에서 제공된 '소아 청소년 성장도표'를 활용하여 18세 기준 예상 신장을 도출합니다.

## 프로젝트 절차
### 데이터 통합 및 전처리
성별, 나이대로 분류되어 있는 이미지와 엑셀 데이터를 통합하고, 전처리 과정을 진행했습니다.
No.값 중에 114_F, 268_F, 185_M가 중복된 값으로 존재했습니다. 114_F, 268_F는 모든 컬럼이 중복되는 데이터로 1개씩 삭제하였습니다. 185_M는 서로 다른 사람의 데이터이므로, 186_M X-ray 이미지 데이터와 정보가 동일한 행의 No.값을 186_M으로 변경하였습니다.

### 이미지 전처리
마스크 생성, 배경삭제, 손목을 기준으로 회전, 이진화분류, 뼈 강조, 테두리 생성

### 라벨링 처리
TW3기법 기반으로 객체(=roi)를 라벨링 처리

### yolov5 학습
yolov5 모델로 학습

### 딥러닝 모델 학습
Tjnet 모델로 학습

### 신장 예측
질병관리청에서 제공된 '소아 청소년 성장도표'를 활용하여 18세 기준 예상 신장을 도출
