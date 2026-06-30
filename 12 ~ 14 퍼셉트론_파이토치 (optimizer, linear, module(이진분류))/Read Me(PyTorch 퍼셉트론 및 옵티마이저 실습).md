# PyTorch 퍼셉트론 및 옵티마이저 실습
본 실습은 PyTorch의 핵심 기능인 자동 미분(Autograd)과 옵티마이저(Optimizer, torch.optim.SGD)를 활용하여, 수동으로 가중치와 편향을 업데이트하던 기존 방식을 자동화하는 과정을 담고 있습니다.

## 🛠 주요 학습 내용
1. 데이터 정규화: 키(cm) 데이터를 평균과 표준편차를 사용하여 정규화((X - mean) / std)하고 학습에 최적화된 형태로 변환.

2. Tensor와 Autograd: requires_grad=True 설정을 통해 학습 가능한 파라미터(a, b)를 정의하고, PyTorch의 자동 미분 기능을 체험.

3. Optimizer 사용: torch.optim.SGD를 사용하여 반복문 내에서 가중치와 편향을 자동으로 업데이트하는 과정 구현.

4. 학습 루프 설계: zero_grad() -> forward(H, z) -> Cost 계산 -> backward() -> step()으로 이어지는 PyTorch의 표준 학습 루프 
   (Training Loop)를 완성.

5. 예측 모델링: 학습된 가중치를 사용하여 새로운 입력 데이터(키)에 대한 확률을 계산하고 농구선수 여부를 판별.

## 🚀 학습 순서
  1. 입력 데이터 준비: 넘파이 배열을 사용하여 입력값 X와 정답 y 정의.

  2. 데이터 정규화: 학습 성능 향상을 위한 데이터 스케일링.

  3. 학습 설정: learning_rate와 epochs 설정.

  4. 옵티마이저 생성: SGD 알고리즘을 사용해 a, b 파라미터 관리.

  5. 학습 루프 실행: 1,000번의 반복 학습을 통해 Cost를 최소화.

  6. 모델 예측: 185cm인 사용자의 농구선수 확률 예측 및 결과 확인.

## 💡 주요 포인트
▶ optimizer.zero_grad(): 이전 에폭의 기울기(gradient) 초기화 (누적 방지).

▶ mean_cost.backward(): 가중치와 편향에 대한 미분값 자동 계산.

▶ optimizer.step(): 저장된 기울기를 바탕으로 가중치와 편향 업데이트.