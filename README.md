# ⚡ CNN-LSTM 기반 BLDC 모터 초기 고장진단 시스템


## 🎯 연구 목표
> **"멀티센서 데이터 + CNN-LSTM = BLDC 모터 초기 베어링 이상 자동 진단"**

- BLDC 모터의 **소리, 진동, IMU 데이터**를 수집  
- 시계열 신호를 전처리 (슬라이딩 윈도우, FFT)  
- **CNN-LSTM 하이브리드 모델**로 고장 여부 분류  
- ROS2 기반 **실시간 고장 진단 시스템** 구현


## ⚙️ 시스템 아키텍처
<p align="center">
  <img src="images/system_architecture.png" width="720" alt="System Architecture">
</p>
- **센서**: Sound (TS0223), Vibration (VIB100), IMU (WT901)  
- **데이터 전처리**: 슬라이딩 윈도우, 정규화, 랜덤 시프팅, FFT 변환  
- **모델 구조**: CNN으로 공간 패턴 추출 → LSTM으로 시간 의존성 학습  
- **실시간 진단**: ROS2 토픽 통신 기반 Publisher/Subscriber  


## ✨ 주요 기능
✅ **멀티센서 데이터 수집 (Sound, Vibration, IMU)**  
✅ **시간 + 주파수 도메인 입력 (10채널)**  
✅ **CNN-LSTM 하이브리드 딥러닝 모델**  
✅ **97% 정확도의 초기 베어링 이상 진단**  
✅ **ROS2 기반 실시간 Fault Detection**  


## 🧪 실험 결과
- BL3640A-24V-06P 모터, RA35 감속기, BLC-22H06P 컨트롤러  
- 센서 3종 → Arduino 시리얼 통신 → CSV 저장 → 모델 학습  

**전처리**
- Sliding Window (VIB=512, Sound=256, accX/Z=256, accY=128)  
- 랜덤 시프팅 증강 + FFT 변환  

**결과**
- **테스트 정확도: 97.42%**  
- 혼동행렬 기준, 정상/소리/진동/IMU Fault 모두 높은 분류 성능  

<p align="center">
  <img src="images/confusion_matrix.png" width="500" alt="Confusion Matrix">
</p>



