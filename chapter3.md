Chapter 3 — Derivatives: Slope at an Exact Point

Machine Learning Mathematics — ML / DL / PyTorch Learning Path

1. Chapter Overview

Chapter 1 me humne padha:

y=wx+b
	​


aur samjha ki:

Slope=
Δx
Δy
	​

	​


Chapter 2 me humne dekha ki curve ke case me slope har point par different ho sakti hai.

Isliye hume ek important question mila:

Curve ke kisi exact point par slope kaise find karein?

Iska answer hai:

Derivative
	​


Derivative ka basic meaning:

Kisi function ke kisi particular point par uski instantaneous rate of change ya instantaneous slope.

Machine Learning me derivative bahut important hai because Gradient Descent derivative/gradient ka use karke decide karta hai ki parameters (w, b) ko kis direction me change karna hai.

2. Average Slope vs Instantaneous Slope

Sabse pehle difference samjho.

Average Slope

Do points ke beech slope:

m=
x
2
	​

−x
1
	​

y
2
	​

−y
1
	​

	​

	​


Ye batata hai:

Do points ke beech average change kitna hai.

Instantaneous Slope

Sirf ek exact point par slope chahiye.

Iske liye derivative use hota hai:

dx
dy
	​

	​


Ye batata hai:

Exactly us point par y, x ke respect me kitni speed se change ho raha hai.

3. Example: Straight Line

Consider:

y=2x

Iski table:

x	y
0	0
1	2
2	4
3	6

Slope:

m=
3−2
6−4
	​

m=2

Straight line me slope har jagah same hai:

m=2
	​

4. Problem Curve me aati hai

Consider:

y=x
2

Values:

x	y
0	0
1	1
2	4
3	9
4	16

Ye straight line nahi hai.

Graph roughly:

y
↑
|
|                       ●
|                  ●
|             ●
|        ●
|    ●
|___●________________________→ x

Curve par slope har point par different hoti hai.

5. x = 2 par Slope kaise nikalein?

Point:

A=(2,4)

Ab ek doosra point lete hain:

B=(3,9)

Average slope:

m=
3−2
9−4
	​

m=5

Lekin ye x=2 par exact slope nahi hai.

Ye (2,4) aur (3,9) ke beech ki average slope hai.

6. Second Point ko paas lekar aao

Ab B ko A ke paas le aate hain.

Take:

B=(2.5,6.25)

Slope:

m=
2.5−2
6.25−4
	​

=
0.5
2.25
	​

=4.5

Aur paas:

B=(2.1,4.41)

Slope:

m=
2.1−2
4.41−4
	​

=
0.1
0.41
	​

=4.1

Aur paas:

B=(2.01,4.0401)
m=
2.01−2
4.0401−4
	​

=
0.01
0.0401
	​

=4.01

Aur paas:

B=(2.001,4.004001)
m=4.001

Observe:

Second Point	Average Slope
(3,9)	5
(2.5,6.25)	4.5
(2.1,4.41)	4.1
(2.01,4.0401)	4.01
(2.001,4.004001)	4.001

Slope continuously:

5→4.5→4.1→4.01→4.001

Aur ye:

4
	​


ke paas ja rahi hai.

Isi concept ko Limit represent karta hai.

7. Limit ka Role

Mathematically hum likhte hain:

h→0
	​


Iska meaning:

h zero nahi hai, balki zero ke infinitely close approach kar raha hai.

Example:

h=0.1

then:

h=0.01

then:

h=0.001

then:

h=0.0001

Ye values zero ke closer and closer ja rahi hain.

8. Derivative ki Definition

Derivative ki mathematical definition:

f
′
(x)=
h→0
lim
	​

h
f(x+h)−f(x)
	​

	​


Ye first-principles definition of derivative hai.

Isko samjho:

f(x)
  │
  │
  │   Original point
  ●
   \
    \
     ●
     │
  f(x+h)

