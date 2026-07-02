# TensorFlow/Keras 기반 퍼셉트론 이진 분류 실습
본 실습은 기존의 PyTorch 방식에서 벗어나, 딥러닝 프레임워크인 TensorFlow 2 및 Keras의 Sequential 모델을 사용하여 이진 분류(Binary Classification) 모델을 간편하게 구축하고 학습하는 방법을 다룹니다.

## 🛠 주요 학습 내용
 1. Sequential API 활용: Keras의 Sequential 모델을 사용하여 레이어를 순차적으로 쌓아 올리는 모델 설계 방식을 익힙니다.

 2. 모델 컴파일(Compilation): model.compile()을 통해 손실 함수(BinaryCrossentropy)와 최적화 도구(SGD)를 설정하는 과정을 학습합니다.

 3. 프레임워크 간 비교: PyTorch에서 수동으로 구현했던 Forward 계산 및 학습 루프를 Keras의 model.fit() 메서드가 어떻게 자동화하는지 확인합니다.

 4. 텐서 연산 및 예측: TensorFlow 텐서(tf.Tensor)를 활용한 데이터 처리 및 모델의 predict 과정(sigmoid 적용 등)을 실습합니다.

## 🚀 학습 순서
  1. 환경 설정: 데이터 전처리 및 모델 학습을 위해 필요한 tensorflow, numpy, pandas 라이브러리를 임포트합니다.

  2. 데이터 준비: 실습용 데이터를 정의하고, Keras 모델이 학습할 수 있는 적절한 형태(텐서)로 변환합니다.

  3. 모델 설계: tf.keras.Sequential을 선언하고, Dense 레이어를 추가하여 퍼셉트론 구조를 정의합니다.

  4. 모델 컴파일 및 학습: 손실 함수와 학습률을 설정한 뒤, model.fit()을 호출하여 학습을 진행합니다.

  5. 예측 및 평가: 학습된 모델에 새로운 입력을 전달하고, tf.sigmoid를 적용하여 확률값을 계산한 뒤 농구선수 여부를 판별합니다.

## 💡 이번 실습의 핵심 포인트
▶  간결한 인터페이스: Keras는 복잡한 반복문을 직접 작성하지 않고도 fit() 함수 하나로 모델 학습을 수행할 수 있어 생산성이 매우 높습니다.

▶  직관적인 구조: model.add(tf.keras.layers.Dense(1))와 같은 방식으로 레이어를 추가하여 모델을 점진적으로 확장하기 쉽습니다.

▶  학습 관리: set_seed를 통해 모델의 초기 가중치 생성 과정을 동일하게 유지하여 실험의 재현성을 확보합니다.