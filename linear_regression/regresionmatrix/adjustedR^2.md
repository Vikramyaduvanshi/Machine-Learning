# Adjusted R² - Notes

## 1. Problem: R² ko "dhoka" kaise milta hai?

- Ghar ki price ke liye features: area, rooms. Ab ek **random feature** add karo (jaise "ghar ke bahar kitne kabutar baithe the", pure noise).
- Training mein MSE **kabhi badhta nahi**, kam ya barabar hi rehta hai.

$$SS_{res}\ \text{kam ya barabar} \Rightarrow R^2\ \text{kam nahi hota}$$

- R² dekh kar lagta hai model behtar hua, jabki asal mein sirf **overfitting** hui.

---

## 2. Idea: har extra feature par penalty

Naya feature tabhi accha hai jab woh **itna improvement de ki penalty bhi cover ho jaye**.

$$R^2_{adj} = 1 - (1 - R^2)\cdot\frac{n-1}{n-p-1}$$

- $n$ = samples ki sankhya
- $p$ = features ki sankhya (intercept chhodkar)

---

## 3. Formula under the hood

$$R^2 = 1 - \frac{SS_{res}/n}{SS_{tot}/n}$$

Adjusted R² mein dono ko **unbiased variance estimate** (degrees of freedom se divide) se replace karte hain:

$$R^2_{adj} = 1 - \frac{SS_{res}/(n-p-1)}{SS_{tot}/(n-1)}$$

- Upar: model ki variance, $p+1$ parameters ($p$ weights + 1 intercept) fit hue, isliye $n-p-1$ se divide
- Neeche: baseline ki variance, sirf mean fit hua, isliye $n-1$ se divide

Simplify karne par wahi formula milta hai:

$$R^2_{adj} = 1 - (1-R^2)\cdot\frac{n-1}{n-p-1}$$

**Key point:** $p$ badhne par $n-p-1$ chhota hota hai, toh $SS_{res}/(n-p-1)$ **bada** hota hai. Yahi penalty hai.

---

## 4. Numerical example

$n = 20$ samples, ek feature wale model ka $R^2 = 0.80$.

**Case 1:** $p = 1$

$$R^2_{adj} = 1 - 0.20 \cdot \frac{19}{18} = 0.789$$

**Case 2:** bekaar feature add kiya, $p = 2$, $R^2 = 0.801$

$$R^2_{adj} = 1 - 0.199 \cdot \frac{19}{17} = 0.778$$

R² badha (0.800 -> 0.801) lekin Adjusted R² gir gaya (0.789 -> 0.778). Feature kaam ka nahi.

**Case 3:** kaam ka feature add kiya, $p = 2$, $R^2 = 0.90$

$$R^2_{adj} = 1 - 0.10 \cdot \frac{19}{17} = 0.888$$

Adjusted R² badha (0.789 -> 0.888), feature genuinely helpful.

| Case | p | R² | R²_adj |
|---|---|---|---|
| Original | 1 | 0.800 | 0.789 |
| Bekaar feature | 2 | 0.801 | 0.778 ↓ |
| Kaam ka feature | 2 | 0.900 | 0.888 ↑ |

---

## 5. Important properties

1. **R²_adj ≤ R² hamesha** (jab p ≥ 1), kyunki (n-1)/(n-p-1) ≥ 1.
2. **Negative ho sakta hai**, jab model kamzor ho aur p bada ho.
3. **n bahut bada, p chhota** hone par penalty ≈ 1, toh R²_adj ≈ R². Penalty tab matter karti hai jab **p, n ke comparison mein bada** ho.
4. Formula tabhi valid hai jab **n > p + 1**. Agar p ≥ n - 1 ho toh denominator zero ya negative (model data memorize kar leta hai).

---

## 6. Limitations

- Sirf ek **rough penalty**, overfitting ka perfect detector nahi.
- Non-linear models (neural networks, trees) mein "p" define karna mushkil, isliye wahan aam taur par nahi use hota.
- Model selection ke liye **cross-validation** aur **test set** zyada reliable. AIC/BIC bhi isi tarah ke penalised criteria hain.

---

## 7. R² vs Adjusted R²

| Point | R² | R²_adj |
|---|---|---|
| Naya feature add karne par | Kabhi kam nahi hota | Gir bhi sakta hai |
| Penalty | Nahi | Haan (p ke hisaab se) |
| Alag p wale models compare karna | Misleading | Better |
| Range | -∞ se 1 | -∞ se 1 |

---

## Python check

```python
def adjusted_r2(r2, n, p):
    return 1 - (1 - r2) * (n - 1) / (n - p - 1)

print(adjusted_r2(0.800, 20, 1))  # ~0.789
print(adjusted_r2(0.801, 20, 2))  # ~0.778
print(adjusted_r2(0.900, 20, 2))  # ~0.888
```

---

## Quick revision

- Problem: bekaar feature se bhi R² badhta hai
- Fix: degrees of freedom se adjust karo
- **R²_adj = 1 - (1 - R²) · (n-1)/(n-p-1)**
- p badhe -> penalty badhti hai
- Bekaar feature -> R²_adj girta hai, kaam ka feature -> badhta hai
- Hamesha R²_adj ≤ R²