Distance = h

Do points ke beech:

Δx=h

Aur:

Δy=f(x+h)−f(x)

Therefore:

Δx
Δy
	​

=
h
f(x+h)−f(x)
	​


Ab second point ko infinitely close le aate hain:

h→0

Therefore:

f
′
(x)=
h→0
lim
	​

h
f(x+h)−f(x)
	​

	​

9. h kya represent karta hai?

h simply change in x hai.

Suppose current point:

x

Second point:

x+h

To difference:

(x+h)−x=h

Therefore:

Δx=h
	​

10. f(x+h) kya hai?

Suppose:

f(x)=x
2

Then:

f(x+h)=(x+h)
2

Meaning:

Function me x ki jagah x+h put karo.

11. First Principles se x² ka Derivative

Ab actual derivation karte hain.

Function:

f(x)=x
2
	​


Derivative definition:

f
′
(x)=
h→0
lim
	​

h
f(x+h)−f(x)
	​

Step 1: Function substitute karo

Because:

f(x)=x
2

Therefore:

f(x+h)=(x+h)
2

So:

f
′
(x)=
h→0
lim
	​

h
(x+h)
2
−x
2
	​

Step 2: Square expand karo

Formula:

(a+b)
2
=a
2
+2ab+b
2

Therefore:

(x+h)
2
=x
2
+2xh+h
2

Substitute:

f
′
(x)=
h→0
lim
	​

h
x
2
+2xh+h
2
−x
2
	​

Step 3: x² cancel karo
x
2
−x
2
=0

Therefore:

f
′
(x)=
h→0
lim
	​

h
2xh+h
2
	​

Step 4: h common lo

Numerator:

2xh+h
2

h common:

h(2x+h)

Therefore:

f
′
(x)=
h→0
lim
	​

h
h(2x+h)
	​

Step 5: h cancel karo
f
′
(x)=
h→0
lim
	​

(2x+h)
Step 6: Limit apply karo

As:

h→0

Therefore:

2x+h→2x+0

So:

f
′
(x)=2x
	​


Therefore:

dx
d
	​

(x
2
)=2x
	​

12. Important: h = 0 Directly kyun nahi put kiya?

Ye bahut important concept hai.

Starting formula:

h
f(x+h)−f(x)
	​


Agar directly:

h=0

put kar do:

0
f(x)−f(x)
	​

=
0
0
	​


0/0 undefined hai.

Isliye hum pehle algebraically simplify karte hain:

h
(x+h)
2
−x
2
	​


↓

h
h(2x+h)
	​


↓

2x+h

Ab h denominator me nahi hai.

Tab:

h→0

apply kar sakte hain.

13. Derivative at a Particular Point

Humne derive kiya:

f
′
(x)=2x

Ab suppose hume:

x=2

par slope chahiye.

Then:

f
′
(2)=2(2)
f
′
(2)=4
	​


Therefore:

y=x² ke graph par x=2 par instantaneous slope = 4.

14. x = 3 par slope

Same derivative:

f
′
(x)=2x

Put:

x=3
f
′
(3)=2(3)
f
′
(3)=6
	​


Notice:

At:

x=2

slope:

4

At:

x=3

slope:

6

Isliye curve ki slope har point par different hai.

15. Derivative ka Graphical Meaning

Function:

y=x
2

Graph:

y
↑
│
│                 /
│              __/
│           __/
│        __/
│     __/
│___/______________________→ x
       ↑
      x=2

At x=2, curve ko touch karne wali ek straight line hoti hai.

Us line ko:

Tangent Line
	​


kehte hain.

Tangent line ki slope:

f
′
(2)=4
	​


So:

Derivative = tangent line ki slope.

16. Secant Line vs Tangent Line

Ye terminology important hai.

Secant Line

Curve ke do points ko connect karti hai.

●
 \
  \
   ●

Uski slope:

Δx
Δy
	​

