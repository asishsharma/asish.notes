# Jupyter notebooks


## M1
### 1.1 **FINANCIAL DERIVATIVE BASICS**



|  |  |
|:---|:---|
|**Reading Time** |  75 minutes |
|**Prior Knowledge** | Options, financial derivatives basics  |
|**Keywords** |Option, Call, Put, Risk-neutral probabilities, Real-world probabilities, No-arbitrage argument, Binomial model |


---


*Here you have the first Jupyter Notebook of your Derivative Pricing course.*
*We will use this format throughout the whole course in order to do a proper mapping of the theoretical concepts in the slides/videos to the hands-on development of the ideas.* 

*In this notebook, we will develop a function in Python in order to construct a simple binomial tree. Make sure you understand this properly because it is going to set the foundation for future work.* 


Let's start importing some of the libraries that we may need to use down the road:
```python
import numpy as np
```

In order to compute the binomial tree  in the video/slides of Lesson 1, we need a bunch of input data: upward movement (**u**), downward movement (**d**), risk-free rate (**$r_f$**), time-horizon (**T**), and number of steps in the tree (**N**).

All these would be user-inputs to our function. However, there is one input that we need to consider with caution: the **time-step**. That is, how long does moving from one node to the next one in the tree represent in terms of time?

In our baseline example on the slides the time-horizon for the evolution of the underlying (T) was equal to 1 year. There was 1 step in the tree (N=1). Therefore, there were no doubts that the time-step needed to be equal to 1. 

What if we want a different number of steps, or the time-horizon for the evolution of the underlying is different?
In those cases, the time-step ($dt$) we use for our binomial model will be $→$ $dt = T/N$.

Although we have not yet introduced the utility to specify $dt$, you will realize soon that $dt$ will be helpful for the calculation of risk-neutral probabilities.

#### 1.1.1. Constructing a Binomial Tree


In the following code snippet, you have the code for a general function to simulate the underlying stock price for some inputs: initial stock price (`S_ini`), time-horizon ($T$), upward ($u$) and downward ($d$) movements, and number of steps (N).
```python
def binomial_tree(S_ini, T, u, d, N):
    S = np.zeros([N + 1, N + 1])  # Underlying price
    for i in range(0, N + 1):
        S[N, i] = S_ini * (u ** (i)) * (d ** (N - i))
    for j in range(N - 1, -1, -1):
        for i in range(0, j + 1):
            S[j, i] = S_ini * (u ** (i)) * (d ** (j - i))
    return S
```
Note that we store everything in a variable, $S$, the one returned by the function. This variable will contain an array with the values of the stock price at each point in time in a lower triangular matrix.

Let's check it by replicating the same tree for $N=2$ that you have in the Lesson 1 slides:
```python
Stock = binomial_tree(100, 1, 1.2, 0.8, 2)
Stock
```
#### 1.1.2. Extending the Tree with Call Option Payoffs

Next, let's extend the previous function by adding another variable that computes the payoffs associated with a Call Option of certain characteristics. Note that we are focusing on a European Call Option with strike price $K=90$, and therefore the payoff is only computed at maturity:
```
def binomial_tree_call(S_ini, K, T, u, d, N):
    C = np.zeros([N + 1, N + 1])  # Call prices
    S = np.zeros([N + 1, N + 1])  # Underlying price
    for i in range(0, N + 1):
        C[N, i] = max(S_ini * (u ** (i)) * (d ** (N - i)) - K, 0)
        S[N, i] = S_ini * (u ** (i)) * (d ** (N - i))
    for j in range(N - 1, -1, -1):
        for i in range(0, j + 1):
            S[j, i] = S_ini * (u ** (i)) * (d ** (j - i))
    return S, C
```
It is easy to see that the variable $C$ output by the function will return Call Option payoff at maturity. We can verify this by replicating the simple N=1 tree with Call option payoff from the Lesson 1 slides:
```
Stock, Call = binomial_tree_call(100, 90, 10, 1.2, 0.8, 10)
print("Underlying Price Evolution:\n", Stock)
print("Call Option Payoff:\n", Call)
```
#### 1.1.3. Introducing Risk-Neutral Probabilities and backward induction of Call Option Value

For the final part of this notebook, let's work with the risk-neutral probabilities. Once we have the probabilities, we can, by backward induction, calculate the value of the Call Option (given its future payoffs and the associated probabilities) at each node.

Importantly, once we know the risk-neutral probabilities, the value of the Call Option at each node will depend on the expected payoff in the two potential future scenarios (up or down movements), discounted at risk-free. That is:

$C_{t}= e^{-rdt}[p c_{t+1}^u + (1-p) c_{t+1}^d]$

where $dt$ is the discounted period from one node to the next (**time-step**), and $c_{t+1}^u$ and $c_{t+1}^d$ are the **values of the Call option in the next period**. We will therefore have to start from the last period (maturity) and work backwards, hence the term backward induction.

Note that we use $dt$ here because we are assuming there are a **bunch of periods (steps) in the tree from the initial date until maturity of the option**. Under the 1-step case, we can calculate risk-neutral probabilities as we did in the videos, because $dt=T/N = 1/1 = 1 = T$:

$p=\frac{e^{rT}-d}{u-d}$

Once we consider a different $dt$, we just need to modify $p$ accordingly:

$p=\frac{e^{rdt}-d}{u-d}$

