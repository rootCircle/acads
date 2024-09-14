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
	- ### One
		-