Tangent Line

Curve ko ek point par touch karti hai.

      /
     /
----●---------
   /

Uski slope:

Derivative
	​

17. Derivative Notation

Derivative ko different ways me likha ja sakta hai.

Leibniz notation
dx
dy
	​

	​


Meaning:

y ka derivative with respect to x.

Function notation
f
′
(x)
	​


Read:

f prime of x.

Operator notation
dx
d
	​

f(x)
	​


Example:

dx
d
	​

(x
2
)

Answer:

2x
18. d/dx ko kaise samjhein?
dx
d
	​


normal fraction ki tarah treat nahi karna chahiye.

Ye ek derivative operator hai.

Iska meaning:

"x ke respect me derivative nikalo."

Example:

dx
d
	​

(x
2
)

Means:

x² ka x ke respect me derivative nikalo.

Answer:

2x
19. "With Respect To" ka Meaning

Suppose:

y=2x
dx
dy
	​

=2

Matlab:

x ko change karne par y kitna change hota hai.

But agar function me multiple variables hain:

J(w,b)

To hume specify karna padega ki kis variable ke respect me change dekh rahe hain.

For w:

∂w
∂J
	​

	​


For b:

∂b
∂J
	​

	​

20. Derivative ka Physical Meaning

Derivative sirf graph ki slope nahi hai.

General meaning:

Rate of Change
	​


Example: Distance vs Time

s(t)

Velocity:

v=
dt
ds
	​

	​


Matlab:

Time change hone par distance kitni speed se change ho raha hai.

Example

Suppose:

s=t
2

Then:

dt
ds
	​

=2t

At:

t=3

Velocity:

v=2(3)=6

So:

v=6
	​

21. Derivative ka ML Meaning

Machine Learning me humare paas Cost Function hota hai.

For example:

J(w)

Graph:

Cost J
↑
│\
│ \
│  \
│   \
│    \____
│         \____
│              \
└──────────────────→ w

Yahan:

X-axis = w
Y-axis = J(w)

Derivative:

dw
dJ
	​

	​


batata hai:

Current w par Cost kis direction me change ho rahi hai aur kitni steeply change ho rahi hai.

22. Positive Gradient

Suppose:

dw
dJ
	​

>0

Graph ka slope positive hai.

Matlab:

w increase karne par Cost increase ho rahi hai.

Gradient Descent:

w
new
	​

=w
old
	​

−α
dw
dJ
	​


Positive derivative subtract hoga.

Therefore w decrease karega.

23. Negative Gradient

Suppose:

dw
dJ
	​

<0

Matlab:

w increase karne par Cost decrease ho rahi hai.

Gradient Descent:

w
new
	​

=w
old
	​

−α
dw
dJ
	​


Negative value subtract karne se:

−negative=+positive

Therefore w increase karega.

24. Example: Negative Gradient

Suppose:

w=1
dw
dJ
	​

=−4

Learning rate:

α=0.1

Gradient Descent:

w
new
	​

=w
old
	​

−α
dw
dJ
	​


Substitute:

w
new
	​

=1−(0.1)(−4)
=1+0.4
w
new
	​

=1.4
	​

25. α Learning Rate
α=Learning Rate
	​


Important:

α derivative se calculate nahi hota.

Hum training ke liye learning rate choose/set karte hain.

Example:

α=0.1

or:

α=0.01

or:

α=0.001
α ka kaam

Derivative:

Direction aur slope ki steepness batata hai.

Learning rate:

Kitna bada step lena hai ye control karta hai.

Therefore:

Component	Meaning
dJ/dw	Direction + slope
α	Step size
w	Current parameter
w_new	Updated parameter
26. Learning Rate Too Small

Suppose:

α=0.00001

Steps bahut small honge.

Training:

● → ● → ● → ● → ● → ●

Model minimum tak pahunchne me bahut time le sakta hai.

27. Learning Rate Too Large

Agar:

