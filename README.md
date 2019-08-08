# CarND-02-Neural-Network-Basic
Udacity Self-Driving Car Engineer Nanodegree: Introduction to Neural Network

## Perceptron 

y = setp(w1x1 + w2x2)

- If the point is correctly classified, do nothing.
- If the point is classified positive, but it has a negative label, subtract ...
- If the point is classified negative, but it has a positive label, add ..

```python
def perceptronStep(X, y, W, b, learn_rate = 0.01):
    for i in range(len(X)):
        y_hat = prediction(X[i],W,b)
        if y[i]-y_hat == 1:
            W[0] += X[i][0]*learn_rate
            W[1] += X[i][1]*learn_rate
            b += learn_rate
        elif y[i]-y_hat == -1:
            W[0] -= X[i][0]*learn_rate
            W[1] -= X[i][1]*learn_rate
            b -= learn_rate
    return W, b
```

## Softmax

```python
import numpy as np

def softmax(L):
    expL = np.exp(L)
    sumExpL = sum(expL)
    result = []
    for i in expL:
        result.append(i*1.0/sumExpL)
    return result
```
example:
```
Trying for L=[5,6,7]
expL: [ 148.4131591   403.42879349 1096.63315843]
result: [0.09003057317038046, 0.24472847105479764, 0.6652409557748219]
```
