# 1주차

**Lec 01. 기본적인 Machine Learning의 용어와 개념 설명**

<aside>
✅ Supervised learning

: learning with labeled examples

- Image labeling
- Email spam filter
- Predicting exam score

Unsupervised learning

: un-labeled data

Training data set

: feature ‘x’의 value ‘y’ label을 가지고 모르는 x에 대해서 value를 예측하기 위한 데이터 셋

</aside>

# Supervised learning

: Training data set을 가지고 훈련하여 feature value를 예측함

Regression

Binary classification 

multi-label classification

---

**Lec 02. Linear Regression의 Hypothesis와 cost 설명**

Regression : 학습 데이터를 기반으로 수치적 예측을 하는 것

Linear Regression : 데이터에 맞는 linear한 선을 찾는 것

<aside>
✅ H(x) = Wx + b

</aside>

Which hypothesis is better? 

⇒ W와 b의 최적 값을 찾아내기!!

## Cost Function = Loss Function

- minimize cost(W, b)
![image](https://user-images.githubusercontent.com/92504386/193465906-e3ce86bc-d4d3-41eb-a8b7-7effed8fc743.png)


H(x) - y  (*m은 데이터 개수)

: 실제 값과 가설 값의 차를 계산하여 제곱하고 이를 최소화 하는 w, b 구하기

제곱을 함으로써 차이가 많이 날 때, 패널티를 부여할 수 있다는 장점이 있음.

---

**Lec 03. Linear Regression, How to minimize cost**

# Gradient descent algorithm

: 비용(손실) 최소화 알고리즘

weight값을 계속적으로 업데이트 하는 알고리즘.

- 변수가 여러개여도 사용가능함
- 최초의 추정(랜덤 값)을 통해 시작
- 최소점에 도달했다고 판단 될 때까지 점차 감소하도록 함.

Initial weight 한 지점을 잡고 Incremental Step을 통해서 minimum cost를 찾는다.

경사를 따라 내려오면서 최저점을 찾음 ⇒ 미분을 통해 구함.

![image](https://user-images.githubusercontent.com/92504386/193465937-cc67664a-1810-4beb-935e-f58d43d2eb60.png)

> 기존 1/m에서 1/2m을 하는 이유 ⇒ 미분을 할 때 지수 승 2가 내려와서 약분 계산하기 편하도록 하기 위함.
> 
![image](https://user-images.githubusercontent.com/92504386/193465954-045e7bde-e13a-4c65-a82e-12010beab537.png)
> cost function을 미분 한 값을 w에서 빼고 w로 업데이트 하면서 반복
알파 = learning rate(학습율) , 알파 값의 크기에 따라 W의 업데이트 속도가 결정됨.
> 

![image](https://user-images.githubusercontent.com/92504386/193465975-fe641bf6-d51f-492f-ac35-6ac0eeed8054.png)

W : Gradient descent algorithm