α

bahut bada hai, model minimum ko cross karke baar-baar jump kar sakta hai.

●        ●
     ●        ●
          ●

Training unstable ho sakti hai.

28. Appropriate Learning Rate

Suitable learning rate hone par model gradually minimum ki taraf move karta hai:

●
  ●
    ●
      ●
        ●
          ●
            ●

Goal:

Cost minimum karna
	​

29. Gradient Descent ka Basic Formula

For one parameter w:

w
new
	​

=w
old
	​

−α
dw
dJ
	​

	​


For multiple parameters:

w
new
	​

=w
old
	​

−α
∂w
∂J
	​

	​


and:

b
new
	​

=b
old
	​

−α
∂b
∂J
	​

	​

30. Old w aur New w ka Important Concept

Gradient current point par calculate hota hai.

Suppose:

w
old
	​

=2
b
old
	​

=3

Current point:

(2,3)

Isi point par calculate hua:

dw=
∂w
∂J
	​


and:

db=
∂b
∂J
	​


Suppose:

dw=5
db=4

Then:

w
new
	​

=2−α(5)
b
new
	​

=3−α(4)

Dono gradients same old point (2,3) se aaye.

Isliye updates conceptually simultaneous hote hain.

31. Why Old Values?

Imagine current point:

(w,b)=(2,3)

Gradient calculate hua:

(dw,db)

Ye gradient isi point ka direction batata hai.

Agar pehle w change kar diya aur phir b ko update karte waqt new w use kiya, to tum different point par chale gaye.

Conceptually:

Old Point
(w_old, b_old)
       │
       │ calculate gradients
       ▼
(dw, db)
       │
       ▼
New Point
(w_new, b_new)

Correct implementation conceptually:

new_w = w - alpha * dw
new_b = b - alpha * db

w = new_w
b = new_b

Ya mathematical notation me dono updates ko same old values se calculate kiya jata hai.

32. Derivative Rules ka Preview

First principles se:

dx
d
	​

(x
2
)=2x

Lekin har baar limit se derivative calculate karna lengthy hai.

Isliye calculus me rules develop kiye gaye.

Constant Rule
dx
d
	​

(c)=0
	​


Example:

dx
d
	​

(5)=0
Power Rule
dx
d
	​

(x
n
)=nx
n−1
	​


Example:

dx
d
	​

(x
2
)=2x

Example:

dx
d
	​

(x
3
)=3x
2

Example:

dx
d
	​

(x
5
)=5x
4

Power Rule ko next chapter me detail me derive aur practice karenge.

33. Constant Multiplication Rule

If:

f(x)=5x
2

Then:

dx
d
	​

(5x
2
)=5
dx
d
	​

(x
2
)
=5(2x)
=10x
	​

34. Sum Rule

If:

f(x)=x
2
+x
3

Then:

dx
d
	​

(x
2
+x
3
)=
dx
d
	​

(x
2
)+
dx
d
	​

(x
3
)
=2x+3x
2

Therefore:

f
′
(x)=2x+3x
2
	​

35. Complete Example

Given:

f(x)=3x
2
+5x+7

Derivative:

f
′
(x)=
dx
d
	​

(3x
2
)+
dx
d
	​

(5x)+
dx
d
	​

(7)

First term:

dx
d
	​

(3x
2
)=6x

Second:

dx
d
	​

(5x)=5

Third:

dx
d
	​

(7)=0

Therefore:

f
′
(x)=6x+5
	​

36. Derivative ka Quick Verification

Function:

f(x)=x
2

Derivative:

f
′
(x)=2x

At:

x=2

Derivative:

f
′
(2)=4

Numerically humne earlier nearby points se dekha:

4.1,4.01,4.001

which approach:

4

Therefore calculus result consistent hai.

