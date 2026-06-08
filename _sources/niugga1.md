# Matrix 2x2, Eigenvalues, Eigenvectors, dan Power Iteration

## 1. Matriks

Dari "2112", dibentuk matriks:

\[
A =
\begin{bmatrix}
2 & 1 \\
1 & 2
\end{bmatrix}
\]

---

## 2. Program Python

```python
import numpy as np

# Definisi matriks
A = np.array([[2, 1],
              [1, 2]])

print("Matriks A:")
print(A)

# Eigenvalue dan Eigenvector
eigenvalues, eigenvectors = np.linalg.eig(A)

print("\nEigenvalues:")
print(eigenvalues)

print("\nEigenvectors:")
print(eigenvectors)

# Power Iteration (10 iterasi)
x = np.array([1.0, 1.0])  # vektor awal

print("\nIterasi Power Method:")
for i in range(10):
    x = A @ x
    x = x / np.linalg.norm(x)
    print(f"Iterasi ke-{i+1}: {x}")

# Aproksimasi eigenvalue terbesar
lambda_approx = x.T @ A @ x

print("\nPerkiraan eigenvalue terbesar:")
print(lambda_approx)