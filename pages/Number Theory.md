## Modular Arithmetic
	- 15 \equiv 3 mod 12
	- a \equiv b mod m
		- a = km + b
	- ### Properties
		- (a % n + b % n) %n = (a + b) % n
		- (a % n - b % n) %n = (a - b) % n
		- (a % n * b % n) %n = (a * b) % n
- ## Modular Exponentiation
	- $a^b$ mod m
	- ![image.png](../assets/image_1714039966539_0.png){:height 191, :width 483}
	- ![image.png](../assets/image_1714041024750_0.png){:height 163, :width 315}
	- Last n digits of a number
- ## GCD - Euclidean Algorithm
	- Repeated division till remainder is 0
		- GCD(x, 0) = x
		- GCD(a, b) = GCD(b, a mod b)
	- Relative Prime : GCD(a, b) = 1