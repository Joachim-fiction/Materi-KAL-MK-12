# materi operasi baris elementer 5




# Sistem Persamaan Linear 5 Variabel

Diberikan sistem persamaan linear dengan lima variabel sebagai berikut:

$$
\begin{aligned}
x_1 + x_2 &= 3 \\
x_2 + x_3 &= 5 \\
x_3 + x_4 &= 7 \\
x_4 + x_5 &= 9 \\
x_1 + x_5 &= 6
\end{aligned}
$$

## Representasi Matriks Augmentasi

Sistem persamaan tersebut dapat dinyatakan dalam bentuk matriks augmentasi:

$$
\left[
\begin{array}{ccccc|c}
1 & 1 & 0 & 0 & 0 & 3 \\
0 & 1 & 1 & 0 & 0 & 5 \\
0 & 0 & 1 & 1 & 0 & 7 \\
0 & 0 & 0 & 1 & 1 & 9 \\
1 & 0 & 0 & 0 & 1 & 6
\end{array}
\right]
$$

## Proses Eliminasi Gauss

### Langkah 1: Eliminasi Kolom Pertama

Operasi baris elementer: $R_5 \leftarrow R_5 - R_1$

$$
\left[
\begin{array}{ccccc|c}
1 & 1 & 0 & 0 & 0 & 3 \\
0 & 1 & 1 & 0 & 0 & 5 \\
0 & 0 & 1 & 1 & 0 & 7 \\
0 & 0 & 0 & 1 & 1 & 9 \\
0 & -1 & 0 & 0 & 1 & 3
\end{array}
\right]
$$

### Langkah 2: Eliminasi Kolom Kedua

Operasi: $R_5 \leftarrow R_5 + R_2$

$$
\left[
\begin{array}{ccccc|c}
1 & 1 & 0 & 0 & 0 & 3 \\
0 & 1 & 1 & 0 & 0 & 5 \\
0 & 0 & 1 & 1 & 0 & 7 \\
0 & 0 & 0 & 1 & 1 & 9 \\
0 & 0 & 1 & 0 & 1 & 8
\end{array}
\right]
$$

### Langkah 3: Eliminasi Kolom Ketiga

Operasi: $R_5 \leftarrow R_5 - R_3$

$$
\left[
\begin{array}{ccccc|c}
1 & 1 & 0 & 0 & 0 & 3 \\
0 & 1 & 1 & 0 & 0 & 5 \\
0 & 0 & 1 & 1 & 0 & 7 \\
0 & 0 & 0 & 1 & 1 & 9 \\
0 & 0 & 0 & -1 & 1 & 1
\end{array}
\right]
$$

### Langkah 4: Eliminasi Kolom Keempat

Operasi: $R_5 \leftarrow R_5 + R_4$

$$
\left[
\begin{array}{ccccc|c}
1 & 1 & 0 & 0 & 0 & 3 \\
0 & 1 & 1 & 0 & 0 & 5 \\
0 & 0 & 1 & 1 & 0 & 7 \\
0 & 0 & 0 & 1 & 1 & 9 \\
0 & 0 & 0 & 0 & 2 & 10
\end{array}
\right]
$$

## Solusi dengan Substitusi Mundur

Dari baris terakhir diperoleh:
$$2x_5 = 10 \Rightarrow \boxed{x_5 = 5}$$

Substitusi mundur memberikan:
- $x_4 + 5 = 9 \Rightarrow \boxed{x_4 = 4}$
- $x_3 + 4 = 7 \Rightarrow \boxed{x_3 = 3}$
- $x_2 + 3 = 5 \Rightarrow \boxed{x_2 = 2}$
- $x_1 + 2 = 3 \Rightarrow \boxed{x_1 = 1}$

## Hasil Akhir

Solusi sistem persamaan linear adalah:

$$\boxed{(x_1, x_2, x_3, x_4, x_5) = (1, 2, 3, 4, 5)}$$