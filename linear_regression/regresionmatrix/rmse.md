# RMSE (Root Mean Squared Error) - Notes

## 1. RMSE kya hai?

RMSE, MSE ka **square root** hai.

$$\text{RMSE} = \sqrt{\text{MSE}} = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2}$$

---
`````````````````````````````````````````````````````````````````````````````````
## 2. Kyu chahiye?

- MSE ki **unit squared** ho jati hai (lakh²), jiska intuitive matlab nahi hota.
- Square root lene se unit wapas **original (lakh)** ho jati hai.
- Isse bol sakte hain: "model ki typical galti lagbhag X lakh hai."

---

## 3. Example

Errors: +5, -5, 0

$$\text{MSE} = \frac{50}{3} \approx 16.67 \text{ lakh}^2$$

$$\text{RMSE} = \sqrt{16.67} \approx 4.08 \text{ lakh}$$

---

## 4. RMSE vs MAE (Case A aur B)

| | Errors | MAE | MSE | RMSE |
|---|---|---|---|---|
| Case A | 3, 3, 3, 3 | 3 | 9 | 3 |
| Case B | 0, 0, 0, 12 | 3 | 36 | 6 |

- Case A: sab errors barabar, toh **RMSE = MAE**
- Case B: ek bada error, toh **RMSE > MAE**

---

## 5. Important properties

1. **RMSE ≥ MAE hamesha.** Barabar tabhi jab saare errors ki magnitude same ho. RMSE aur MAE ke beech jitna bada gap, utna zyada errors ka spread (outliers ka sign).
2. **Outliers ke prati sensitive.** Andar squaring hoti hai, toh bade errors ko zyada weight milta hai.
3. **Minimizer wahi jo MSE ka.** Square root increasing function hai, toh jahan MSE minimum, wahin RMSE minimum.
4. **Gradient thoda alag:**

$$\frac{\partial\, \text{RMSE}}{\partial w} = \frac{1}{2\,\text{RMSE}} \cdot \frac{\partial\, \text{MSE}}{\partial w}$$

   RMSE zero ke paas jaye toh division by zero ka risk, isliye training mein direct use kam hota hai.

---

## 6. Comparison table

| Point | MSE | RMSE | MAE |
|---|---|---|---|
| Formula | (1/n) Σ e² | √MSE | (1/n) Σ \|e\| |
| Unit | Squared | Original | Original |
| Outliers | Sensitive | Sensitive | Robust |
| Training mein use | Haan (common) | Kam | Kabhi kabhi |
| Interpret karna | Mushkil | Aasan | Aasan |

---

## 7. Thumb rule

- **Train karo MSE se** (smooth aur simple gradient)
- **Report karo RMSE ya MAE se** (original unit)
- Outliers ignore karne hain -> **MAE**
- Bade errors bardasht nahi -> **RMSE / MSE**

---

## Quick revision

- RMSE = √(average of squared errors)
- Unit original hoti hai, interpret karna aasan
- RMSE ≥ MAE, gap bada matlab outliers
- MSE aur RMSE ka minimum same point par aata hai

---

## Practice (Desmos)

- Slider `a` banao aur plot karo: `y = sqrt(((5-a)^2 + (-5-a)^2 + (0-a)^2)/3)`
- Minimum kahan aata hai dekho, yeh MSE wale minimum jaisa hi point hoga