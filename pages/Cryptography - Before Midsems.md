## Introduction
	- Cryptography - Achieve PAIN (Privacy & Confidential, Auth, Integrity, Non reputation[Proof of Action])
	- Cryptoanalysis - Defeat PAIN
	- #### Symbols
		- Plain Text P over alphabet \Sigma
		- Cipher Text C over alphabet \Delta
		- Key space = K
		- $w = d_k(e_k(w))$, w is plain text, k is key, d/e are decryption/encryption functions
		- cryptosystem is a five-tuple (P, C, K, E, D)
		- if $$e_k=d_k$$, then k is *involuntary key*.
	- Avalanche effect: Small change in input, should cause large unpredictable change in output
	- The cryptosystem should *not be closed under composition*
	- Asymmetric key => Use public key to encrypt and private key to decrypt;
		- Slower than symmetric encryption, because $$k = b^x mod\ m$$ (or y) is shared, and encryption key is $k=b^x.b^y\ mod\ m$ which has to be calculated!
	- Symmetric key => Most secure and performant, but key exchange is problematic.
- ## Classical ciphers
	- ### Transposition Cipher
		- #### Columnar: Type in rows(exclude space), read in columns separated by space
			- Complete: Left spaces are replaced with 'z'
			  logseq.order-list-type:: number
			- Incomplete
			  logseq.order-list-type:: number
			- Distance between two consecutive `z` may give column size.
		- #### Row: Type in column, read in rows
		- #### Keyword Column Transposition: Like columnar but uses a key, and reads in map of alphabetical order of letter of keys!
	- ### Shift Cipher
		- #### Caesar cipher (Shift $\le$ 13; ROT13 => Shift by 13)
		- #### Affine cipher
			- $c_i ≡ (ap_i + b) mod\ 26$
			- character A=0, Z=25
			- Key space = 26φ(26)
		- #### Mono-alphabetic cipher: map each character to something else
			- Frequency analysis attacks
			- Homophone cipher: Replace each letter with variety of substitute dependent on frequency!
			  logseq.order-list-type:: number
			- Polygraphic Cipher: Substitution of a group of characters
			  logseq.order-list-type:: number
				- ##### Playfair cipher
				  logseq.order-list-type:: number
					- Take key, enter non-repeated letter in 5x5 box, fill remaining with increasing order of alphabet that haven't occurred before!
					- *I & J in same block*
					- ![image.png](../assets/image_1726312051911_0.png){:height 174, :width 320}
					- Cipher is next in same row
			- Poly-alphabetic Cipher
			  logseq.order-list-type:: number
				- Vigenére Cipher
				  logseq.order-list-type:: number
					- $K = (k_0, k_1, ... , k_{n−1}) ,\ where\ each\ k_i ∈ \{0, 1, · · · , 25\}$
					- $C_i ≡ (P_i + k_{i\ mod\ n}) mod\ 26$
					- ![image.png](../assets/image_1726313318369_0.png){:height 169, :width 321}
					- Kasiski Test: GCD of separation between two identical segments in cipher gives us the possible length of cipher.
					- Index of Coincidence: probability that two randomly selected letters in the ciphertext represent the same plaintext symbol
						- ![image.png](../assets/image_1726313609639_0.png){:height 96, :width 298}
						- 0.03846 ≤ I ≤ 0.065
				- Hill cipher
				  logseq.order-list-type:: number
					- ![image.png](../assets/image_1726313863756_0.png)
	- ### Codebook Cipher
		- A book with mapping of plain segment to cipher and vice-versa. The longer the block more immune to frequency analysis!
		- #### Block Cipher
			- $T[X] = f_{key}(X)$ T is Table, and X is block
	- ### One time pad
		- Encryption: Plaintext ⊕ Key = Ciphertext
		- Key length = Length of plain text
	- ### Engima (Machine cipher)
		- Poly alphabetic substitution cipher, but with each letter typed permutation changes
- ## Shannon's Theory and Perfect Secrecy
	- For a system to be secure, it should require at-least 2^112 ops before breaking it.
	- |Attack|Compromised|
	  |--|--|
	  |KCA|Cipher Text|
	  |KPA|Plain Text|
	  |CPA/CPA1|Cipher Text for any choosen plain text|
	  |CCA/CCA1|Plain text for any choosen cipher text|
	  |ACPA/CPA2|CPA, in which choice of plain text depend on cipher text from previous request|
	  |ACCA/CCA2|CCA, in which choice of cipher text depend on plain text from previous request|
	- ### Perfect Secrecy
		- #### Introduction
			- Probability of C given K & P
			- ![image.png](../assets/image_1726381040007_0.png)
			- ![image.png](../assets/image_1726382486332_0.png)
			- ![image.png](../assets/image_1726382504034_0.png)
			- K and P are independent
		- Perfect secrecy or Shannon-secure: $$Pr[x|y] = Pr[x] ∀x ∈ P, y ∈ C.$$
		- or every x ∈ P and every y ∈ C, ∃ ! K : eK (x) = y.
		- Let $P = C = K = (Z_2)^n$ for n ≥ 1. For $K ∈ (Z_2)^n$ , $e_K (x) = (x_1 + K_1, . . . , x_n + K_n)$ mod 2
	- #### Self Information (less probability => more information)
		- ![image.png](../assets/image_1726383763625_0.png)
	- #### Entropy (average self information)
		- ![image.png](../assets/image_1726384169878_0.png)
		- ##### Theorems
			- H(X) ≤ log2 n where n=|X| & equality if when Pr[x]=1/n
			- H(X, Y) ≤ H(X) + H(Y) & equality if X, Y are independent
			- $H(X|Y) = ∑_y Pr[y].H(X|y) = − ∑_y ∑_x Pr[y]Pr[x|y] log_2 Pr[x|y]$.
			- H(X, Y) = H(Y) + H(X|Y)
			- H(X|Y) ≤ H(X) & equality if X, Y are independent
			- H(K|C) = H(K) + H(P) − H(C)
	- #### Spurious Key (false positive keys that give wrong meaning when decrypting a cipher)
		-
		-
		-