Now, let's write a final function that recognizes all these issues.
```
def binomial_call_full(S_ini, K, T, r, u, d, N):
    dt = T / N  # Define time step
    p = (np.exp(r * dt) - d) / (u - d)  # Risk neutral probabilities (probs)
    C = np.zeros([N + 1, N + 1])  # Call prices
    S = np.zeros([N + 1, N + 1])  # Underlying price
    for i in range(0, N + 1):
        C[N, i] = max(S_ini * (u ** (i)) * (d ** (N - i)) - K, 0)
        S[N, i] = S_ini * (u ** (i)) * (d ** (N - i))
    for j in range(N - 1, -1, -1):
        for i in range(0, j + 1):
            C[j, i] = np.exp(-r * dt) * (p * C[j + 1, i + 1] + (1 - p) * C[j + 1, i])
            S[j, i] = S_ini * (u ** (i)) * (d ** (j - i))
    return C[0, 0], C, S
```
Notice that since we are doing backward induction, the first value of the Call Option Payoff matrix (the last we calculate) is the price of the Call Option today.

Let's replicate with the values from the example in the slides to check it:
```
call_price, C, S = binomial_call_full(100, 90, 10, 0, 1.2, 0.8, 10)
print("Underlying Price Evolution:\n", S)
print("Call Option Payoff:\n", C)
print("Call Option Price at t=0: ", "{:.2f}".format(call_price))
```
Feel free to play around with these functions to get familiar with how they work.

#### 1.1.4. Conclusion

In this lesson, we have started to price options in the simple framework of the binomial model. In the next lesson, we will keep working with the binomial model on features like the put-call parity.

See you in the next lesson!






### 1.2 **OPTION PRICING AND PUT-CALL PARITY**

|  |  |
|:---|:---|
|**Reading Time** |  40 minutes |
|**Prior Knowledge** |Financial Derivatives basics, Binomial tree, Risk neutral probabilities  |
|**Keywords** |Risk neutral probabilities, Binomial model, No-arbitrage, Put-Call parity  |


---


*In this notebook, we will continue to develop the binomial model for option pricing in Python. Building on the work we did in Lesson 1, we will now focus on relevant features like the put-call parity. Make sure you understand this properly because it is going to lay the foundation for future work.*


As usual, let's start importing some of the libraries that we may need to use down the road:
```
import numpy as np
```
Our first task is going to be to extend the binomial model function used in Lesson 1 to also consider put options:

#### 1.2.1. Binomial Tree for Put Options


We will create another function, similar to what we did with the call option case, to price put options. The following snippet contains the code for the call option we used in Lesson 1:
```
def binomial_call_full(S_ini, K, T, r, u, d, N):
    dt = T / N  # Define time step
    p = (np.exp(r * dt) - d) / (u - d)  # Risk neutral probs
    C = np.zeros([N + 1, N + 1])  # Call prices
    S = np.zeros([N + 1, N + 1])  # Underlying price
    for i in range(0, N + 1):
        C[N, i] = max(S_ini * (u ** (i)) * (d ** (N - i)) - K, 0)
        S[N, i] = S_ini * (u ** (i)) * (d ** (N - i))
    for j in range(N - 1, -1, -1):
        for i in range(0, j + 1):
            C[j, i] = np.exp(-r * dt) * (p * C[j + 1, i + 1] + (1 - p) * C[j + 1, i])
            S[j, i] = S_ini * (u ** (i)) * (d ** (j - i))
    return C[0, 0], C, S
```
Before continuing, can you think of how to modify this accordingly to construct another function that prices put options?
```
def binomial_put_full(S_ini, K, T, r, u, d, N):
    dt = T / N  # Define time step
    p = (np.exp(r * dt) - d) / (u - d)  # Risk neutral probs
    P = np.zeros([N + 1, N + 1])  # Call prices
    S = np.zeros([N + 1, N + 1])  # Underlying price
    for i in range(0, N + 1):
        P[N, i] = max(K - (S_ini * (u ** (i)) * (d ** (N - i))), 0)
        S[N, i] = S_ini * (u ** (i)) * (d ** (N - i))
    for j in range(N - 1, -1, -1):
        for i in range(0, j + 1):
            P[j, i] = np.exp(-r * dt) * (p * P[j + 1, i + 1] + (1 - p) * P[j + 1, i])
            S[j, i] = S_ini * (u ** (i)) * (d ** (j - i))
    return P[0, 0], P, S
```
Let's verify this is correct with the numbers from the example in the slides and videos: 
```
put_price, P, S = binomial_put_full(36, 36, 50, 0.01, 1.1, 0.7, 50)
print("Underlying Price Evolution:\n", S)
print("Put Option Payoff:\n", P)
print("Price at t=0 for Put option with K=90 is $", "{:.2f}".format(put_price))
```
Next, we will verify whether put-call parity holds in this example at t=0.

#### 1.2.2. Put-Call Parity in the Binomial Tree

We know that the price of the call and put options with K=90 at t=0 is given by the previous functions:
```
put_price, P, S = binomial_put_full(100, 90, 10, 0, 1.2, 0.8, 10)
print("Price at t=0 for Put option with K=90 is $", "{:.2f}".format(put_price))
call_price, C, S = binomial_call_full(100, 90, 10, 0, 1.2, 0.8, 10)
print("Price at t=0 for Call option with K=90 is $", "{:.2f}".format(call_price))
```
We already know that in order to satisfy absence of arbitrage conditions, the relationship between the price of the put and the call options must be:

$C_0 + Ke^{-rT} = S_0 + P_0$

Let's check whether this is the case for t=0:

call_price + 90 * np.exp(-0 * 1) == S[0, 0] + put_price

We have verified that the put-call parity here holds perfectly at t=0. The question that arises now is does this behavior also hold at other nodes of the tree (other times)?

