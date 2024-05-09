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
	- ### Euler Totient Function \Phi(n)
		- \Phi(n) = No of positive integers less than n who are relative prime to n
		- |Criteria of n|$$\Phi(n)$$|
		  |--|--|
		  |n is prime|n - 1|
		  |n = p * q, where p, q is prime and p \ne q|(p - 1)(q - 1)|
		  |n = a * b[:br]either or both are composite|$n * (1 - 1/p1) (1 - 1/p2) .....$[:br][:br]where p1, p2,.... are distinct primes[:br]n=${p1}^{a1}.{p2}^{a2}.{p3}^{a3}.....$|
	- ### Fermat's Little Theorem
		- If p is prime and a is +ve integer not divisible by p
		- $a^{p-1}\equiv 1\ mod\ p$
	- ### Euler's Theorem
		- Every positive integer a & n and are relatively prime, then
			- $a^{\Phi(n)} \equiv\ 1\ mod\ n$
	- ### Primitive Root
		- a is said to be primitive root of prime number p if a mod p, $$a^2$$ mod p .... $a^{p-1}$ mod p are distinct.
	- ### Multiplicate Inverse
		- Only if both number are relatively co-prime
		- ![image.png](../assets/image_1714675325084_0.png){:height 189, :width 227}
		- ### Using extended euclidean algorithm
			- ![image.png](../assets/image_1714828535080_0.png){:height 245, :width 486}
			- ![image.png](../assets/image_1714828760651_0.png){:height 183, :width 459}
- ## Chinese Remainder Theorem
	- X \cong $a_1$ mod $m_1$
	  X \cong $a_2$ mod $m_2$
	  ...
	  X \cong $a_n$ mod $m_n$
		- This equation has unique solution if moduli are distinct and relatively prime.
	- X = ($$a_1M_1M_1^{-1} + a_2M_2M_2^{-1} + ...$$) mod M
		- M = $$m_1*m_2*m_3*....$$
		- $M_n$ = $$M/m_n$$
		- $M_n * M_n^{-1} \cong 1\ mod\ m_n$
	- kX \cong a mod m
		- X \cong $k^{-1}$ a mod m
- ## Discrete logarithm problem
	- ![image.png](../assets/image_1714831582740_0.png){:height 190, :width 561}
	- ![image.png](../assets/image_1714831700835_0.png){:height 231, :width 303}
- ## Factoring Fermat's Algorithm
	- To factor n = A.B; Used when A,B are close
		- Solve for integral value of X = $\sqrt{n + Y^2}$ and put solution in n = (X + Y)(X - Y)
- ## Fermat's primality test
	- Test :
		- If p is prime, then $a^p$ - a is a multiple of p \forall 1 \le a \lt p
	- Not accurate, fails for number like 561
- ## Miller Rabin primality test
	- n - 1 = $2^k$ * m (greatest value of k satisfying it)
	  logseq.order-list-type:: number
	- Choose a, 1 \lt a \lt n - 1
	  logseq.order-list-type:: number
	- Compute $b_0=a^m mod n$
	  logseq.order-list-type:: number
		- If $b_0$ is +1, then composite, -1 then *probably* prime
		  logseq.order-list-type:: number
		- If neither, then calculate $b_1$..... until we get one, using $b_i = b_{i-1}^2 (mod\ n)$
		  logseq.order-list-type:: number
- ## Bézout's identity
	- Let *a* and *b* be integers with greatest common divisor *d*. Then there exist integers *x* and *y* such that *ax* + *by* = *d*
	- A result of extended euclidean algo.