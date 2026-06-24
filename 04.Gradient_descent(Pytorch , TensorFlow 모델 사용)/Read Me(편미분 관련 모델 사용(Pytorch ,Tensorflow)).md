경사 하강법(Gradient Descent) 실습: PyTorch 편미분 활용
이 프로젝트는 PyTorch를 사용하여 경사 하강법을 자동으로 구현하고, 학습 과정에서 모델의 파라미터(기울기 a, 절편 b)가 어떻게 최적화되는지 학습하는 과정을 담고 있습니다.

목차
데이터 준비

모델 예측 및 오차 계산

PyTorch를 활용한 경사 하강법

학습 결과 및 하이퍼파라미터 비교

1. 데이터 준비
Pandas를 사용하여 기온(temperature)에 따른 떡볶이 판매량(sales) 데이터를 정의하고 데이터프레임으로 시각화합니다.

입력(X): 기온 [10, 7, 4, 0]

출력(Y): 판매량 [30, 50, 60, 80]

2. 모델 예측 및 오차 계산
선형 회귀 모델 H(x) = a * x + b의 초기값을 설정하고, 반복문을 통해 각 데이터별 예측값과 오차(실제값 - 예측값)를 직접 계산해 봅니다.

3. PyTorch를 활용한 경사 하강법
PyTorch의 자동 미분(autograd) 기능을 사용하여 경사 하강법을 구현합니다.

텐서 변환: Pandas 데이터를 PyTorch 텐서로 변환합니다.

학습 파라미터: requires_grad=True 설정을 통해 기울기(a)와 절편(b)에 대한 미분값을 자동으로 계산합니다.

학습 루프(Epoch):

pred = a * x + b: 예측값 계산

cost = torch.mean(error  2): 비용(Cost) 함수 계산 (평균 제곱 오차)

cost.backward(): 기울기 자동 계산

a -= learning_rate * a.grad: 경사 하강법을 통한 파라미터 업데이트

4. 학습 결과 및 하이퍼파라미터 비교
다양한 Learning Rate(학습률)를 실험하여 모델 학습의 안정성을 비교합니다.

비교값: [0.1, 0.01, 0.001, 0.0001]

학습률이 너무 클 경우 Cost가 발산할 수 있음을 확인하고, 적절한 학습률 설정의 중요성을 체감합니다.

환경 설정
실습을 위해 아래 라이브러리 설치가 필요합니다.

Bash
pip install pandas torch matplotlib



----------------------------------------------------------------------------------------------------------


경사 하강법 및 선형 회귀 실습: TensorFlow 2 (Keras) 활용
이 프로젝트는 딥러닝 프레임워크인 TensorFlow 2와 Keras 고수준 API를 사용하여 데이터를 학습하고, 기온에 따른 판매량을 예측하는 선형 회귀 모델을 구축하는 실습을 다룹니다.

목차
데이터 준비

TensorFlow 모델 구축

모델 학습 (Compile & Fit)

결과 시각화 및 예측

1. 데이터 준비
Pandas를 사용하여 기온(temperature)과 판매량(sales) 데이터를 불러옵니다. 모델 학습을 위해 데이터를 NumPy 배열 형태로 변환하여 TensorFlow가 처리할 수 있게 준비합니다.

2. TensorFlow 모델 구축
Keras의 Sequential API를 사용하여 선형 회귀 모델을 정의합니다.

레이어 구성: tf.keras.layers.Dense(units=1, input_dim=1)를 사용하여 단일 뉴런으로 구성된 선형 모델을 만듭니다. 이는 y = ax + b 형태의 수식을 학습합니다.

3. 모델 학습 (Compile & Fit)
모델이 학습할 수 있도록 설정하고 데이터를 주입합니다.

Compile:

optimizer: 경사 하강법의 변형인 SGD(Learning Rate 설정)를 사용합니다.

loss: 오차 측정 지표로 mean_squared_error (평균 제곱 오차)를 사용합니다.

Fit: 모델에 데이터를 전달하여 정해진 횟수(Epoch)만큼 반복 학습을 진행합니다.

4. 결과 시각화 및 예측
시각화: 학습된 모델의 예측선(red)을 실제 데이터(scatter)와 함께 그려 모델의 적합도를 확인합니다.

예측: 학습된 모델에 새로운 입력값(예: 기온 5도)을 넣어 예상 판매량을 계산합니다.

환경 설정
실습을 위해 아래 라이브러리 설치가 필요합니다.

Bash
pip install pandas tensorflow numpy matplotlib