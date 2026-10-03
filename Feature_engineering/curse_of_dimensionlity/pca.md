# PCA (Principal Component Analysis) — Final Notes

## 1. PCA kya karta hai?

**PCA dimensionality reduction technique hai.**

Agar dataset mein bahut saare correlated features hain, PCA unhe kuch naye **Principal Components** mein convert karta hai, jisme maximum possible variance retain ki jaati hai.

Example:

```text
Original features:
X1, X2, X3, X4, X5

        ↓ PCA

Principal Components:
PC1, PC2
```

Goal:

> **Kam dimensions mein maximum information/variance retain karna.**

---

# 2. PCA ka Complete Flow

```text
Original Data
      ↓
Mean Centering
      ↓
Covariance Matrix
      ↓
Eigenvalues + Eigenvectors
      ↓
Eigenvalues ko sort karo
      ↓
Principal Components select karo
      ↓
Data ko selected components par project karo
      ↓
Reduced Dataset
```

---

# 3. Mean

Mean kisi feature ka average hota hai.

Formula:

$$
\mu=\frac{\sum x_i}{n}
$$

Example:

```text
X = [2, 4, 6, 8, 10]
```

$$
\mu_X=\frac{2+4+6+8+10}{5}=6
$$

Do features ke case mein:

```text
X = CGPA
Y = Placement Marks

mean(X) = 6
mean(Y) = 60
```

---

# 4. Mean Centering

PCA mein data ko mean ke around center kiya jata hai.

Formula:

$$
X_c=X-\mu_X
$$

$$
Y_c=Y-\mu_Y
$$

Example:

```text
Original:

X = [2, 4, 6, 8, 10]
Y = [20, 40, 60, 80, 100]

Mean:

X = 6
Y = 60
```

Mean subtract karne ke baad:

```text
X_centered = [-4, -2, 0, 2, 4]

Y_centered = [-40, -20, 0, 20, 40]
```

Centered data ka mean:

```text
X mean = 0
Y mean = 0
```

### Mean centering kyun?

Data ka center origin `(0,0)` par aa jata hai.

```text
Before:

center = (6, 60)

After:

center = (0, 0)
```

Important:

> Mean centering data ki direction ya spread ko change nahi karta; data ko coordinate system mein shift karta hai.

---

# 5. Variance

Variance batata hai ki values mean ke around kitni spread hain.

Population variance:

$$
\sigma^2=
\frac{\sum(x_i-\mu)^2}{n}
$$

Example:

```text
X = [2, 4, 6]
mean = 4
```

Differences:

```text
[-2, 0, 2]
```

Squared differences:

```text
[4, 0, 4]
```

Variance:

$$
\frac{4+0+4}{3}
=
\frac83
\approx2.67
$$

Important:

```text
High variance → data zyada spread
Low variance  → data kam spread
```

PCA mein variance important hai kyunki PCA **maximum variance wali directions** find karta hai.

---

# 6. Standard Deviation

Standard deviation variance ka square root hai.

$$
\sigma=\sqrt{\sigma^2}
$$

Agar:

$$
Variance=2.67
$$

toh:

$$
Std\approx1.63
$$

Difference:

```text
Variance → squared units
Std      → original units
```

---

# 7. Covariance

Covariance batata hai ki do features **saath mein kis direction mein change karte hain**.

Formula:

$$
Cov(X,Y)=
\frac{\sum (x_i-\mu_X)(y_i-\mu_Y)}{n}
$$

Interpretation:

```text
Positive covariance
→ X badhta hai toh Y generally badhta hai

Negative covariance
→ X badhta hai toh Y generally ghatta hai

Near zero
→ weak linear relationship
```

Important:

> Zero covariance ka matlab ye nahi ki nonlinear relationship bilkul nahi hai.

---

# 8. Covariance Matrix

Agar do features hain:

```text
X
Y
```

toh covariance matrix:

$$
C=
\begin{bmatrix}
Var(X)&Cov(X,Y)\\
Cov(Y,X)&Var(Y)
\end{bmatrix}
$$

Example:

$$
C=
\begin{bmatrix}
8&80\\
80&800
\end{bmatrix}
$$

Ismein:

```text
Diagonal:
8   → Var(X)
800 → Var(Y)

Off-diagonal:
80 → Cov(X,Y)
```

Covariance matrix symmetric hoti hai:

$$
Cov(X,Y)=Cov(Y,X)
$$

---

# 9. PCA ke liye Covariance Matrix important kyun?

PCA ko ye pata karna hai:

> Data kis direction mein maximum variance rakhta hai?

Covariance matrix features ke:

* variance
* pairwise relationship

