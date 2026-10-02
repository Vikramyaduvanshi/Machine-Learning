Chapter 4 — Multiple Features, Parameters & Vectorization
1. Ab tak hum kya kar rahe the?

Ab tak hamara model tha:

y
^
	​

=wx+b
	​


Isme sirf one feature x tha.

Example:

House price predict karni hai using only house size.

House Size (x)
      ↓
    wx + b
      ↓
   Prediction ŷ

Lekin real-world problem me prediction usually sirf ek feature se nahi hoti.

2. Multiple Features kya hote hain?

Suppose house price predict karni hai.

Sirf size important nahi hai.

Aur bhi factors ho sakte hain:

House size
Number of bedrooms
Number of floors
Age of house

So ab:

x
1
	​

=house size
x
2
	​

=bedrooms
x
3
	​

=floors

Hamare paas total:

n=3
	​


features hain.

3. Feature kya hota hai?

Feature = input ka ek individual property/attribute.

Example:

Feature	Meaning
x
1
	​

	House size
x
2
	​

	Bedrooms
x
3
	​

	Floors

Inhe hum mathematically:

x
1
	​

,x
2
	​

,x
3
	​

	​


likhte hain.

4. Single Feature se Multiple Features

Single feature:

y
^
	​

=wx+b

Multiple features me:

y
^
	​

=w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+w
3
	​

x
3
	​

+b
	​


Agar n features hain:

y
^
	​

=w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+⋯+w
n
	​

x
n
	​

+b
	​


Compact form:

y
^
	​

=
j=1
∑
n
	​

w
j
	​

x
j
	​

+b
	​

5. w₁, w₂, w₃ kya hain?

Har feature ka apna weight hota hai.

Suppose:

y
^
	​

=w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+w
3
	​

x
3
	​

+b

Then:

w
1
	​

 → feature x
1
	​

 ka weight
w
2
	​

 → feature x
2
	​

 ka weight
w
3
	​

 → feature x
3
	​

 ka weight

Weight basically batata hai:

Prediction me particular feature ka kitna contribution hai.

6. Real Example

Suppose:

x
1
	​

=10
x
2
	​

=2
x
3
	​

=1

Aur model ke parameters:

w
1
	​

=5
w
2
	​

=10
w
3
	​

=20
b=100

Then:

y
^
	​

=w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+w
3
	​

x
3
	​

+b

Substitute:

y
^
	​

=5(10)+10(2)+20(1)+100
=50+20+20+100
y
^
	​

=190
	​

7. Har Feature ka Contribution

Upar wale example me:

Feature 1
w
1
	​

x
1
	​

=5(10)=50

Contribution:

50
Feature 2
w
2
	​

x
2
	​

=10(2)=20

Contribution:

20
Feature 3
w
3
	​

x
3
	​

=20(1)=20

Contribution:

20

Bias:

b=100

Total:

50+20+20+100=190
8. w ab ek number nahi hai

Single feature me:

w=5

Ek number tha.

Multiple features me:

w
1
	​

,w
2
	​

,w
3
	​

,…,w
n
	​


hote hain.

Isliye hum in sab weights ko ek saath store kar sakte hain.

9. Weight Vector

Weights:

w
1
	​

,w
2
	​

,w
3
	​


ko ek vector me likh sakte hain:

w
=[w
1
	​

,w
2
	​

,w
3
	​

]
	​


Example:

w
=[1.0,2.5,−3.3]
	​


Important:

Ab w ek single number nahi, weights ka collection/vector hai.

10. Feature Vector

Similarly features:

x
1
	​

,x
2
	​

,x
3
	​


ko vector me store kar sakte hain:

x
=[x
1
	​

,x
2
	​

,x
3
	​

]
	​


Example:

x
=[10,20,30]
	​


So:

Weights:

w = [1.0, 2.5, -3.3]

Features:

x = [10, 20, 30]
11. Important Difference: Feature vs Parameter

Ye distinction bahut important hai.

Features

Features data se aate hain:

x
1
	​

,x
2
	​

,x
3
	​


Example:

House size
Bedrooms
Floors
Parameters

Model learn karta hai:

w
1
	​

,w
2
	​

,w
3
	​

,b

Training ke during Gradient Descent in values ko optimize karta hai.

So:

x=data/input
	​

w,b=parameters learned by model
	​

12. b kya hai?

Bias:

b
	​


Ab bhi sirf ek number hai.

Example:

b=4

Image me bhi:

b = 4

So:

w
=[w
1
	​

,w
2
	​

,w
3
	​

]

but:

b=4
13. Image wala Exact Example

Image me:

w = np.array([1.0, 2.5, -3.3])

