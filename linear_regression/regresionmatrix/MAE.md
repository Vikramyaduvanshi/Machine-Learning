Isko directly .md file mein paste kar sakte ho.

# MAE — Mean Absolute Error

## 1. MAE kya hota hai?

**MAE = Mean Absolute Error**

MAE ek **regression evaluation metric** hai jo batata hai ki model ki predictions actual values se average mein kitni door hain.

Simple meaning:

> **Model average mein kitna galat predict kar raha hai?**

---

# 2. Basic Regression Model

Linear Regression mein:

$$
\hat{y} = wx + b
$$

Yahan:

- $x$ = input feature
- $w$ = weight / slope
- $b$ = bias / intercept
- $\hat{y}$ = predicted value
- $y$ = actual value

Prediction error:

$$
e = y - \hat{y}
$$

Therefore:

$$
e = y - (wx+b)
$$

---

# 3. MAE Formula

MAE ka complete formula:

$$
\boxed{
MAE =
\frac{1}{n}
\sum_{i=1}^{n}
|y_i-\hat{y}_i|
}
$$

Yahan:

- $y_i$ = actual value
- $\hat{y}_i$ = predicted value
- $|y_i-\hat{y}_i|$ = absolute error
- $n$ = total observations

---

# 4. MAE mein Absolute kyu?

Agar actual aur prediction ka difference directly lein:

$$
Error = y-\hat{y}
$$

To error positive ya negative ho sakta hai.

Example:

### Case 1

$$
Actual = 100
$$

$$
Prediction = 80
$$

Error:

$$
100-80=20
$$

### Case 2

$$
Actual = 100
$$

$$
Prediction = 120
$$

Error:

$$
100-120=-20
$$

Dono predictions actual value se **20 units door** hain.

Lekin ek error `+20` hai aur doosra `-20`.

Agar directly average karenge to errors cancel ho sakte hain.

Isliye absolute value:

$$
|20|=20
$$

$$
|-20|=20
$$

MAE positive distance ko consider karta hai.

---

# 5. Numerical Example

Maan lo:

| Actual | Prediction |
|---:|---:|
| 100 | 90 |
| 200 | 220 |
| 300 | 270 |

## Step 1 — Errors

$$
100-90=10
$$

$$
200-220=-20
$$

$$
300-270=30
$$

Errors:

$$
[10,-20,30]
$$

---

## Step 2 — Absolute Errors

$$
|10|=10
$$

$$
|-20|=20
$$

$$
|30|=30
$$

Therefore:

$$
[10,20,30]
$$

---

## Step 3 — Mean

$$
MAE=
\frac{10+20+30}{3}
$$

$$
MAE=
\frac{60}{3}
$$

$$
\boxed{MAE=20}
$$

### Interpretation

Model ki prediction average mein actual value se:

$$
\boxed{20\ units}
$$

door hai.

Agar target house price ₹ lakh mein tha, to:

> Average prediction error = ₹20 lakh.

---

# 6. MAE ka Graphical Meaning

Har prediction ke liye:

$$
Error = Actual-Predicted
$$

MAE:

$$
|Actual-Predicted|
$$

Graphically ye actual value aur predicted value ke beech ki **vertical distance** ko measure karta hai.