ko capture karti hai.

Phir isi matrix se **eigenvalues aur eigenvectors** nikale jaate hain.

---

# 10. Eigenvector

Eigenvector ek **special direction** hota hai.

Basic equation:

$$
Av=\lambda v
$$

Yahan:

```text
A = matrix
v = eigenvector
λ = eigenvalue
```

Normal vector matrix se multiply hone par direction change kar sakta hai.

Eigenvector ke case mein:

```text
direction same
magnitude scale
```

Example:

$$
A=
\begin{bmatrix}
2&0\\
0&3
\end{bmatrix}
$$

Vector:

$$
v=
\begin{bmatrix}
1\\0
\end{bmatrix}
$$

Then:

$$
Av=
\begin{bmatrix}
2\\0
\end{bmatrix}
=
2
\begin{bmatrix}
1\\0
\end{bmatrix}
$$

Therefore:

```text
Eigenvector = [1, 0]
Eigenvalue  = 2
```

---

# 11. Eigenvalue

Eigenvalue batati hai ki corresponding eigenvector ki direction mein **kitna variance** hai.

PCA mein:

```text
Eigenvector → direction
Eigenvalue  → us direction ka variance
```

Isliye:

> **Largest eigenvalue → maximum variance wali direction**

Aur us direction ka eigenvector:

> **PC1 (Principal Component 1)**

Second largest eigenvalue:

> **PC2**

and so on.

---

# 12. Eigenvalue kaise calculate karte hain?

Formula:

$$
\det(C-\lambda I)=0
$$

Hamari covariance matrix:

$$
C=
\begin{bmatrix}
8&80\\
80&800
\end{bmatrix}
$$

Identity matrix:

$$
I=
\begin{bmatrix}
1&0\\
0&1
\end{bmatrix}
$$

Therefore:

$$
C-\lambda I=
\begin{bmatrix}
8-\lambda&80\\
80&800-\lambda
\end{bmatrix}
$$

Determinant:

$$
(8-\lambda)(800-\lambda)-80(80)=0
$$

Simplify:

$$
\lambda^2-808\lambda=0
$$

Factor:

$$
\lambda(\lambda-808)=0
$$

Therefore:

$$
\boxed{\lambda_1=808}
$$

$$
\boxed{\lambda_2=0}
$$

---

# 13. Eigenvector kaise calculate karte hain?

Formula:

$$
(C-\lambda I)v=0
$$

Largest eigenvalue:

$$
\lambda=808
$$

Substitute:

$$
\begin{bmatrix}
-800&80\\
80&-8
\end{bmatrix}
\begin{bmatrix}
x\\y
\end{bmatrix}
=
\begin{bmatrix}
0\\0
\end{bmatrix}
$$

First equation:

$$
-800x+80y=0
$$

Therefore:

$$
80y=800x
$$

$$
\boxed{y=10x}
$$

Agar:

$$
x=1
$$

then:

$$
y=10
$$

Therefore eigenvector:

$$
\boxed{
v_1=
\begin{bmatrix}
1\\10
\end{bmatrix}
}
$$

---

# 14. `y = 10x` ka relation

Equation:

$$
y=10x
$$

bilkul normal straight-line equation:

$$
y=mx+c
$$

jaisi hai.

Yahan:

```text
m = 10
c = 0
```

Eigenvector:

$$
[1,10]
$$

isi direction mein point karta hai.

```text
(1,10)
(2,20)
(3,30)
```

ye same straight-line direction mein hain.

Important:

> `[1,10]` aur `[2,20]` different length ke hain, lekin same direction represent karte hain.

---

# 15. Eigenvector Normalization

Eigenvector:

$$
v=
\begin{bmatrix}
1\\10
\end{bmatrix}
$$

Length:

$$
\|v\|=\sqrt{1^2+10^2}
$$

$$
=\sqrt{101}
$$

Normalize:

$$
\hat v=\frac{v}{\|v\|}
$$

Therefore:

$$
\hat v=
\begin{bmatrix}
1/\sqrt{101}\\
10/\sqrt{101}
\end{bmatrix}
$$

Approximately:

$$
\boxed{
\hat v=
\begin{bmatrix}
0.0995\\
0.9950
\end{bmatrix}
}
$$

Normalization ka purpose:

> Eigenvector ki length ko `1` banana.

Important:

> Normalization direction change nahi karta.

---

# 16. Mean Centering vs Eigenvector Normalization

Dono ko confuse nahi karna.

### Mean Centering

```text
Data ka center → (0,0)
```

Formula:

$$
X_c=X-\mu
$$

### Eigenvector Normalization