b = 4

x = np.array([10, 20, 30])

So:

w
1
	​

=1.0
w
2
	​

=2.5
w
3
	​

=−3.3

and:

x
1
	​

=10
x
2
	​

=20
x
3
	​

=30

and:

b=4
14. Prediction Manually Calculate Karo

Formula:

f
w,b
	​

(x)=w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+w
3
	​

x
3
	​

+b

Substitute:

f
w,b
	​

(x)=(1.0)(10)+(2.5)(20)+(−3.3)(30)+4

Calculate:

1(10)=10
2.5(20)=50
−3.3(30)=−99

Therefore:

f
w,b
	​

(x)=10+50−99+4
f
w,b
	​

(x)=−35
	​


Ye model ki prediction hai.

15. Σ Symbol kya karta hai?

Image me formula hai:

f
w
,b
	​

(
x
)=
j=1
∑
n
	​

w
j
	​

x
j
	​

+b
	​


Ye basically shortcut notation hai.

Σ ka meaning:

Sab terms ko add karo.

For n=3:

j=1
∑
3
	​

w
j
	​

x
j
	​


means:

w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+w
3
	​

x
3
	​


So:

j=1
∑
3
	​

w
j
	​

x
j
	​

=w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+w
3
	​

x
3
	​

	​

16. j = 1 to n ka Meaning

Formula:

j=1
∑
n
	​

w
j
	​

x
j
	​


Yahan j ek counter/index hai.

If:

n=3

then:

j=1,2,3

So:

j = 1 → w₁x₁
j = 2 → w₂x₂
j = 3 → w₃x₃

Then:

w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+w
3
	​

x
3
	​

17. Mathematics aur Python Indexing ka Difference

Image me ek important point hai.

Mathematics

Usually counting:

1,2,3,…,n

So:

w
1
	​

,w
2
	​

,w
3
	​

Python

Index starts from:

0

So:

w[0]
w[1]
w[2]

Correspondence:

Math	Python
w
1
	​

	w[0]
w
2
	​

	w[1]
w
3
	​

	w[2]
x
1
	​

	x[0]
x
2
	​

	x[1]
x
3
	​

	x[2]
18. Python Code — Without Vectorization

Image me:

f = w[0] * x[0] + \
    w[1] * x[1] + \
    w[2] * x[2] + b

Ye exactly mathematical formula:

w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+w
3
	​

x
3
	​

+b

ko implement kar raha hai.

19. General Python Version

Agar features n hain to manually likhna possible nahi.

Suppose:

n=100,000

Kya hum:

w[0] * x[0] +
w[1] * x[1] +
w[2] * x[2] +
...

100,000 times likhenge?

Obviously nahi.

Isliye loop use karte hain.

20. Without Vectorization — Loop
f = 0

for j in range(n):
    f = f + w[j] * x[j]

f = f + b

Ye exactly:

j=1
∑
n
	​

w
j
	​

x
j
	​

+b

implement karta hai.

21. Python range(n)

Agar:

n = 3

Then:

range(3)

produces:

0
1
2

So loop:

for j in range(n):

means:

j = 0
j = 1
j = 2
22. Loop ko Step-by-Step Run Karo

Given:

w = [1.0, 2.5, -3.3]

x = [10, 20, 30]

b = 4

Initially:

f = 0
Iteration 1
j = 0

Calculate:

w[0]x[0]
=1.0(10)
=10

So:

f = 0 + 10
f=10
Iteration 2
j = 1

Calculate:

w[1]x[1]
=2.5(20)
=50

So:

f=10+50
f=60
Iteration 3
j = 2

Calculate:

w[2]x[2]
=(−3.3)(30)
=−99

So:

f=60−99
f=−39

Finally:

f = f + b
f=−39+4
f=−35
	​

23. Problem with This Approach

Loop mathematically correct hai.

But large datasets me:

for j in range(n):

slow ho sakta hai.

Suppose:

n=100,000

or:

n=1,000,000

To millions of individual Python operations ho sakti hain.

Yahan Vectorization useful hoti hai.

24. Vectorization kya hai?

Vectorization ka simple meaning:

Multiple operations ko efficiently ek saath perform karna instead of manually Python loops.

Instead of:

w[0] * x[0]
w[1] * x[1]
w[2] * x[2]
...

hum vectors par operation kar sakte hain.

25. Dot Product

Vectorization ka core concept hai:

w
⋅
x
	​


Isko dot product kehte hain.

For:

w
=[w
1
	​

,w
2
	​

,w
3
	​

]

and:

x
=[x
1
	​

,x
2
	​

,x
3
	​

]

Dot product:

w
⋅
x
=w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+w
3
	​

x
3
	​

	​


Exactly wahi calculation jo loop kar raha tha.

26. Vectorized Formula

Without vectorization:

f
w
,b
	​

(
x
)=w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+w
3
	​

x
3
	​

+b

Summation form:

f
w
,b
	​

(
x
)=
j=1
∑
n
	​

w
j
	​

x
j
	​

+b

Vectorized form:

f
w
,b
	​

(
x
)=
w
⋅
x
+b
	​

27. Dot Product Example

Given:

w
=[1,2,3]
x
=[10,20,30]

Dot product:

w
⋅
x
=(1)(10)+(2)(20)+(3)(30)
=10+40+90
=140

If:

b=5

Then:

f=140+5
f=145
	​

28. NumPy me Vectorization

Image me:

f = np.dot(w, x) + b

Ye:

w
⋅
x
+b
	​


calculate karta hai.

Example:

import numpy as np

w = np.array([1.0, 2.5, -3.3])
x = np.array([10, 20, 30])
b = 4

f = np.dot(w, x) + b

print(f)

Output:

-35.0
29. np.dot(w, x) andar kya kar raha hai?

Given:

w = [1.0, 2.5, -3.3]
x = [10, 20, 30]

Conceptually:

[1.0,  2.5, -3.3]
   ×     ×     ×
[10,   20,    30]
   ↓     ↓     ↓
  10    50    -99
       ↓
   10 + 50 - 99
       ↓
      -39

Then:

+ b
−39+4=−35
30. Vectorization vs Loop
Without Vectorization
f = 0

for j in range(n):
    f = f + w[j] * x[j]

f = f + b
With Vectorization
f = np.dot(w, x) + b

Mathematical result:

Same
	​


But vectorized code generally much more efficient hota hai, especially large numerical workloads me.

31. Why NumPy is Fast?

Python loop:

for j in range(n):

har iteration ko Python level par handle karta hai.

NumPy numerical operations optimized low-level implementations use kar sakti hain and hardware efficiently utilize kar sakti hain.

Isliye:

np.dot(w, x)

large arrays ke liye generally much faster approach hoti hai than manually looping in Python.

32. Vector ka Visualization

Suppose:

w
=[w
1
	​

,w
2
	​

,w
3
	​

]

and:

x
=[x
1
	​

,x
2
	​

,x
3
	​

]

Think:

w = [ w₁   w₂   w₃ ]
       ×    ×    ×
x = [ x₁   x₂   x₃ ]

       ↓    ↓    ↓

     w₁x₁ w₂x₂ w₃x₃

       \    |    /
        \   |   /
         \  |  /
          ADD

       + b

       ↓

       ŷ
33. Parameters vs Features — Again Important

Model:

f
w
,b
	​

(
x
)=
w
⋅
x
+b
	​

Features
x

Input data.

Parameters
w
,b

Model parameters.

During training:

w
,b are learned
	​


Input:

x
 comes from data
	​

34. Training ke Context me

Suppose:

x
=[10,20,30]

Initial parameters:

w
=[1,2,3]
b=4

Prediction:

y
^
	​

=
w
⋅
x
+b

Then:

y
^
	​

=145

Suppose actual value:

y=160

Then model ki prediction:

y
^
	​

=145

Actual:

y=160

Difference/error:

y
^
	​

−y
=145−160
=−15

Then Cost Function is used to measure how wrong prediction hai.

Uske baad gradients:

∂w
1
	​

∂J
	​

,
∂w
2
	​

∂J
	​

,
∂w
3
	​

∂J
	​

,
∂b
∂J
	​


calculate honge.

Then Gradient Descent parameters update karega.

35. One Feature se Multiple Features tak Full Journey
Stage 1 — One feature
y
^
	​

=wx+b
	​

Stage 2 — Multiple features
y
^
	​

=w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+⋯+w
n
	​

x
n
	​

+b
	​

Stage 3 — Summation
y
^
	​

=
j=1
∑
n
	​

w
j
	​

x
j
	​

+b
	​

Stage 4 — Vectorization
y
^
	​

=
w
⋅
x
+b
	​


Ye four forms same model calculation ko represent karte hain.

36. Important Connection with PyTorch

Aage jab hum PyTorch use karenge, vectors/tensors ka concept extremely important hoga.

For example:

import torch

w = torch.tensor([1.0, 2.5, -3.3])
x = torch.tensor([10.0, 20.0, 30.0])

b = 4.0

y_hat = torch.dot(w, x) + b

Concept same:

y
^
	​

=
w
⋅
x
+b
	​


Bas NumPy ke badle PyTorch tensors use kar rahe hain.

