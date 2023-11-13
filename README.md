# 2023_ETRI_openAPI-
CCTV를 통한 도심범죄 및 위급상황 대처 시스템

[요약]

CCTV security 프로젝트는 CCTV, AI와 데이터베이스를 기반인 프로젝트로, 최근 다양한 길거리 사건에서 빠른 대응의 필요성을 느껴 계획하였습니다.

[활용한 API의 종류 및 상세 활동 내용]

○ 객체 검출 API

CCTV 데이터를 통해 실시간으로 추출된 이미지 Input을 통해 공간상의 객체의 정보를 분류하였으며, ‘Person’ 객체를 인지하면 따로 추출된 이미지를 사람 상태 이해 API의 Input으로 사용하였습니다.

○사람 상태 이해 API

객체 검출 API를 통해 ‘Person’ 객체를 인지하였다면, 각 사람의 상태를 분석하였습니다.

[활용사례 결과물의 동작 과정]

1. OpenCV

OpenCV를 통해 실시간으로 CCTV 및 동영상을 이미지로 분할 및 저장합니다.

2. Python

Python을 통해 ETRI 객체 검출 API와 사람 상태 이해 API를 각각의 함수로 정의해서 불러옵니다.

3. 객체 검출 이해 API

저장된 이미지의 객체를 객체 검출 이해 API를 통해 파악하고 분류합니다. 이때 ‘Person’과 ‘Knife’ 등 특정 객체를 따로 저장합니다.

4. 사람 상태 이해 API

따로 저장된 ‘Person’ 객체 이미지는 사람 상태 이해 API를 통해 상태를 파악하고 ‘Lying’과 ‘Crouch’의 상태가 되면 조건문을 통해 따로 저장합니다.

5. FireBase

위와 같이 객체 검출 이해 API에서 인식된 모든 사진은 시간별로 데이터베이스에 저장됩니다. 그 외 조건문에 의해 따로 분류된 이미지는 데이터베이스에 저장됩니다.



![image](https://github.com/jhg8342/2023_ETRI_openAPI-/assets/105159817/5140b0df-6207-42e0-a3df-35446c5a9a1f)

데이터베이스에 다음과 같이 저장됩니다.

6. Python

데이터베이스를 통해 문제시되는 사진을 따로 불러와 기존에 설정하였던 기준치를 넘어서면 사전방지를 위한 조치를 취합니다.

 
![image](https://github.com/jhg8342/2023_ETRI_openAPI-/assets/105159817/6a90234c-a566-4d27-b54c-12f8faa6b214)

전체 프로세스는 다음과 같습니다.

[활용사례 결과물의 독창성 및 우수성]

최근 길거리 위급상황은 늘고 있지만 그에 비해 대처하는 시스템이 부족한 것으로 보입니다. 따라서 길거리 범죄 및 위급상황에 대처할 수 있는 시스템을 좀 더 보완하고 빠른 사전대처가 가능하다면 범죄와 사고를 빠르게 예방할 수 있습니다.

 

[활용사례 결과물의 활용 범위 및 시장성]

서울시 5대범죄 발생장소별 통계에 따라 노상에서 가장 많이 일어나는걸 알 수 있습니다. CCTV의 기술의 발전을 통해 범죄를 사전에 차단하고 발생시 빠른 대처를 통해 안전한 길거리를 만들 수 있습니다.

데이터의 부족으로 범죄에 대한 사전 판단 및 학습이 부족하지만, 많은 데이터를 학습한다면 강도, 절도, 살인과 같은 5대 범죄를 사전에 방지할 수 있습니다. 이를 통해 주택가와 같은 개인의 수요도 증가할 수 있습니다.

[활용 데이터의 종류 및 확보방법]

서울 열린데이터 광장을 통해 2023년 범죄 발생통계와 인구밀도 통계, 인구성장률 통계를 이용하여 선형회귀 학습을 진행하였고, 뉴스를 참조하여 판단기준을 설정하였습니다. 인구밀도가 낮아질수록 범죄율이 희미하게 높아지는 결과를 참조하였습니다.

실제 CCTV 데이터를 여건상 구하지 못하여 컴퓨터상의 동영상 데이터를 가져와 300프레임 단위로 이미지를 추출하였습니다.