```text
Eigenvector ki length → 1
```

Formula:

$$
\hat v=\frac{v}{\|v\|}
$$

Therefore:

```text
Mean Centering
→ data ko center karta hai

Normalization
→ eigenvector ko unit length karta hai
```

Dono ka purpose completely different hai.

---

# 17. Projection

Ab humein data ko principal component mein convert karna hai.

Formula:

$$
\boxed{Z=X_c\hat v}
$$

Yahan:

```text
Xc = centered data
v  = normalized eigenvector
Z  = principal component score
```

Example:

Centered point:

$$
X_c=(2,20)
$$

Normalized eigenvector:

$$
\hat v=(0.0995,0.9950)
$$

Projection:

$$
PC1=
2(0.0995)+20(0.9950)
$$

$$
\boxed{PC1\approx20.099}
$$

Yaani original point:

```text
(8,80)
```

center hone ke baad:

```text
(2,20)
```

aur PC1 par project hone ke baad:

```text
20.099
```

Ab 2-dimensional point ko 1-dimensional component se represent kar sakte hain.

---

# 18. Normalized vs Unnormalized Eigenvector

Agar eigenvector:

$$
[1,10]
$$

use karein:

$$
PC1=2(1)+20(10)=202
$$

Normalized vector:

$$
[0.0995,0.995]
$$

use karein:

$$
PC1\approx20.099
$$

Direction same rahegi.

Difference:

```text
Direction → same
Scale     → different
```

Standard PCA eigenvectors ko unit length mein use karta hai.

---

# 19. Principal Components

Eigenvalues ko descending order mein sort karte hain.

Example:

```text
λ1 = 808
λ2 = 0
```

Therefore:

```text
PC1 → eigenvector corresponding to 808
PC2 → eigenvector corresponding to 0
```

Rule:

$$
\boxed{\text{Largest eigenvalue → PC1}}
$$

$$
\boxed{\text{Second largest → PC2}}
$$

and so on.

---

# 20. Explained Variance Ratio

Ye batata hai ki **total variance ka kitna percentage kisi principal component ne capture kiya.**

Formula:

$$
EVR_i=
\frac{\lambda_i}
{\sum_j\lambda_j}
$$

Example:

$$
\lambda_1=808
$$

$$
\lambda_2=0
$$

Total:

$$
808+0=808
$$

PC1:

$$
EVR_1=
\frac{808}{808}=1
$$

$$
\boxed{100\%}
$$

PC2:

$$
EVR_2=
\frac{0}{808}=0
$$

$$
\boxed{0\%}
$$

Is example mein PC1 alone 100% variance retain karta hai.

Reason:

```text
Y = 10X
```

Features perfectly linearly related hain.

---

# 21. Dimensionality Reduction

Suppose:

```text
Original:
X1, X2, X3, X4, X5
```

PCA ke baad:

```text
PC1, PC2
```

Agar PC1 + PC2 total variance ka sufficiently large percentage retain karte hain, toh baaki components ko discard kiya ja sakta hai.

Example:

```text
Original dimensions = 5
Reduced dimensions  = 2
```

Isliye PCA dimensionality reduction technique hai.

---

# 22. PCA ka Under-the-Hood Summary

```text
1. Original Data
       ↓
2. Mean calculate
       ↓
3. Mean subtract
       ↓
4. Centered Data
       ↓
5. Covariance Matrix
       ↓
6. Eigenvalues + Eigenvectors
       ↓
7. Eigenvalues sort
       ↓
8. Largest eigenvalues select
       ↓
9. Corresponding eigenvectors = Principal Components
       ↓
10. Data ko components par project
       ↓
11. Reduced Dataset
```

## Sabse important 4 cheezein

```text
Covariance Matrix
        ↓
Eigenvalues
        ↓
Eigenvectors
        ↓
Projection
```

Aur inka meaning:

| Concept                  | Meaning                                       |
| ------------------------ | --------------------------------------------- |
| Mean Centering           | Data ka center `(0,0)` par lana               |
| Covariance Matrix        | Features ka variance + relationship           |
| Eigenvector              | Important direction                           |
| Eigenvalue               | Us direction mein variance                    |
| PC1                      | Largest eigenvalue ka eigenvector             |
| Normalization            | Eigenvector ki length 1 karna                 |
| Projection               | Data ko principal direction par convert karna |
| Explained Variance Ratio | Kitna variance retain hua                     |

## One-line intuition

> **PCA data ko aisi new directions mein rotate karta hai jahan pehli direction maximum variance capture kare, doosri direction remaining maximum variance capture kare, aur phir low-variance directions ko discard karke dimensions reduce karta hai.**
