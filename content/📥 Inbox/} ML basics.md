---
tags: 🧠️/📥️/🏛️/🟧
source: coursera
publish: true
parent: [[Machine learning]]
aliases: ML basics
type: course
status: 🟧
---

Related: 
URL: <https://www.coursera.org/specializations/machine-learning-introduction>

### 1. [Supervised ML: Regression and Classification](https://www.coursera.org/learn/machine-learning?specialization=machine-learning-introduction)

supervised ML
Unsupervised ML
Linear regression
logistic regression
Cost function
	formula
	visualisation
Loss function
##### [[Gradient descent]]
###### logic
###### implementation-loss fn
###### formulae

repeat until convergence {
$$w=w-\alpha\frac{1}{m}\sum_{i=1}^m(f_{w,b}(x^{(i)})-y^{(i)})\ x^{(i)}$$
$$b=b-\alpha\frac{1}{m}\sum_{i=1}^m(f_{w,b}(x^{(i)})-y^{(i)})$$
}



##### multiple linear regression
![](https://i.imgur.com/Si9L0cs.png)

equation $f_{w,b}=w_1x_1+w_2x_2+...+w_nx_n+b$ 
parameter vector represented by $\vec{w}=[w_1\ w_2\ w_3\ ...\ w_n]$  
$\overrightarrow{X}=[X_1\ X_2\ X_3\ ...\ X_n]$ 
$f_{\vec{w},b}=\vec{w}.\vec{X}+b$ 

>this is not equivalent to multivariate regression.

###### Vectorization
[[Vectorisation]] helps in multiple linear regression
it does this by: 
1. writing code more succinctly and making it more efficient
2. take advantage of modern numerical algebra library's
3. parallel computations when using GPU's. 
  ![](https://i.imgur.com/xqzHGlL.png)

what makes vectorization so fast? 
parallel multiplication and after that one-step summation instead of doing it one-after the other
![](https://i.imgur.com/qtpX1r8.png)

how is this specifically useful for gradient descent? 
![](https://i.imgur.com/PTjbZIQ.png)

###### lab session: 
what is indexing and slicing of arrays :::
- Indexing is the process of accessing an element in a sequence using its position in the sequence (its index). 
- Slicing is the process of accessing a sub-sequence of a sequence by specifying a starting and ending index.
```python
# example of indexing
my_list = ['apple', 'banana', 'cherry', 'date']
print(my_list[0]) # output: 'apple'
print(my_list[1]) # output: 'banana'
print(my_list[-1]) # output: 'date'
print(my_list[4]) # gives error: index must be in bounds of array

# example of sequencing
sequence[start_index:end_index]

# can also be written with following syntax
sequence[start:stop:step]

# leaving start blank is considered as 0, leaving stop blank is considered as the last element in array
```

operations on a single vector:
```python
import numpy as np
a=np.array([1,2,3,4,5])

# on this, the following operations can be performed
b = -a; b=np.sum(a); b=np.mean(a) ; b=a**2; b= 5*a


# and many more
```

operations on 2 vectors: 
```python
a=np.array([1,2,3,4])
b=np.array([5,6,7,8])

# sum
c=a+b

# dot product. using numpy is much faster than for loop iteration
c=np.dot(a,b)
```

Matrices in python
```python
# matrix creation
a=np.zeros((1,5)) # creates 1 vector of shape 5. or , a is a vector of shape (1,5)
b=np.zeros((2,1)) # creates 2 vectors of shape 1

# shape of scalar is ()
```

```python
# matrix operations

# 1.indexing & slicing an element in a matrix
a=np.arrnge(6).reshape(-1,2) # shape of a is (3,2)
a[2,0] # gives 1st element of 3rd vector in 'a'
a[2] # gives 3rd vector in 'a'

a[0, 2:7:1]. # gives 2nd to 7th element with a step of 1 of 1st vector of 'a'. **Note** that the vector a has changed from above.
```

###### Gradient descent for multiple linear regression using vectorization 

notation using vectorized notation
![](https://i.imgur.com/mLwg3g2.png)

![](https://i.imgur.com/nHeBlvy.png)

[![](https://i.imgur.com/hGUUnm5m.png)](https://i.imgur.com/hGUUnm5.png)

###### Lab session mult variable gradient descent implementation
jupyter notebook file [link](https://www.coursera.org/learn/machine-learning/ungradedLab/7GEJh/optional-lab-multiple-linear-regression/lab?path=%2Fnotebooks%2FC1_W2_Lab02_Multiple_Variable_Soln.ipynb): 
training data: 
| Size (sqft) | Number of Bedrooms | Number of floors | Age of Home | Price (1000s dollars) |
| ---- | ---- | ---- | ---- | ---- |
| 2104 | 5 | 1 | 45 | 460 |
| 1416 | 3 | 2 | 40 | 232 |
| 852 | 2 | 1 | 35 | 178 |

##### feature scaling
weight of feature should be inversely proportional to size of feature
![](https://i.imgur.com/dvqpRnp.png)
problem when size of features is too big is when using gradient descent, we might bounce around a lot before coming to the optimal value. The solution is to normalize the features to a reasonable scale. typically 0->1
![](https://i.imgur.com/LwNeDAD.png)

Feature scaling methods: 
1. max normalization: 
	1. divide each feature by its max range
	2. $x_1=\frac{x_1}{2000}$ and $x_2=\frac{x_2}{5}$
2. mean normalization: 
	1. if $300\le x_1 \le 2000$ and $0\le x_2 \le 5$ then after mean normalization, $x_1=\frac{x_1-\mu_1}{2000-300}$ and $x_2=\frac{x_2-\mu_2}{5-0}$  where $\mu_1$ and $\mu_2$ are the mean of training values of $x_1$ and $x_2$ 
3. ==z-score normalization==: most common
	1. Based on standard deviation ($\sigma$) 
	2. $x_1=\frac{x_1-\mu_1}{\sigma_1}$ and $x_2=\frac{x_2-\mu_2}{\sigma_2}$

As a rule of thumb, its better to have the features range between -1 and 1
can ignore those ranges which are close to ideal range, but if large range/extremely small range is there, then go for rescaling
[![](https://i.imgur.com/T658GBOm.png)](https://i.imgur.com/T658GBO.png)
How to check if gradient descent is working, i.e. if converging
[[learning curve]]
![](https://i.imgur.com/Q29tVly.png)
if at any point in the curve, cost increases with increase in # iterations, you have chosen an $\alpha$ that is too big.

how to choose learning rate($\alpha$)
too small--> takes too many iterations
too large--> my not converge
[![](https://i.imgur.com/2uySB1Lm.png)](https://i.imgur.com/2uySB1L.png)

methodology: try out [[Gradient descent]] with a few examples of learning rate, from small to large, and compare learning curves. Start out with the smallest $\alpha$ and move in increments of 3x (suggestion). Note the $\alpha$ for which learning curve shows increases with iterations. 
Select an $\alpha$ as close to the one above without causing increases in iterations.

###### Lab: Feature scaling and learning rate



##### [[Feature engineering]]
it is choosing the right features, or creating new features([[engineered feature]])
[![](https://i.imgur.com/YZb54rNm.png)](https://i.imgur.com/YZb54rN.png)

##### [[Polynomial regression]]
How to fit not just straight lines, but curves to our data: polynomial regression
What is it? ➡️ fitting polynomial equation for thee features, instead of a linear equation
eg. 
When there are features which are multiples of other features, it becomes much more important to scale the features. eg, when considering size, size², size^3 for house price

which features to use and not use-> will be covered in course 2 

##### [[Logistic regression]]
- Introduction : 
	- to be used when the 'answer' to be predicted is binary, i.e. either a `yes` or a `no`. only 2 possible outputs. 
	- though it is called logistic <u>regression</u>, it is essentially binary 'classification'. 
		- class == category ; positive class & negative class. 
	- we call it logistic regression, as when the training samples are represented on a graph, the best fit for a binary classification problem can be better represented by a modified log function
	- decision boundary: detailed later as well. 
	- sigmoid function/logistic function is a good fit for these sorts of problems, with a slight shift. 
		- ![](https://i.imgur.com/gLDnEoH.png)
		- ![](https://i.imgur.com/wK2fLnM.png)
	- Interpretation of logistic regression output
		- $f_{\vec{w}.x+b}(\vec{x})=\frac{1}{1+e^{-(\vec{w}.x+b)}}$ can be thought of as the probability that the class of $\vec{y}$ is 1. eg. if `f` calculated is 0.7, it means the logistic regression model thinks there is a 70% chance that $\hat{y}$ is 1
		- note: in many research papers, you can see $$f_{\vec{w}.x+b}(\vec{x})=P(y=1|\vec{x};\vec{w},b)$$ what this function denotes is the probability of y being 1 given input $\vec{x}$ and parameters $\vec{w}\  and\  b$
	- Lab: logistic regression: 
		```python
		x_train = []
		y_train = []
		w_in= [] # to be determined by the regression
		b_in = 0 # Scalar to be determined by regression
		
		# playing with LR. 
		addpt = plt_one_addpt_onclick( x_train,y_train, w_in, b_in, logistic=True)
		```
	- Decision boundary: 
		- What is it: can be thought of as the point on x post which a decision on weather y is 1 can be made. (it is 0 for the regular sigmoid function)
		- NOTE: $\hat{y}$ represents the prediction, $\vec{y}$ represents the training data. 
		- ![](https://i.imgur.com/PPKAfKh.png)
		- ![](https://i.imgur.com/B68vYZq.png)
		- Non-linear decision boundaries: 
			- ![example](https://i.imgur.com/vOLLUkM.png)
			- ![](https://i.imgur.com/aydol1U.png)
		- lab: 
- cost function for logistic regression
	- ![](https://i.imgur.com/sBm2tXD.png)
	- what about using the same cost function we used for linear regression, the [[squared error cost function]]...
	  ![](https://i.imgur.com/mZmvp7e.png)
	- consider Loss of a single training example to be $L(f_{\vec{w},b}(\vec{x}^{(i)})),y^{(i)})$ which is called the logistic loss function, making overall cost function to be $J(\vec{w},b)=\frac{1}{m}\sum_{i=1}^mL$
	  ![](https://i.imgur.com/fltUIA2.png)
	  ![](https://i.imgur.com/buAeCGe.png)
	- ![](https://i.imgur.com/bAcxuvG.png)
	- Simplified cost function: 
		- simpler way to write so that its easier to implement [[Gradient descent]]
		- $L(f_{\vec{w},b}(\vec{x}^{(i)})),y^{(i)}) =- y^{(i)}(f_{\vec{w},b}(\vec{x}^{(i)}))-(1-y^{(i)})log(1-f_{\vec{w},b}(\vec{x}^{(i)}))$
		- simplified cost function = $J(\vec{w},b)=\frac{1}{m}\sum_{i=1}^mL(f_{\vec{w},b}(\vec{x}^{(i)})),y^{(i)})$
		- This cost function is picked for [[Logistic regression]] because of a statistical concept called [[maximum likelyhood estimation]] so as to get a cost function that is convex
		-  lab session
			```python
			
			def compute_cost_logistic(X, y, w, b):
			    m = X.shape[0]
			    cost = 0.0
			    for i in range(m):
			        z_i = np.dot(X[i],w) + b
			        f_wb_i = sigmoid(z_i)
			        cost +=  -y[i]*np.log(f_wb_i) - (1-y[i])*np.log(1-f_wb_i)
			             
			    cost = cost / m
			    return cost
			```
			```python
			# This is just a representation of decision boundary. dont need to keep it, can remove.
			import matplotlib.pyplot as plt
			
			# Choose values between 0 and 6
			x0 = np.arange(0,6)
			
			# Plot the two decision boundaries
			x1 = 3 - x0
			x1_other = 4 - x0
			
			fig,ax = plt.subplots(1, 1, figsize=(4,4))
			# Plot the decision boundary
			ax.plot(x0,x1, c=dlc["dlblue"], label="$b$=-3")
			ax.plot(x0,x1_other, c=dlc["dlmagenta"], label="$b$=-4")
			ax.axis([0, 4, 0, 4])
			
			# Plot the original data
			plot_data(X_train,y_train,ax)
			ax.axis([0, 4, 0, 4])
			ax.set_ylabel('$x_1$', fontsize=12)
			ax.set_xlabel('$x_0$', fontsize=12)
			plt.legend(loc="upper right")
			plt.title("Decision Boundary")
			plt.show()
			```
			- ![](https://i.imgur.com/xqJBG9f.png)
- Gradient descent for logistic regression
	- aim: find parameters {w,b} that Minimize cost function J. 
		- then, given a new person(given his tumor size and age), the model should be able to predict weather the tumor is malignant or not. 
	- same [[Gradient descent|GD]] formula can used for linear regression, but need to keep in mind that f has changed. 
		- monitoring [[Gradient descent|GD]] (learning curve) and vectorized implementation and feature scaling remains the same. 
		- lab: =
- [[Overfitting]] and under-fitting & regularization
	-  what is it
		- examples in regression and classification
	- how to fix it
		- get more data. 
		- feature selection
			- when not possible to get more training samples, select features to include/exclude. --feature selection.
				- disadvantage of feature selection: useful features could be lost. 
		- Regularization: 
			- reduce size of parameters: encourage the algo to shrink weights of parameters instead of 0, thereby eliminating features. 
			- 
			- 







### 2. [Advanced Learning Algorithms](https://www.coursera.org/learn/advanced-learning-algorithms?specialization=machine-learning-introduction)
### 3. [Unsupervised ML:  Recommenders, Reinforcement Learning](https://www.coursera.org/learn/unsupervised-learning-recommenders-reinforcement-learning?specialization=machine-learning-introduction)