37. Chapter 3 ka Complete Concept Map
                 FUNCTION
                    │
                    ▼
                  GRAPH
                    │
                    ▼
              TWO POINTS
                    │
                    ▼
              Average Slope
                    │
                    ▼
          Second Point → First Point
                    │
                    ▼
                  h → 0
                    │
                    ▼
                 LIMIT
                    │
                    ▼
               DERIVATIVE
                    │
                    ▼
          Instantaneous Slope
                    │
                    ▼
            Cost Function J(w)
                    │
                    ▼
                 dJ/dw
                    │
                    ▼
              Gradient Descent
                    │
                    ▼
                Update w
38. Most Important Formulas
Average slope
m=
Δx
Δy
	​

	​

Derivative definition
f
′
(x)=
h→0
lim
	​

h
f(x+h)−f(x)
	​

	​

Derivative of x²
dx
d
	​

(x
2
)=2x
	​

Derivative of a constant
dx
d
	​

(c)=0
	​

Power rule
dx
d
	​

(x
n
)=nx
n−1
	​

Gradient Descent
w
new
	​

=w
old
	​

−α
∂w
∂J
	​

	​

Bias update
b
new
	​

=b
old
	​

−α
∂b
∂J
	​

	​

39. Chapter 3 — Key Terms
Term	Meaning
Derivative	Exact/instantaneous rate of change
Instantaneous slope	Ek exact point par slope
Average slope	Do points ke beech slope
Secant line	Two points ko connect karti hai
Tangent line	Ek point par curve ko touch karti hai
Limit	Kisi value ke infinitely close approach ko describe karta hai
h	Change in x
f(x+h)	Function evaluated at x+h
f'(x)	Derivative of f(x)
d/dx	Derivative with respect to x
dJ/dw	Cost ka w ke respect me derivative
α	Learning rate
Gradient	Multiple parameters ke derivatives ka collection
40. Chapter 3 — Final Mental Model

Is poore chapter ko ek chain ki tarah yaad rakho:

Two Points→Average Slope
	​


Second point ko current point ke closer lekar jao:

h→0
	​


Then:

Limit of Average Slope=Instantaneous Slope
	​


Aur:

Instantaneous Slope=Derivative
	​


For:

f(x)=x
2

first principles se:

f
′
(x)=2x
	​


Machine Learning me:

∂w
∂J
	​

	​


Cost function ki current slope batata hai.

Aur Gradient Descent:

w
new
	​

=w
old
	​

−α
∂w
∂J
	​

	​


me:

∂J/∂w → kidhar jaana hai + slope kitni hai
α → kitna bada step lena hai
w_new → new position
41. Practice Questions
Q1

First principles se prove karo:

dx
d
	​

(x
2
)=2x
Q2

Find:

dx
d
	​

(x
3
)
Q3

Find:

dx
d
	​

(5x
2
)
Q4

Find:

dx
d
	​

(3x
2
+4x+7)
Q5

For:

f(x)=x
2

find:

f
′
(2)
Q6

For:

J(w)=w
2

find:

dw
dJ
	​

Q7

Suppose:

w
old
	​

=2
dw
dJ
	​

=−3
α=0.1

Find:

w
new
	​


using:

w
new
	​

=w
old
	​

−α
dw
dJ
	​

42. Final Takeaway

Derivative koi magic formula nahi hai.

Humne pehle:

Δx
Δy
	​


se two-point slope nikali.

Phir second point ko first point ke infinitely close le gaye:

h→0

Aur us process ka limit:

h→0
lim
	​

h
f(x+h)−f(x)
	​

	​


Derivative hai.

For:

f(x)=x
2

humne complete algebra karke prove kiya:

f
′
(x)=2x
	​


Aur isi concept ko ML me Cost Function par apply karne se:

∂w
∂J
	​

	​


milta hai, jo Gradient Descent ko batata hai ki current w se kis direction me move karna chahiye.

Chapter 3 ka core chain:

Slope→Limit→Derivative→Gradient→Gradient Descent
	​