In order to check this, let's first increase the number of steps of the binomial tree to N=2:
```python
put_price, P, S = binomial_put_full(100, 90, 1, 0, 1.2, 0.8, 2)
print("Price at t=0 for Put option with K=90 is $", "{:.2f}".format(put_price))
call_price, C, S = binomial_call_full(100, 90, 1, 0, 1.2, 0.8, 2)
print("Price at t=0 for Call option with K=90 is $", "{:.2f}".format(call_price))
```
For completeness, let's start verifying Put-Call parity at t=0:
```
call_price + 90 * np.exp(-0 * 1) == S[0, 0] + put_price
```
Now, let's check the same thing for some other node of the two-step tree. Remember that this is the evolution of underlying prices and option payoffs:
```
print("Underlying Price Evolution:\n", S)
print("Call Option Payoff:\n", C)
print("Put Option Payoff:\n", P)
```
Let's check put-call parity for the node following path 'd' (underlying price S_d = 80), which we can index as [1,0] in the matrix S:
```
C[1, 0] + 90 * np.exp(-0 * 0.5) == S[1, 0] + P[1, 0]
```
Now, it is your turn to check whether this relationship holds for other nodes (you can also try trees with more steps) $→$ Does put-call parity hold?

#### 1.2.3. Conclusion 

In this lesson, we have worked throughout the binomial tree to verify the put-call parity on certain nodes. In the next lesson, we will work on the concept of delta-hedging.


### 1.3 **INTRODUCING DELTA**

|  |  |
|:---|:---|
|**Reading Time** |  45 minutes |
|**Prior Knowledge** | Binomial tree for stock price evolution, Pricing options under  a binomial tree, No-arbitrage argument  |
|**Keywords** |Delta of a security, Delta hedging, Putting all the  previous ideas together  |

*In this lesson, we are going to revisit and reinforce some previous concepts, like option pricing in a binomial tree, and then move on to some new ideas about how we can perfectly hedge away the underlying price risk through **delta hedging**.*

*To begin with, let's see the type of underlying stock price distribution that we are going to be using in the following graph. Remember that, for simplicity, we are going to be using a risk-free rate $r=0$, and that we will be working with (pricing) a call option with strike price $K=90$.*