```text
Actual
  ●
  |
  |  ← Absolute Error
  |
  ●
Prediction

Har point ki distance nikalo:

$$ |y_i-\hat{y}_i| $$

Phir sab distances ka average:

$$ MAE= \frac{\text{sum of all absolute distances}}{n} $$
7. MAE ka Main Goal

MAE sirf calculate karne ke liye nahi hai.

Machine Learning mein hum chahte hain:

$$ \boxed{MAE \rightarrow minimum} $$

Matlab:

Aise model parameters $w$ aur $b$ find karo jisse MAE minimum ho.

Since:

$$ \hat{y}=wx+b $$

MAE:

$$ MAE= \frac{1}{n} \sum |y_i-(wx_i+b)| $$

Goal:

$$ \boxed{ \min_{w,b} \frac{1}{n} \sum |y_i-(wx_i+b)| } $$
8. Optimization ka Basic Idea

Model ke parameters:

$$ w,b $$

hote hain.

Initially model ke parameters perfect nahi hote.

Example:

Initial:
w = 1
b = 0

        ↓

Prediction

        ↓

MAE calculate

        ↓

Parameters adjust

        ↓

Prediction again

        ↓

MAE again

        ↓

Repeat

Goal:

$$ MAE \downarrow $$
9. Derivative kyu use hota hai?

Optimization mein hume pata karna hota hai:

Parameter ko kis direction mein change karna hai taaki error decrease ho?

Derivative batata hai:

Function ko thoda change karne par output kis direction mein aur kitni rate se change hoga.

For example:

$$ E(b)=b^2 $$

Derivative:

$$ \frac{dE}{db}=2b $$

Agar:

$$ b=5 $$

then:

$$ \frac{dE}{db}=10 $$

Positive derivative ka matlab error graph increasing direction mein hai.

Agar:

$$ b=-5 $$

then:

$$ \frac{dE}{db}=-10 $$

Negative derivative ka matlab opposite direction mein move karna useful hoga.

At:

$$ b=0 $$ $$ \frac{dE}{db}=0 $$

Yahan minimum milta hai.

10. MAE mein Problem — Absolute Value

MAE:

$$ MAE= \frac{1}{n} \sum |y_i-\hat{y}_i| $$

Single error ko:

$$ e=y-\hat{y} $$

maan lo.

Then:

$$ MAE \propto |e| $$

Absolute function:

$$ |e| $$

ka graph:

       /
      /
     /
----●----
   /
  /

e = 0 par sharp corner hai.

Is point par normal derivative defined nahi hota.

11. MAE ka Derivative / Subgradient

For:

$$ L(e)=|e| $$

Derivative:

$$ \frac{d|e|}{de} = \begin{cases} +1 & e>0\\ -1 & e<0 \end{cases} $$

At:

$$ e=0 $$

normal derivative undefined hota hai.

Is situation mein subgradient use kiya ja sakta hai.

Simple intuition:

Error positive
      ↓
gradient +1

Error negative
      ↓
gradient -1
12. Linear Regression ke liye MAE

Model:

$$ \hat{y}_i=wx_i+b $$

Residual:

$$ e_i=y_i-(wx_i+b) $$

MAE:

$$ MAE= \frac{1}{n} \sum |y_i-(wx_i+b)| $$

Hume $w$ aur $b$ ko optimize karna hai.

13. MAE ka Gradient with respect to b

Residual:

$$ e_i=y_i-(wx_i+b) $$

Derivative of residual with respect to $b$:

$$ \frac{\partial e_i}{\partial b}=-1 $$

Absolute error ka subgradient:

$$ sign(e_i) $$

Therefore:

$$ \boxed{ \frac{\partial MAE}{\partial b} = -\frac{1}{n} \sum sign(e_i) } $$

where:

$$ sign(e_i)= \begin{cases} +1 & e_i>0\\ -1 & e_i<0 \end{cases} $$
14. MAE ka Gradient with respect to w

Residual:

$$ e_i=y_i-(wx_i+b) $$

Derivative:

$$ \frac{\partial e_i}{\partial w}=-x_i $$

Therefore:

$$ \boxed{ \frac{\partial MAE}{\partial w} = -\frac{1}{n} \sum sign(e_i)x_i } $$

Ye gradient batata hai ki $w$ ko kis direction mein change karna hai.

15. Gradient Descent se MAE Optimize karna

Gradient Descent ka basic rule:

$$ \boxed{ Parameter_{new} = Parameter_{old} - LearningRate \times Gradient } $$

For $w$:

$$ \boxed{ w_{new} = w- \alpha \frac{\partial MAE}{\partial w} } $$

For $b$:

$$ \boxed{ b_{new} = b- \alpha \frac{\partial MAE}{\partial b} } $$

Yahan:

$\alpha$ = learning rate
gradient = direction of increase
minus sign = opposite direction mein move karo
16. Simple Gradient Descent Flow
Initial w, b
     ↓
Prediction
     ↓
Calculate Error
     ↓
Calculate MAE
     ↓
Calculate Gradient / Subgradient
     ↓
Update w and b
     ↓
Prediction again
     ↓
Calculate MAE again
     ↓
Repeat
     ↓
MAE decreases

Eventually:

$$ MAE \rightarrow minimum $$
17. Numerical Example of MAE Optimization

Suppose:

Actual       Prediction

100             90
200            220
300            280

Residuals:

$$ e=[10,-20,20] $$

Signs:

$$ sign(e)=[+1,-1,+1] $$

MAE:

$$ MAE= \frac{10+20+20}{3} $$ $$ \boxed{MAE=16.67} $$

For $b$:

$$ \frac{\partial MAE}{\partial b} = -\frac{1}{3}(1-1+1) $$ $$ = -\frac{1}{3} $$

So:

$$ \boxed{ \frac{\partial MAE}{\partial b} =-0.333 } $$

Suppose:

$$ b=10 $$

and:

$$ \alpha=0.1 $$

Then:

$$ b_{new} = 10-(0.1)(-0.333) $$ $$ b_{new} = 10+0.0333 $$

So:

$$ \boxed{b_{new}\approx10.033} $$

Gradient ne bataya ki $b$ ko increase karna chahiye.

18. MAE vs MSE
MAE
$$ MAE= \frac{1}{n} \sum |y_i-\hat{y}_i| $$

Error ko absolute karta hai.

MSE
$$ MSE= \frac{1}{n} \sum(y_i-\hat{y}_i)^2 $$

Error ko square karta hai.

19. Large Errors par Difference

Suppose:

$$ Error=10 $$

MAE contribution:

$$ |10|=10 $$

MSE contribution:

$$ 10^2=100 $$

Now:

$$ Error=100 $$

MAE contribution:

$$ |100|=100 $$

MSE contribution:

$$ 100^2=10000 $$

So MSE large errors ko bahut strongly punish karta hai.

MAE:

Error = 10   → 10
Error = 100  → 100


MSE:

Error = 10   → 100
Error = 100  → 10000
20. MAE vs MSE — Gradient Difference
MAE
$$ |e| $$

Gradient/subgradient approximately:

$$ sign(e) $$

Magnitude mostly constant:

small error → 1
large error → 1
MSE
$$ e^2 $$

Derivative:

$$ 2e $$

Therefore:

small error → small gradient
large error → large gradient

So:

MSE large errors ko much stronger correction deta hai.

21. MAE Outliers ke liye useful kyu?

Suppose normal errors:

[5, 7, 10, 6]

Aur ek outlier:

100

MAE:

$$ |100|=100 $$

MSE:

$$ 100^2=10000 $$

MSE outlier ko extremely strongly punish karega.

MAE comparatively less sensitive hai.

Therefore:

MAE is more robust to outliers than MSE.

22. Important Property: MAE → Median

Ek interesting mathematical property:

Suppose model sirf ek constant value predict karta hai:

$$ \hat{y}=b $$

MAE:

$$ MAE= \frac{1}{n} \sum|y_i-b| $$

MAE ko minimize karne wala optimal $b$ generally median hota hai.

Example:

$$ y=[10,20,30,40,100] $$

Median:

$$ \boxed{30} $$

Therefore MAE minimize karne ke liye:

$$ \boxed{b=30} $$
23. MAE vs MSE — Mean vs Median

Constant prediction case:

MSE → Mean

MAE → Median

Example:

$$ y=[10,20,30,40,100] $$

Mean:

$$ \frac{10+20+30+40+100}{5}=40 $$

Median:

$$ 30 $$

Therefore:

MSE → prediction = 40
MAE → prediction = 30

Outlier 100 mean ko strongly pull karta hai.

Median comparatively stable rehta hai.

24. MAE ka Unit

MAE ki unit target variable ke same hoti hai.

Example:

House price:

Actual / Prediction → ₹ lakh

Then:

$$ MAE=10 $$

means:

Average prediction error = ₹10 lakh.

This makes MAE easy to interpret.

25. MAE Kab Use Kare?

MAE useful hai jab:

prediction error directly interpret karna ho
outliers ka effect relatively kam rakhna ho
average absolute deviation important ho
target ki original units mein error chahiye

Examples:

House price prediction
Sales prediction
Demand forecasting
Temperature prediction
Revenue prediction
26. MAE ki Limitation

MAE ke kuch limitations:

1. Large errors ko MSE jitna punish nahi karta

Because:

$$ MAE \propto |e| $$

while:

$$ MSE \propto e^2 $$
2. Zero par differentiable nahi
$$ |e| $$

at:

$$ e=0 $$

normal derivative undefined hai.

Isliye optimization mein subgradient ya other optimization techniques use ki ja sakti hain.

3. Scale dependent hai

Suppose:

Model A:
MAE = 10

Model B:
MAE = 5

B better lagta hai.

Lekin agar dono different target scales par trained hain, direct comparison meaningful nahi ho sakta.

27. MAE vs RMSE vs R²

Ye teen different cheezein measure karte hain.

MAE

Average absolute error:

$$ MAE= \frac{1}{n} \sum|y-\hat y| $$
RMSE

Squared errors ka root:

$$ RMSE= \sqrt{ \frac{1}{n} \sum(y-\hat y)^2 } $$
R²

Model kitni variance explain kar raha hai:

$$ R^2= 1- \frac{ \sum(y-\hat y)^2 }{ \sum(y-\bar y)^2 } $$
28. Important Difference
MAE
 ↓
Average error magnitude

MSE
 ↓
Squared error / large errors

RMSE
 ↓
Error magnitude in original units

R²
 ↓
Model data ki variance ko kitna explain karta hai
29. MAE Complete Under-the-Hood Flow
Input X
   ↓
Model
ŷ = wx + b
   ↓
Prediction
   ↓
Residual
e = y - ŷ
   ↓
Absolute Error
|e|
   ↓
Mean
MAE
   ↓
Optimization
   ↓
Gradient / Subgradient
   ↓
Update w, b
   ↓
Prediction again
   ↓
MAE decreases
30. One-Line Intuition

MAE actual aur predicted values ke beech absolute distance ka average hai.

Mathematically:

$$ \boxed{ MAE= \frac{1}{n} \sum_{i=1}^{n}|y_i-\hat{y}_i| } $$

Aur optimization ka goal:

$$ \boxed{MAE\rightarrow minimum} $$

For linear regression:

$$ \boxed{ \min_{w,b} \frac{1}{n} \sum_{i=1}^{n} |y_i-(wx_i+b)| } $$
31. Final Cheat Sheet
Concept	Formula / Meaning
Prediction	$\hat y=wx+b$
Error / Residual	$e=y-\hat y$
Absolute Error	$
MAE	$\frac{1}{n}\sum
Goal	$MAE\rightarrow minimum$
MAE gradient	Based on $sign(e)$
Positive error	$sign(e)=+1$
Negative error	$sign(e)=-1$
Zero error	Normal derivative undefined
Optimization	Gradient/Subgradient Descent
MAE outlier sensitivity	Lower than MSE
MAE constant optimum	Median
MSE constant optimum	Mean
MAE unit	Same as target
MSE	Large errors strongly punished
RMSE	Same target unit, large errors emphasized
32. Most Important Things to Remember
MAE
 ↓
Absolute Error ka Average
 ↓
Positive/Negative errors cancel nahi hote
 ↓
Goal = MAE minimize karna
 ↓
w aur b optimize hote hain
 ↓
Derivative/Subgradient direction batata hai
 ↓
Gradient Descent parameters update karta hai
 ↓
MAE decrease hota hai
Core Formula
$$ \boxed{ MAE= \frac{1}{n} \sum_{i=1}^{n}|y_i-\hat y_i| } $$
Linear Regression ke saath
$$ \boxed{ MAE= \frac{1}{n} \sum_{i=1}^{n} |y_i-(wx_i+b)| } $$
Optimization
$$ \boxed{ \min_{w,b} MAE } $$
Parameter Update
$$ \boxed{ \theta_{new} = \theta_{old} - \alpha \times gradient } $$

where $\theta$ can be $w$ or $b$.


Available next action: :contentReference[oaicite:0]{index=0}