# Characteristic of Satellite Data
- 위성 이미지와 에어본 이미지는 비슷한 특징을 가진다.
- 위성 종류는 다양한데 -> 날씨, 지리, 군사, 환경, 농업 등 다양한 용도에서 활용된다.
- 고해상도 및 정밀한 데이터의 경우, 허가가 필요한 경우가 많다.
- 대표적인 우리 위성으로는 KOMSAT이 있다.
- 산, 도심, 강 등 지형적 특징을 파악할 수 있다.
- 재난, 산불, 홍수, 지진 등 재난 상황을 파악하고 예측하는데 활용된다.
- 추가적으로 코로나 영향 분석에도 활용되었다.
- 센서로는 passive 센서인 optical 센서뿐만 아니라, active 센서인 micro-wave 센서 (e.g. SAR image)도 있다.

### Resolutions
- 공간 해상도(Spatial resolution): 위성이 찍은 이미지의 픽셀 크기
- 스펙트럼 해상도(Spectral resolution): 위성이 찍은 이미지의 스펙트럼의 범위
- 시간 해상도(Temporal resolution): 위성이 찍은 이미지의 시간 간격
- 레디오메트릭 해상도(Radiometric resolution): 위성이 찍은 이미지의 에너지 수준(반사율)에 대한 해상도 (e.g. 8bit, 16bit 이를 다루는 데 있어 연산량이 증가하기 때문에, 중요도가 떨어질 수 있다.)

### Preprocessing
- 위성 이미지는 resolution으로 부터 오는 제약이 있기 때문에, preprocessing이 매우 중요한 분야이다.
- Image resampling: 이미지의 해상도를 변경하는 작업 (속도, 분석 성능, 저장 공간 등을 고려하여 결정)
- Pansharpening: 고해상도 panchromatic 이미지와 저해상도 다중 스펙트럼 이미지를 결합하여 고해상도 다중 스펙트럼 이미지를 생성하는 작업
- Super-resolution: 저해상도 이미지를 고해상도 이미지로 변환하는 작업
- Atmospheric correction: 대기 중의 먼지, 습기 등으로 인한 산란, 흡수 등을 보정하는 작업
- Geometric correction: 위성 이미지의 기하학적 왜곡을 보정하는 작업
- Orthorectification: 지구 표면의 기하학적 왜곡을 보정하는 작업
