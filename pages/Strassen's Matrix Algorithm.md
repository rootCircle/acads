- Multiplying two matrix
- O(n^2.8)
- Matrix Multiplication - Col(1st) = Row(2nd)
- Naive multiplication complexity = O(n^3)
- In naive multiplication
  $T\left(n\right)=8T\left(\frac{n}{2}\right)+\relax\theta(n^2)$
- In Strassen's matrix Multiplication
  $T\left(n\right)=7T\left(\frac{n}{2}\right)+\theta(n^2)$
- Constraint - Dimension of matrix should be in 2^n and can't multiply more than two matrixes
- 4x4 to break into 2x2 and so on.......
- Non-feasible in practically terms
- Theoretically faster