![tree.png](data:image/png;base64,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f/nlF3VRRDo9BtZOGSG2gwSSS4Az18nlz6uTAAmQAAm4gABcFBcuXKjSj6NHjwZcFPPly+eC1rOJJEACiSTA4DqRtHktEiABEiABVxGAi+K4ceM080fx4sVV+lGnTh26KLpqFNlYEkgsAS5oTCxvXo0ESIAESMAFBOCiOHz4cJk3b57Akpwuii4YNDaRBBxCgMG1QwaCzSABEiABEkguAWT6WLlypRq+7N27V7p06SL79++Xiy66KLkN49VJgARcRYDBtauGi40lARIgARKINQG4KMLsZdiwYXLhhRfKww8/LI0bN6aLYqxBsz4S8AkBBtc+GWh2kwRIgARIICWBr776SkaMGKHuidWqVVOb8qpVq6Y8iJ9IgARIIEICTMUXITAeTgIkQAIk4G4C69atUx01XBNz5cqlLopz5swRBtbuHle2ngScQoAz104ZCbaDBEiABEggbgTgogjXxCFDhgi01ZB+wFUxT548cbsmKyYBEvAnAabi8+e4s9ckQAIk4AsCP/zwg7ooIp3eTTfdpKn0qlev7ou+s5MkQALJIUBZSHK486okQAIkQAJxJLB161Z56KGHpEyZMnLq1CnZvHmzLF++XBhYxxE6qyYBElACnLnmF4EESIAESMATBOCiOH/+fJV+/PTTT9KjRw9p37690EXRE8PLTpCAawgwuHbNULGhJEACJEAC6RGAi+LYsWPVRfGaa66R3r17ywMPPEAXxfRgcRsJkEDcCVAWEnfEvAAJkAAJkEA8CMBFsWPHjoKA+ssvv1QDGGQCoT15PGizThIggXAJMFtIuKR4HAmQAAmQQNIJINMHrMiHDh0q+/bto4ti0keEDSABEkhNgMF1aiL8TAIk4CsCf//9ty54u+CCC1wtI/jll1/k/PPPl2zZsoUcv7/++kt+++03dSMMebA5AFpmnHPOOeeEc3hcjoGL4qRJk9RFsUCBApr1o1GjRnRRjAttVkoCJJAVApSFZIUezyUBEnAlAQSKAwcOlCpVquhit4suukiDtBIlSugiODd16tixYyqNQMAJx8H0CmZ73333XWndurVcddVVmtsZx5ctW1aef/55OXToUHqnyd69ezW7Bm488ubNq8fDIjyRBX2ChrpIkSKyZcsWmTZtmnz44YfSvHlzBtaJHAheiwRIIGwCDK7DRsUDSYAEvEDgxIkTUrNmTXnxxRfl6quv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)

Let's start importing some of the libraries that we will need to use down the road:
```
import numpy as np
```
#### 1.3.1. Delta Hedging in the Binomial Tree


In the following section, you have the code for a general function to price a European call option using a binomial tree methodology. The function, as you can see, is able to compute the evolution of the underlying asset $S_t$, the price of the call option at each node of the tree, $C_t$, and also the $\Delta_t$ (number of shares in terms of exposure) in each node of the tree.
```
def call_option_delta(S_ini, K, T, r, u, d, N):
    dt = T / N  # Define time step
    p = (np.exp(r * dt) - d) / (u - d)  # risk neutral probs
    C = np.zeros([N + 1, N + 1])  # call prices
    S = np.zeros([N + 1, N + 1])  # underlying price
    Delta = np.zeros([N, N])  # delta
    for i in range(0, N + 1):
        C[N, i] = max(S_ini * (u ** (i)) * (d ** (N - i)) - K, 0)
        S[N, i] = S_ini * (u ** (i)) * (d ** (N - i))
    for j in range(N - 1, -1, -1):
        for i in range(0, j + 1):
            C[j, i] = np.exp(-r * dt) * (p * C[j + 1, i + 1] + (1 - p) * C[j + 1, i])
            S[j, i] = S_ini * (u ** (i)) * (d ** (j - i))
            Delta[j, i] = (C[j + 1, i + 1] - C[j + 1, i]) / (
                S[j + 1, i + 1] - S[j + 1, i]
            )
    return C[0, 0], C, S, Delta
```
In order to understand properly the general function defined above, we are going to use the toy example from the course slides. First of all, we will map the example in the course slides with the parameters in the function "call_option_delta".



*   N = 2 (Two periods/time steps). Thus, we will have three times: $t=0$, $t=1$, $t=2$
*   Delta will be defined in three nodes: one node at $t=0$, named $\Delta_0$, and two nodes (two potential outcomes) at $t=1$: $\Delta_1^u$ and $\Delta_1^d$.

If we run the "call_option_delta" function, we can print directly the underlying asset price, call price, and delta for all nodes as follows. As you can see, these match what you have in the slides:


```
price, call, S, delta = call_option_delta(100, 90, 15, 0, 1.2, 0.8, 15)
print("Underlying: \n", S)
print("Call Price: \n", call)
print("Delta: \n", delta)
```
According to the above results, we can conclude that, if we want to hedge the sale of this call option (remember, we are selling this as a bank), we will need to perform the following steps:

*   At $t=0$, we have to buy 0.675 shares (assuming that the underlying is a stock).
*   At $t=1$, we have to "hold" 0.1875 shares if we are "down" ($\Delta_1^d$=0.1875) or 1 share if we are "up" ($\Delta_1^u$=1). 

To give you a complete idea of how the hedging system would work in practice, we will focus on the path, $du$.  

Thus, at the first step, we follow the path "down". Than means that at $t=0$, we buy 0.675 shares at \\$100 USD price per share = \\$67.5 USD total cost. At $t=1$, we sell 0.4875 shares (0.675-0.1875 = 0.4875 shares) at \\$80 USD price to get \\$39 USD. Thus, we end up at $t=1$ with a cost of \\$28.5 USD, but we still have 0.1875 shares. 

Finally, if we end up following the path "${du}$" (first down and then up), the final price of the underlying is \\$96 USD and the payoff of our call is \\$6 USD. Thus, we have at maturity, +96*0.1875 - 28.5 = \\$-10.5 USD. The price of the call in this path ("${du}$"), as you can see in the above results, is equal to $c_2^{du}=6$ USD. This \\$6 USD is the payment that we need to fulfill with the buyer; thus, our total cost is -10.5 - 6 = \\$16.5 USD, which is the call price. 



#### 1.3.2. Generalization to Any N

It is easy, once the above example is properly understood, to generalize the binomial tree and the hedging strategy to any number of time steps. For instance, see the example below with N=4.
```
price, call, S, delta = call_option_delta(100, 90, 10, 0, 1.2, 0.8, 10)
print("Underlying: \n", S)
print("Call Price: \n", call)
print("Delta: \n", delta)
```
The price of the call is equal to \\$20.205 USD, which is quite different from the previous value of \\$16.5 USD. You will notice that if you try with a higher N, the call price will increase monotonically. See the code snippet below:

##### 1.3.2.1. Convergence

Next, let's check the power of the binomial pricing method. In the following code snippet, we calculate the price of the option for different N's. Execute the following code to see how the price of the option changes with N.
```
price_array = []
for N in [1, 10, 100, 200, 300, 400, 500, 600, 700, 800, 900, 1000, 1500, 2000, 2500]:
    price, call, S, delta = call_option_delta(100, 90, 1, 0, 1.2, 0.8, N)
    price_array.append(price)
    print("With N = {:3d}, the price is {:.2f}".format(N, price))
```
In the next snippet, you can see this from a more visual perspective:
```
import matplotlib.pyplot as plt

N = [1, 10, 100, 200, 300, 400, 500, 600, 700, 800, 900, 1000, 1500, 2000, 2500]
plt.plot(N, np.array(price_array))
plt.title("Convergency with steps")
plt.xlabel("Number of steps (N)")
plt.ylabel("Option Price")
plt.grid(True)
plt.show()
```
Of course, the maximum value of the call price must be the underlying price. The question is, **why are we getting this absurd behavior?**

#### 1.3.3. Conclusion

We have gone over the basic steps to price options in a binomial model and explore how the prices we obtain change when we use a different number of steps in the model. However, the results from these experiments yielded somewhat inconsistent, or absurd, results.

In the next lesson, we will see that we need to adjust "$u$" and "$d$" with the number of steps ($dt$) in order to match the underlying asset's volatility. Doing this, we will get rid of the previous problem.

See you in the next lesson!

**References**

- Hull, J. C. (2021). *Options futures and other derivatives*. 11th Edition. Pearson. Chapter 13.




### 1.4. **MATCHING VOLATILITY AND RISK-MEASURES**


|  |  |
|:---|:---|
|**Reading Time** |  45 minutes |
|**Prior Knowledge** | Risk-neutral probability, Volatility, Time-step  |
|**Keywords** | Model calibration, Matching volatility|


---

*In the final notebook for Module 1, we will put all the previous concepts together to perform a complete valuation of a call option adjusting the binomial tree inputs $u$ and $d$ for the volatility of the underlying asset.*

*This adjusting step is the foundation of **model calibration**, which will be one of the keystones of the course and of derivative pricing in general.*

Let's start importing some of the libraries that we will need to use down the road:

import numpy as np

#### 1.4.1. Adjusting $u$ and $d$ for Underlying Volatility


Let's start by adjusting the inputs $u$ and $d$ to match underlying volatility. As we have covered in the notes/videos for the lesson, we know that adjustment will lead to:

$u = e^{\sigma \sqrt{dt}}$ and $d=e^{-\sigma \sqrt{dt}}$

Now, assume that we know the underlying stock volatility for the next year (e.g., $\sigma =30\%$). (*For now, let's take this number as given*.)

We can modify our previous functions to incorporate the volatility adjustment to $u$ and $d$:
```
def call_option_delta(S_ini, K, T, r, sigma, N):
    dt = T / N  # Define time step
    u = np.exp(sigma * np.sqrt(dt))  # Define u
    d = np.exp(-sigma * np.sqrt(dt))  # Define d
    p = (np.exp(r * dt) - d) / (u - d)  # risk neutral probs
    C = np.zeros([N + 1, N + 1])  # call prices
    S = np.zeros([N + 1, N + 1])  # underlying price
    Delta = np.zeros([N, N])  # delta
    for i in range(0, N + 1):
        C[N, i] = max(S_ini * (u ** (i)) * (d ** (N - i)) - K, 0)
        S[N, i] = S_ini * (u ** (i)) * (d ** (N - i))
    for j in range(N - 1, -1, -1):
        for i in range(0, j + 1):
            C[j, i] = np.exp(-r * dt) * (p * C[j + 1, i + 1] + (1 - p) * C[j + 1, i])
            S[j, i] = S_ini * (u ** (i)) * (d ** (j - i))
            Delta[j, i] = (C[j + 1, i + 1] - C[j + 1, i]) / (
                S[j + 1, i + 1] - S[j + 1, i]
            )
    return C[0, 0], C, S, Delta
```
#### 1.4.2. Convergence

Let's see what the call option ($K=90$, $r=0\%$, $T=1$, $\sigma=0.3$) price is for different N's:
```
price_array = []
for N in [1, 10, 100, 200, 300, 400, 500, 600, 700, 800, 900, 1000, 1500, 2000, 2500]:
    call_price, C, S, delta = call_option_delta(100, 90, 1, 0.1, 0.2, N)
    price_array.append(call_price)
    print("With N = {:3d}, the price is {:.2f}".format(N, call_price))
```
```
import matplotlib.pyplot as plt

N = [1, 10, 100, 200, 300, 400, 500, 600, 700, 800, 900, 1000, 1500, 2000, 2500]
plt.plot(N, np.array(price_array))
plt.title("Convergency with steps")
plt.xlabel("Number of steps (N)")
plt.ylabel("Option Price")
plt.grid(True)
plt.show()

```
As we can see in the graph above, the price of the call option now clearly converges to a price of $c = 17.01$. 

#### 1.4.3. How Do We Obtain $\sigma$ ?

Obtaining the volatility of the underlying asset in order to calibrate the model is one of the most challenging tasks that we will face.

For now, we have taken this input as a given. However, in reality, we would need to estimate this somehow. Can you think of how to do it?

* Historical asset volatility (e.g., last year) ? → But this relies on the past = No good

* Implied asset volatility ? → implied by what? → Exchange-traded option prices

We will do a deep analysis of the latter point during the course. For now, just think about the following idea:

If we have an exchange-traded option (for which the **price is set by supply and demand**) and a **pricing equation** that depends on parameters (including $\sigma$), we can resolve this equation and **extract the volatility implied by that price.**

We will come back to this concept in the future. For now, you can explore this by looking at the Options Chain for Apple (AAPL) [in Yahoo! Finance.](https://finance.yahoo.com/quote/AAPL/options?p=AAPL)


#### 1.4.4. Conclusion

Throughout this lesson, we have worked on a simple model calibration, something that will become very relevant when dealing with more complex models. We will be constantly revisiting model calibration throughout the course, so make sure you grasp the concept fully. 

In the next module, we will revisit most of these ideas for the case of American options.

See you in Module 2!




## M2



### 2.1 **INTRO TO AMERICAN OPTIONS**


|  |  |
|:---|:---|
|**Reading Time** |  60 minutes |
|**Prior Knowledge** | Binomial model, Option pricing |
|**Keywords** | American options, Early-exercise, Volatility matching|


---

*In this lesson, we are going to introduce the American payoff and how to implement the pricing of an American option with Python. Let's start importing some of the libraries that we will need to use down the road:*
```
import numpy as np
```
#### 2.1.1. American Options Payoff

An American option is a style of options contract that allows holders to exercise their rights at any time before and on the expiration date. Thus, American-style options allow investors to capture profit as soon as the stock price moves favorably.

The value of this option, if it is left alive until maturity, is the same as its European counterpart. On the other hand, the value of the option if it is exercised is given by:

$$max(0, S_t-K)$$ 

in the call case and,

$$max(0, K-S_t)$$ 

in the put case.



Thus, the **first step** consists of computing the European option prices for each node in the tree. 

Second, for each node, we get the maximum value between the European option price and the payoff from early exercise.

For instance, if we follow the slide example:


![American_tree_notebook.png](data:image/png;base64,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)

The above figure shows the European option price for each node. In the **second step**, we decide whether to exercise the option in each node. Thus, in the next figure, we are going to keep the maximum value (in each node) between the European option price and the payoff from early exercise. See figure below:

![American_tree_notebook_2.png](data:image/png;base64,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)

The node that changes from the European option price to the American price is node {d}. **Why?** It is simple: We are comparing the European option price, $9.4636, with the payoff from early excercise, which is given by:

$$K-S = $52 - $40 = $12 > 9.4636$$

Just for completeness, in the other node in which we should make a decision, {u}, the payoff from early exercise is lower than the European option price:

$$K - S = $52 - $60 = - $8 < $1.4247$$
```
def american_option(S_ini, K, T, r, u, d, N, opttype):

    dt = T / N  # Define time step
    p = (np.exp(r * dt) - d) / (u - d)  # risk neutral probs
    C = np.zeros([N + 1, N + 1])  # call prices
    S = np.zeros([N + 1, N + 1])  # underlying price

    for i in range(0, N + 1):
        S[N, i] = S_ini * (u ** (i)) * (d ** (N - i))
        if opttype == "C":
            C[N, i] = max(S[N, i] - K, 0)
        else:
            C[N, i] = max(K - S[N, i], 0)

    for j in range(N - 1, -1, -1):
        for i in range(0, j + 1):
            C[j, i] = np.exp(-r * dt) * (
                p * C[j + 1, i + 1] + (1 - p) * C[j + 1, i]
            )  # Computing the European option prices
            S[j, i] = (
                S_ini * (u ** (i)) * (d ** (j - i))
            )  # Underlying evolution for each node
            if opttype == "C":
                C[j, i] = max(
                    C[j, i], S[j, i] - K
                )  # Decision between the European option price and the payoff from early-exercise
            else:
                C[j, i] = max(
                    C[j, i], K - S[j, i]
                )  # Decision between the European option price and the payoff from early-exercise

    return C[0, 0], C, S
```

#### 2.1.2. Numerical Interpretation

Thus, for an American call, the value of the American option at a node is given by:

$$C(S,K,t) = max(S-K, e^{-rt}\left[C(uS, t+dt)p^*+C(dS, t+dt)(1-p^*)\right]$$ 

where, 

$$e^{-rt}\left[C(uS, t+dt)p^*+C(dS,t+dt)(1-p^*)\right]$$ 

represent the expected discounted value of "leaving alive" the option for another period (European option price). In other words,\

$$ e^{-rt} E^{*}[C(t+dt)] = e^{-rt} \left[C(uS, t+dt)p^*+C(dS,t+dt)(1-p^*)\right]$$


Thus, in each node, we will make the decision of exercising the option only if the expected discounted value of the call in the next period is less than the value that we get if we decide to exercise the option.


Finally, let's try to reproduce our "toy-model" using the code. Remember the "toy-model" parameters (European Put Option):

$$u = 1.2, d = 0.8, T = 2 = N , dt = 1, r = 5\%, K=52, S_0 = 50$$
```
option_price, C, S = american_option(145, 100, 100, 0.1, 1.2, 0.8, 100, "P")
```
First, we check the underlying evolution...
```
S
```
Second, we check the option price in each node...
```
C
```
Thus, finally, the price of the American put is given by...
```
print(option_price)
```
#### 2.1.3. Matching Volatility in the American Option Function

Finally, in the next function, we compute the parameters "u" and "d" as a function of the underlying volatility (see Module 1, Lesson 4). 
```
def american_option_vol(S_ini, K, T, r, sigma, N, opttype):

    dt = T / N  # Define time step
    u = np.exp(sigma * np.sqrt(dt))  # Define u
    d = np.exp(-sigma * np.sqrt(dt))  # Define d
    p = (np.exp(r * dt) - d) / (u - d)  # risk neutral probs
    C = np.zeros([N + 1, N + 1])  # call prices
    S = np.zeros([N + 1, N + 1])  # underlying price

    for i in range(0, N + 1):
        S[N, i] = S_ini * (u ** (i)) * (d ** (N - i))
        if opttype == "C":
            C[N, i] = max(S[N, i] - K, 0)
        else:
            C[N, i] = max(K - S[N, i], 0)

    for j in range(N - 1, -1, -1):
        for i in range(0, j + 1):
            C[j, i] = np.exp(-r * dt) * (
                p * C[j + 1, i + 1] + (1 - p) * C[j + 1, i]
            )  # Computing the European option prices
            S[j, i] = (
                S_ini * (u ** (i)) * (d ** (j - i))
            )  # Underlying evolution for each node
            if opttype == "C":
                C[j, i] = max(
                    C[j, i], S[j, i] - K
                )  # Decision between the European option price and the payoff from early-exercise
            else:
                C[j, i] = max(
                    C[j, i], K - S[j, i]
                )  # Decision between the European option price and the payoff from early-exercise

    return C[0, 0], C, S
```
To conclude this example, let's try to get the price of an American option with the same parameters as the European call option of Module 1 (Lesson 4). That is: 

$$K=90, r=0\%, T=1, \sigma=0.3$$

```
price, C, S = american_option_vol(100, 90, 10, 0, 0.3, 10, "C")
print(price)
```
Finally, let's now see what call option ($K=90$, $r=0\%$, $T=1$, $\sigma=0.3$) price we obtain for different N's:
```
price_array = []
for N in [1, 10, 100, 200, 300, 400, 500, 600, 700, 800, 900, 1000, 1500, 2000, 2500]:
    call_price, C, S = american_option_vol(100, 90, 1, 0, 0.3, N, "C")
    price_array.append(call_price)
    print("With N = {:3d}, the price is {:.2f}".format(N, call_price))
```
```
import matplotlib.pyplot as plt

N = [1, 10, 100, 200, 300, 400, 500, 600, 700, 800, 900, 1000, 1500, 2000, 2500]
plt.plot(N, np.array(price_array))
plt.title("Convergency with steps")
plt.xlabel("Number of steps (N)")
plt.ylabel("American Option Price")
plt.grid(True)
plt.show()
```
#### 2.1.4. Conclusion

In this lesson, we have gone over the basics of American option pricing and the fundamental differences compared to European options. In the next lesson, we will revisit the concept of delta hedging in the context of American derivatives. 




### 2.2 **DYNAMIC DELTA HEDGING**



|  |  |
|:---|:---|
|**Reading Time** |  40 minutes |
|**Prior Knowledge** | Pricing in the Binomial model, Characteristics of American options, Delta hedging  |
|**Keywords** | Dynamic delta hedging, American options |


---

*In the previous lesson, we introduced American options, whose main feature is the embedded possibility of early exercise of the option prior to maturity. This is going to be important for pricing but also for hedging purposes. In the context of European options, we could delta-hedge our portfolio by simply looking at terminal prices. This is no longer an option for American derivatives, which require dynamic delta hedging for every step in the tree. In this lesson, we will take a closer look at how to perform dynamic hedging.*

As usual, let's start by importing the numpy library:
```
import numpy as np
```
#### 2.2.1. Delta Hedging in the Binomial Tree: American Options

In the following snippet, you have the code for a general function to price a European option using a binomial tree methodology. The function, as you can see, is able to compute the evolution of the underlying asset $S_t$, the price of the option at each node of the tree, $C_t$, and also the $\Delta_t$ (number of shares in terms of exposure) in each node of the tree.
```
def american_option(S_ini, K, T, r, u, d, N, opttype):

    dt = T / N  # Define time step
    p = (np.exp(r * dt) - d) / (u - d)  # risk neutral probs
    C = np.zeros([N + 1, N + 1])  # call prices
    S = np.zeros([N + 1, N + 1])  # underlying price
    Delta = np.zeros([N, N])  # delta

    for i in range(0, N + 1):
        S[N, i] = S_ini * (u ** (i)) * (d ** (N - i))
        if opttype == "C":
            C[N, i] = max(S[N, i] - K, 0)
        else:
            C[N, i] = max(K - S[N, i], 0)

    for j in range(N - 1, -1, -1):
        for i in range(0, j + 1):
            C[j, i] = np.exp(-r * dt) * (
                p * C[j + 1, i + 1] + (1 - p) * C[j + 1, i]
            )  # Computing the European option prices
            S[j, i] = (
                S_ini * (u ** (i)) * (d ** (j - i))
            )  # Underlying evolution for each node
            if opttype == "C":
                C[j, i] = max(
                    C[j, i], S[j, i] - K
                )  # Decision between the European option price and the payoff from early-exercise
            else:
                C[j, i] = max(
                    C[j, i], K - S[j, i]
                )  # Decision between the European option price and the payoff from early-exercise

            Delta[j, i] = (C[j + 1, i + 1] - C[j + 1, i]) / (
                S[j + 1, i + 1] - S[j + 1, i]
            )  # Computing the delta for each node

    return C[0, 0], C, S, Delta

price, C, S, delta = american_option(45, 100, 5, 0, 1.5, 1 / 1.5, 5, "C")
```
```
price
```
```
delta
```
Let's now compare this delta hedging with the one from the European option with the same characteristics. For that, we will reuse some of the code from Module 1:

```
def european_option(S_ini, K, T, r, u, d, N, opttype):

    dt = T / N  # Define time step
    p = (np.exp(r * dt) - d) / (u - d)  # risk neutral probs
    C = np.zeros([N + 1, N + 1])  # call prices
    S = np.zeros([N + 1, N + 1])  # underlying price
    Delta = np.zeros([N, N])  # delta

    for i in range(0, N + 1):
        S[N, i] = S_ini * (u ** (i)) * (d ** (N - i))
        if opttype == "C":
            C[N, i] = max(S[N, i] - K, 0)
        else:
            C[N, i] = max(K - S[N, i], 0)

    for j in range(N - 1, -1, -1):
        for i in range(0, j + 1):
            C[j, i] = np.exp(-r * dt) * (
                p * C[j + 1, i + 1] + (1 - p) * C[j + 1, i]
            )  # Computing the European option prices
            S[j, i] = (
                S_ini * (u ** (i)) * (d ** (j - i))
            )  # Underlying evolution for each node

            Delta[j, i] = (C[j + 1, i + 1] - C[j + 1, i]) / (
                S[j + 1, i + 1] - S[j + 1, i]
            )  # Computing the delta for each node

    return C[0, 0], C, S, Delta

price_euro, C_euro, S_euro, delta_euro = european_option(
    50, 52, 5, 0.05, 1.2, 0.8, 5, "C"
)
delta_euro
```
```
price_euro
```
#### **2.2.2. Conclusion**

In this lesson, we have seen 
the importance of dynamic delta hedging in the context of American derivatives. This is an important concept as well for other path-dependent options, as we will see in the next lesson.



### 2.3 missing in wqu site.


### **2.4. INTRO TO MONTE CARLO METHODS**


|  |  |
|:---|:---|
|**Reading Time** |  60 minutes |
|**Prior Knowledge** | Binomial model, Option pricing, European options, American options, Asian options |
|**Keywords** |Monte-Carlo methods, Path-dependent options |


---

*In Lesson 4 of Module 2, we will go through the basics of using Monte Carlo methods for derivative pricing. Ideally, you should look at this notebook while working with the corresponding video and slides, but you can also work on this on your own.*


#### **2.4.1. Monte Carlo Methods**

Please note that we are introducing Monte Carlo methods informally here. Monte Carlo comes in handy in a lot of derivative pricing problems in real life, and we will cover this method thoroughly throughout the course. We believe this simple introduction will help down the road regarding basic intuition. The mapping of what the actual analytical computation does versus the Monte Carlo estimation will be very easy to see in this simple setting. In the future, it can be more complex though, so we believe it is best to introduce it here.

Let's start importing the numpy library:
```
import numpy as np
```
Next, we are going to develop a function, `call_option_mc`, that will use Monte Carlo-like methods to study the power of this technique.

The basic intuition of Monte Carlo is that by simulating a fair amount of outcomes randomly from the same distribution as our underlying process, we can obtain a solution close to the actual (full) process. The process will go as follows:
- Select the distribution you are using for the underlying process: In our case, it is a binomial distribution for the stock price. 
- Simulate random realizations of such distribution: We use Python to choose a random number from a binomial distribution using np.random.binomial.
- Calculate option payoff for those simulated values and discount them so that you can confirm a price for the option under each simulated path.
- Get the mean of those prices: By relying on the law of large numbers, when the amount of randomly generated values is high enough, the average of all converges to the true value of the options. Of course, the more simulations, the merrier.

Let's get to it with the European call option example:

#### **2.4.2. European Option Payoff (Monte Carlo)**
```
def call_option_mc(S_ini, K, T, r, sigma, N, M):
    dt = T / N  # Define time step
    u = np.exp(sigma * np.sqrt(dt))  # Define u
    d = np.exp(-sigma * np.sqrt(dt))  # Define d
    p = (np.exp(r * dt) - d) / (u - d)  # risk neutral probs
    C = np.zeros([M])  # call prices
    S = np.zeros([M, N + 1])  # underlying price
    S[:, 0] = S_ini

    for j in range(0, M):
        random = np.random.binomial(
            1, p, N + 1
        )  # We sample random realizations for the paths of the tree under a binomial distribution
        for i in range(1, N + 1):
            if random[i] == 1:
                S[j, i] = S[j, i - 1] * u
            else:
                S[j, i] = S[j, i - 1] * d

        C[j] = np.exp(-r * T) * max(S[j, N] - K, 0)

    return S, C
```
Now that we have our function, let's check its performance by comparing it to the European call option we priced in Module 1. If you remember, these were the characteristics of the option:
- $S_0=100$
- $K=90$
- $T=1$
- $r = 0\%$
- $\sigma = 0.3$

If you remember, when we increase the number of paths in the binomial tree, $N$, the price of the option converged to $\$17.01$ for $N=2,500$.

So, let's see how our (quasi) Monte Carlo algorithm performs for $N=2,500$ using $15,000$ simulations (paths):
```
S, C = call_option_mc(
    100, 90, 1, 0, 0.3, 2500, 15000
)  # Prices 15000 different simulations
```
Now the variable $C$ contains the $15,000$ different prices from the different simulations performed. In order to get the final value for the call option proxied with Monte Carlo, we just average all these values:
```
print(np.mean(C))
```
As you can see, the value is pretty close to the one we got from the workout on the full binomial model of $\$17.01$.

But let's dig a little deeper into the convergence to this value. We will now check how we start approximating to this value as we increase the number of simulations:
```
M = np.arange(1000, 16000, 1000)  # Different number of simulations to be considered
call_price = []
```
*Warning: The following code will take several minutes to run!*
```
for i in range(len(M)):
    S, C = call_option_mc(100, 90, 1, 0, 0.3, 2500, M[i])
    call_price.append(np.mean(C))
```
```
import matplotlib.pyplot as plt

plt.plot(M, call_price)
plt.axhline(y=17.01, color="r", linestyle="-", label="Binomial model price")
plt.ylim([14, 23])
plt.title("MC Estimates for different # simulations")
plt.xlabel("Number of Simulations")
plt.ylabel("Call Option Price")
plt.grid(True)
plt.legend()
plt.show()
```
While the past exercise may seem in vain, given that we can simply use the binomial model to price the option, it gives us a pretty good idea of how the Monte Carlo method works.

Understanding Monte Carlo methods, thus, will help us provide efficient solutions/pricing in more problematic scenarios, as was the case with the Asian option. In this framework, calculating ALL the potential payoffs of the option for $N=2,500$ would mean we have to deal with $2^N = 2^{2500}$ paths. That is virtually impossible and inefficient. 

Hence, Monte Carlo will come in handy in these type of situations for path-dependent derivatives. Let's now build up a function, `asian_option_mc`, to price an Asian option with the same characteristics using this technique:

#### **2.4.3. Asian Option Payoff (Monte Carlo)**
```
def asian_option_mc(S_ini, K, T, r, sigma, N, M):
    dt = T / N  # Define time step
    u = np.exp(sigma * np.sqrt(dt))  # Define u
    d = np.exp(-sigma * np.sqrt(dt))  # Define d
    p = (np.exp(r * dt) - d) / (u - d)  # risk neutral probs
    Asian = np.zeros([M])  # Asian prices
    S = np.zeros([M, N + 1])  # underlying price
    S[:, 0] = S_ini

    for j in range(0, M):
        random = np.random.binomial(1, p, N + 1)
        Total = 0
        for i in range(1, N + 1):
            if random[i] == 1:
                S[j, i] = S[j, i - 1] * u
                Total = Total + S[j, i]
            else:
                S[j, i] = S[j, i - 1] * d
                Total = Total + S[j, i]

        Asian[j] = np.exp(-r * T) * max(Total / (N + 1) - K, 0)

    return S, Asian
```
As before, let's check the prices for the different paths:
```
S, Asian = asian_option_mc(100, 90, 1, 0, 0.3, 2500, 10000)
```
And average them to get a final estimate:
```
print(np.mean(Asian))
```
Let's also study the convergence of the methods in a similar fashion as before:
```
M = np.arange(1000, 16000, 1000)
asian_price = []
```
*Warning: The following code will take several minutes to run!*
```
for i in range(len(M)):
    S, Asian = asian_option_mc(100, 90, 1, 0, 0.3, 2500, M[i])
    asian_price.append(np.mean(Asian))
```
```
import matplotlib.pyplot as plt

plt.plot(M, asian_price)
plt.ylim([10, 15])
plt.title("MC Estimates for different # simulations")
plt.xlabel("Number of Simulations")
plt.ylabel("Asian Call Option Price")
plt.grid(True)
plt.show()
```
#### **2.4.4. Conclusion**

All in all, you have seen firsthand how mastering Monte Carlo methods can be a fundamental ally when it comes to pricing complex derivatives for which it is too costly (or impossible) to actually compute all the potential outcomes of the underlying process.

Please note once again that this lesson introduces Monte Carlo from an informal perspective and only with the goal of simplifying your understanding of it. We will dig deeper into this in future modules.

