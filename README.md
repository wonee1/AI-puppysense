# PuppySense 🐶  
강아지 감정 분류 AI 모델

---

## 📌 개요

반려견의 감정을 이미지 기반으로 분류하기 위한 인공지능 모델을 설계하고 학습한 과정이 담겨 있습니다.  
EfficientNetB4 기반의 딥러닝 모델을 사용하여 강아지의 감정을 다음과 같은 5가지 범주로 분류합니다:

- happy
- angry
- sad
- relaxed

---

## 🧠 주요 내용

### 1. 데이터 전처리 및 불균형 처리
- 이미지 크기: 224x224로 통일
- 클래스 불균형 문제를 완화하기 위해 데이터 증강(`ImageDataGenerator`) 적용
- class weight 자동 계산 적용

### 2. 모델 구성
- `EfficientNetB4`를 베이스 모델로 사용 (`include_top=False`, `trainable=True`)
- 최상위에 GlobalAveragePooling → Dense → Dropout → Softmax 구조 추가
- Dropout과 L2 정규화를 통해 과적합 완화

### 3. 모델 학습
- Optimizer: `Adam`
- Loss: `categorical_crossentropy`
- EarlyStopping 및 ModelCheckpoint 콜백 사용
- Class weight 적용한 학습 진행

### 4. 평가 및 시각화
- Accuracy 및 Loss 시각화 (학습/검증)
- Confusion Matrix를 통한 클래스별 정확도 분석

---

## 🛠 사용된 기술

- Python, Keras, TensorFlow
- EfficientNetB4 (pretrained on ImageNet)
- scikit-learn, matplotlib


---

## 🔍 과적합 방지 전략

- Dropout 비율 증가
- 이미지 증강(Data Augmentation)
- EarlyStopping 콜백
- L2 Regularization
- Validation Set 기반 학습 모니터링

---

## 📂 참고

- 본 노트북은 PuppySense 프로젝트의 모델 학습 파트입니다.
- API 및 서버 배포 관련 정보는 [Puppysense_BE 저장소](https://github.com/wonee1/Puppysense_BE)를 참고해주세요.


