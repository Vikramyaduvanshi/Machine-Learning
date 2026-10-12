# MSE (Mean Squared Error) - Notes

## 1. MSE kya hai?

**Error (residual):** actual aur predicted value ka difference.

$$e = y - \hat{y}$$

**MSE:** saare squared errors ka average.

$$\text{MSE} = \frac{1}{n}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2$$

Jitna chhota MSE, utna accha model.

---

## 2. Error ko square kyu karte hain?

**Problem:** errors ko seedha add karein toh positive aur negative cancel ho jaate hain.

| Sample | Actual y | Predicted ŷ | Error e |
|---|---|---|---|
| 1 | 50 | 45 | +5 |
| 2 | 30 | 35 | -5 |
| 3 | 40 | 40 | 0 |

Sum of errors = 5 + (-5) + 0 = **0** (model galat hai, phir bhi zero aaya).

**Solution:** sign hatane ke 2 tareeke
- Absolute value |e| -> MAE
- Square e^2 -> MSE

**Square ke fayde:**
1. Sign khatam, cancellation nahi hoti
2. Bade errors ko zyada punish karta hai (error 2 guna -> penalty 4 guna)
3. Smooth aur differentiable hai (derivative `2e`)
4. Convex hai, ek hi global minimum

**Example:**

$$\text{MSE} = \frac{25 + 25 + 0}{3} \approx 16.67$$

**Mean kyu, sum kyu nahi?**
- Sum dataset size par depend karta hai
- Mean se alag-alag size ke datasets compare ho sakte hain

---

## 3. MSE vs MAE

$$\text{MAE} = \frac{1}{n}\sum_{i=1}^{n}|y_i - \hat{y}_i|$$

Upar wale example par: MAE = 10/3 ≈ **3.33**, MSE ≈ **16.67**

### Bade errors ke saath behaviour

| | Errors | MAE | MSE |
|---|---|---|---|
| Case A | 3, 3, 3, 3 | 3 | 9 |
| Case B | 0, 0, 0, 12 | 3 | 36 |

- MAE dono mein same, MSE Case B mein 4 guna.
- **MSE bade errors ko zyada punish karta hai, MAE sabko barabar.**

### Comparison table

| Point | MSE | MAE |
|---|---|---|
| Formula | (1/n) Σ e² | (1/n) Σ \|e\| |
| Bade errors | Bahut zyada penalty | Barabar penalty |
| Graph | Smooth parabola | V shape (sharp corner) |
| Gradient | `2e` (smooth) | ±1 (e=0 par undefined) |
| Unit | Squared (lakh²) | Original unit (lakh) |
| Outliers | Sensitive | Robust |

**Gradient ka farak:**
- MSE: error bada -> bada step, error chhota -> chhota step, smoothly settle hota hai
- MAE: gradient hamesha same size ka, minimum ke paas bhi oscillate kar sakta hai

---

## 4. Graph of e²

$$f(e) = e^2$$

| e | -4 | -3 | -2 | -1 | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|---|---|---|---|
| e² | 16 | 9 | 4 | 1 | 0 | 1 | 4 | 9 | 16 |

### 5 important properties

1. **Minimum sirf e = 0 par** (perfect prediction = zero penalty)
2. **Symmetric** (over aur under prediction barabar punish)
3. **Hamesha ≥ 0** (MSE negative nahi ho sakta)
4. **Side steep hoti jaati hai** (slope `2e`: e=1 -> 2, e=5 -> 10, e=10 -> 20)
5. **Convex** (second derivative = 2 > 0, ek hi global minimum)

### ML se connection

Model: ŷ = w·x, data point x = 2, y = 6

$$\text{Error}(w) = (6 - 2w)^2$$

| w | 0 | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|---|
| Error² | 36 | 16 | 4 | **0** | 4 | 16 |

- Yeh bhi parabola hai, bottom w = 3 par (best weight)
- **Gradient Descent = bowl mein kisi bhi point se shuru karke slope ke saath neeche bottom ki taraf jaana**

---

## Quick revision

- MSE = average of squared errors
- Square karne se sign cancel nahi hota, bade errors ko zyada penalty milti hai
- e² ka graph smooth, symmetric, convex bowl hai
- Derivative `2e` hai, isliye Gradient Descent ke liye ideal
- MAE outliers ke liye robust, MSE sensitive

---

## Practice (Desmos)

- `y = x^2` aur `y = abs(x)` ek saath plot karke compare karo
- `y = (6 - 2w)^2` plot karo, bottom w = 3 par check karo
- `y = (6 - 2w)^2 + (4 - w)^2` plot karo (do data points ka MSE)