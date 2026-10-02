Chapter 2 – Limits (Why Derivative Exists?)
Sabse pehle ek question

Abhi tak humne slope nikali thi.

Formula:

m=
Δx
Δy
	​

	​


Example:

Points

A = (1,2)

B = (3,6)

Slope

=
3−1
6−2
	​

=
2
4
	​

=2

Ye easy tha.

Kyun?

Kyuki line seedhi thi.

Lekin agar graph curve ho to?

Suppose function hai

y=x
2

Table

x	y
0	0
1	1
2	4
3	9
4	16

Graph kuch aisa dikhega:

y
16 |                         ●
14 |
12 |
10 |                    ●
 8 |
 6 |
 4 |              ●
 2 |         ●
 0 |●____________________________ x
    0    1    2    3    4

Ye straight line nahi hai.

Question

Agar koi puche

x = 2 par slope kitni hai?

Ab kya karoge?

Formula

Δx
Δy
	​


lagayenge?

Nahi.

Kyuki ek point ki slope exist hi nahi karti.

Slope ke liye 2 points chahiye.

Chalo try karte hain

Point A

(2,4)

Point B

(3,9)

Slope

=
3−2
9−4
	​

=5

Answer

Slope = 5

Lekin

Agar

Point B

(4,16)

Slope

=
4−2
16−4
	​

=
2
12
	​

=6

Ab slope

6

Aa gayi.

Phir

Point B

(2.5,6.25)

Slope

=
2.5−2
6.25−4
	​

=
0.5
2.25
	​

=4.5

Notice kya hua?

Second Point	Slope
(3,9)	5
(4,16)	6
(2.5,6.25)	4.5

Har baar answer alag.

Matlab

Curve ki slope fixed nahi hoti.

Fir mathematicians ne kya socha?

Unhone bola

Agar second point ko first point ke bahut hi paas le aaye?

Yahi Calculus ka birth hai.

Example

First point

(2,4)

Second point

(2.1,4.41)

Slope

=
2.1−2
4.41−4
	​

=
0.1
0.41
	​

=4.1

Aur paas

Second point

(2.01,4.0401)

Slope

=
0.01
4.0401−4
	​

=4.01

Aur paas

Second point

(2.001,4.004001)

Slope

=
0.001
4.004001−4
	​

=4.001

Table dekho

Second Point	Slope
(3,9)	5
(2.5,6.25)	4.5
(2.1,4.41)	4.1
(2.01,4.0401)	4.01
(2.001,4.004001)	4.001

Kya notice hua?

Sab answers

4

ke paas aa rahe hain.

Lekin kabhi exactly

4

nahi bane.

Isi ko bolte hain LIMIT

Mathematicians bole

Hume exact point par second point nahi rakhna.

Bas bahut paas le jana hai.

Mathematically

h→0
lim
	​

	​


Yahan

h

ka matlab

Second point kitna door hai.

Aur

h→0

Matlab

Doori zero nahi ho rahi.

Bas

Zero ke bahut paas ja rahi hai.

Ye difference bahut important hai.

Isliye derivative ka formula bana

Agar function

f(x)

hai

To derivative

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


Abhi ye formula yaad mat karo.

Bas samjho:

f(x) = pehla point
f(x+h) = doosra point (bahut paas)
h = dono ke beech ki distance
Real Life Analogy

Socho tum car chala rahe ho.

Average Speed

Delhi → Agra

200 km

4 hours

Speed

50 km/h

Ye average speed hai.

Lekin police ko ye nahi chahiye.

Police ko chahiye

2:15 PM par exactly tumhari speed kitni thi?

Ek hi instant ki speed.

Average speed se ye nahi mil sakta.

To physics ne bhi derivative use ki.

Speed=
dt
d(Distance)
	​

	​


Matlab

Instant par change kitna ho raha hai.

ML me iska kya use?

Linear Regression me line ki slope constant hoti hai.

Lekin

Cost Function

J(w)

ek curve hota hai.

Example:

Cost
 ^
 |
 |            ●
 |         ●
 |      ●
 |    ●
 |  ●
 |●__________●____________> w

Question

Current

w

par slope kitni hai?

Yahi derivative batata hai.

Aur Gradient Descent isi slope ka use karke decide karta hai:

Left jana hai?
Right jana hai?
Kitna move karna hai?
Chapter 2 Summary
Line

Slope same rehti hai.

Curve

Slope har point par alag hoti hai.

Average Slope

Do points se nikalti hai.

Instant Slope

Second point ko infinitely close laakar nikalte hain.

Isi process ko Limit bolte hain.

Aur us limit ka result hi Derivative hota hai.

🎯 Homework

Function:

y=x
2

Point fix karo:

(2,4)

Ab niche diye second points ke liye slope nikalo:

(3,9)
(2.5,6.25)
(2.1,4.41)
(2.01,4.0401)

Khud calculate karo.

Tum dekhoge answer dheere-dheere 4 ke paas aa raha hai.