37. NumPy Array kya hai?

Image me:

w = np.array([1.0, 2.5, -3.3])

np.array() NumPy ka array create karta hai.

So:

w

represents:

[1.0,2.5,−3.3]

Similarly:

x = np.array([10,20,30])

represents:

[10,20,30]
38. Shape ka Concept

Vectorization me shape bahut important hoga.

For:

w = np.array([1,2,3])

shape:

(3,)
	​


Means 3 elements.

Similarly:

x = np.array([10,20,30])

shape:

(3,)
	​


Dot product possible hai because dimensions match:

(3)⋅(3)
39. Dot Product ke liye Dimensions Match

Suppose:

w=[w
1
	​

,w
2
	​

,w
3
	​

]

3 values.

And:

x=[x
1
	​

,x
2
	​

,x
3
	​

]

also 3 values.

Then:

w⋅x

possible hai.

But:

w = [1,2,3]
x = [10,20]

Dimensions match nahi karte.

Because:

3

=2

Therefore dot product valid nahi hoga.

40. n kya represent karta hai?

Image me:

n=3

n = number of features.

If:

x=[x
1
	​

,x
2
	​

,x
3
	​

]

then:

n=3

If:

x=[x
1
	​

,x
2
	​

,…,x
100
	​

]

then:

n=100
41. Feature Indexing

Mathematics:

x
1
	​

,x
2
	​

,x
3
	​


Python:

x[0]
x[1]
x[2]

So remember:

Math starts from 1
	​


while:

Python indexing starts from 0
	​


Ye ML coding me frequently important hoga.

42. Most Important Formula

Is chapter ka main formula:

f
w
,b
	​

(
x
)=
w
⋅
x
+b
	​


Expanded:

f
w
,b
	​

(
x
)=w
1
	​

x
1
	​

+w
2
	​

x
2
	​

+⋯+w
n
	​

x
n
	​

+b
	​


Summation:

f
w
,b
	​

(
x
)=
j=1
∑
n
	​

w
j
	​

x
j
	​

+b
	​


Python:

f = np.dot(w, x) + b

Ye chaaron exactly same calculation hain.

43. Chapter ka Mental Model
                MULTIPLE FEATURES
                       │
                       ▼
              x₁, x₂, x₃, ... xₙ
                       │
                       │
              Corresponding weights
                       │
                       ▼
              w₁, w₂, w₃, ... wₙ
                       │
                       ▼
              Multiply matching pairs
                       │
                       ▼
          w₁x₁ + w₂x₂ + ... + wₙxₙ
                       │
                       ▼
                      + b
                       │
                       ▼
                     ŷ
                  Prediction

Vectorized:

        w vector             x vector
           │                    │
           └────────┬───────────┘
                    ▼
                DOT PRODUCT
                    │
                    ▼
                   + b
                    │
                    ▼
                    ŷ
44. Chapter 4 — Final Revision
Feature
x
j
	​

=input feature
	​

Weight
w
j
	​

=feature ka learned parameter
	​

Bias
b=single learned parameter
	​

Number of features
n=number of features
	​

Multiple-feature model
y
^
	​

=
j=1
∑
n
	​

w
j
	​

x
j
	​

+b
	​

Vector form
y
^
	​

=
w
⋅
x
+b
	​

NumPy implementation
f = np.dot(w, x) + b
45. Previous Chapters se Connection

Ab tak hamari journey:

CHAPTER 1
Functions
   ↓
y = wx + b
   ↓
Graph
   ↓
Slope


CHAPTER 2
Cost Function
   ↓
J(w,b)
   ↓
Minimum


CHAPTER 3
Derivative
   ↓
dJ/dw
   ↓
Gradient
   ↓
Gradient Descent


CHAPTER 4
Multiple Features
   ↓
w₁x₁ + w₂x₂ + ... + wₙxₙ + b
   ↓
Σ wⱼxⱼ + b
   ↓
w · x + b
   ↓
Vectorization
   ↓
NumPy / PyTorch
🔥 Final Concept

Single feature me:

y
^
	​

=wx+b
	​


Multiple features me w bhi vector ban gaya aur x bhi vector:

y
^
	​

=
w
⋅
x
+b
	​


Aur:

w
⋅
x
=
j=1
∑
n
	​

w
j
	​

x
j
	​

	​


Yani Vectorization koi naya ML formula nahi hai — same mathematical calculation ko efficient way me perform karne ka method hai.

Aage isi foundation par hum multiple features ka Cost Function → derivatives ∂J/∂w
j
	​

 → vectorized Gradient Descent → NumPy implementation → PyTorch tensors/autograd build karenge.