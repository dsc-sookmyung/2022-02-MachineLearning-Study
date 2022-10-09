<aside>
✅ 1주차 복습

* Hypothesis - 가설 함수
H(x) = Wx + b

* Cost Function
  (https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9f73d07e-2ea3-4cbe-9c1e-21121d4c0a84/Untitled.png)

예측값과 실제 값의 차이를 제곱 하여 더한 것의 평균

![image](https://user-images.githubusercontent.com/92504386/194769919-9da271d5-2a32-47bf-af01-5b949bad8e95.png)  
* Gradient descent 
: cost가 최소가 되도록 하는 가장 대표적인 방법



예측값과 실제 값의 차이를 제곱 하여 더한 것의 평균

* Gradient descent 
: cost가 최소가 되도록 하는 가장 대표적인 방법

![* Gradient descent



* Gradient descent
: cost가 최소가 되는 w를 구해서 지속적으로 업데이트 하며 cost 최소화를 함.

</aside>

### Lec 04

## Multi variable linear regression (다중변수 선형 회귀)

### 다중 변수 Hypothesis

![image](https://user-images.githubusercontent.com/92504386/194770057-76410f73-eed7-4ea7-9e85-2400e9486c99.png)

- x=변수, w=weight
- tensorflow에서 사용 할 때는 H(x) =XW로 사용 —> matrix의 곱으로 표현해야 하기 때문

---

### Lab05-1

## Logistic Rregression

- Classification
- Regression
    - Logistic : 0 또는 1로 binary classification
        - x input이 들어갔을 때 weight를 곱한 값이 linear하게 수치가 나오는데 이를 logistic function(=g function)을 통해서 0과 1사이의 값으로 나타낼 수 있고 특정 decision boundary를 통해 0과 1의 boundary로 출력해내는 것이 우리가 원하는 Hypothesis임.
        - linear regression G(Z) : g function을 통해서 나온 실수 수치형 값이 sigmoid 함수 를 통해서 0과 1 사이의 값으로 나타낼 수 있게 됨.
            
            ![image](https://user-images.githubusercontent.com/92504386/194770080-1d967aae-b48e-46b0-ae7c-957b16354f5d.png)

    
           
    
    - Linear : 연속적인 수치 데이터
    
    ### sigmoid 함수 / linear function /
    
    ![image](https://user-images.githubusercontent.com/92504386/194770111-577d03f0-f716-4ea9-a4ba-06840266bf54.png)

    
    `predicted  = tf.cast(hypothesis > 0.5, dtype=tf.int32`
    
    - logistic function을 통해 나온 hypothesis의 Decision boundary = 0.5를 가지고 예측
    
    ---
    
    ### Lab05-02
    
    ## Logistic Regression
    
    ### Cost Function
    
    the cost function to fit the parameters(Θ) = weight
    
    모델의 실제 값 - 예측 값 = cost
    
    cost = 0  → 가설 함수를 잘 찾아냄.
    
    ```jsx
    def loss_fn(hypothesis, labels): # label 은 정답
    	cost - tf.reduce_mean(labels * tf.log(hypothesis) + (1- labels) * tf.log(1- hypothesis))
    	return cost
    ```
    
   ![image](https://user-images.githubusercontent.com/92504386/194770123-cccfec83-74c3-4b57-8c6e-b307afb4979e.png)
    
    가설은 sigmoid 함수, 즉 0과 1사이의 실수형 수치 값을 가지는 반면,
    
    실제 원하는 값은 0과 1의 끊어지는 binary 값임
    
    가설과 실제값을 빼면 구불구불 한 함수가 됨.
    
    → 최적의 값을 찾기 위해서는
    
    Convex 한 (볼록한)구조가 되어야 함!! (a convex logistic regression cost function)
    
    가설과 실제 값의 차이
    
    - - log(h(x))         if  y=1
        
          → 구불구불한 값을 로그 함수에 대입함으로써 실제 원하는 값을 얻게 됨. -1을 하면서 x축 대칭을 하게 되고,
        
        0에 가깝다는 말은 cost가 점점 커짐
        
       ![image](https://user-images.githubusercontent.com/92504386/194770146-addc4704-3e1e-4394-93ae-abc2900acd06.png)

        
    - -log(1-h(x))       if y = 0
        
        ![image](https://user-images.githubusercontent.com/92504386/194770155-46ca2c79-0b10-48dd-bdd5-d9a99e7529d3.png)

        
    
    두 수식을 합치면 convex한 구조를 만들어 낼 수 있음.
    
    `cost = tf.reduce_mean(labels * tf.log(hypothesis) - (1-labels)* tf.log(1- hypothes))`
    
    cost함수를 통해서 convex한 구조로 각각의 cost값을 구할 수 있는 함수를 찾음.
    
    ![image](https://user-images.githubusercontent.com/92504386/194770163-df1dd357-6cb0-4003-9e0e-e3cd4850fd38.png)
    
    ## Optimization
    
    **How to minimize the cost function**
    
    기울기가 0이 되는 지점. 
    
    경사값이 이동할 때마다 모델이 계속해서 업데이트 되었을 때 최솟값
    
    (cost값 * learning_rate * gradient 값) ← 반복
    
    : cost함수에 대해서 어떻게 최소화 할 수 있는가
