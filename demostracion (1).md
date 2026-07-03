# Demostración: Inversa de la Matriz de Fortescue

## Planteamiento

Sea la matriz de transformación de componentes simétricas:

$$
A = \begin{bmatrix} 1 & 1 & 1 \\\\ 1 & a^2 & a \\\\ 1 & a & a^2 \end{bmatrix}, \qquad a = 1\angle 120^\circ = e^{j2\pi/3}
$$

tal que:

$$
\begin{bmatrix} V_a \\\\ V_b \\\\ V_c \end{bmatrix} = A \begin{bmatrix} V_a^{(0)} \\\\ V_a^{(1)} \\\\ V_a^{(2)} \end{bmatrix}
$$

Buscamos $A^{-1}$, definida por $A \cdot A^{-1} = I$.

## Paso 1: Propiedad clave de los números complejos

Para cualquier número complejo $z$ de magnitud unitaria:

$$
z \cdot z^* = |z|^2
$$

En particular, dado que $|a| = 1$:

$$
a \cdot a^* = |a| = 1\angle 120^\circ \cdot 1\angle -120^\circ = 1\angle 0^\circ = 1
$$

## Paso 2: Cálculo de $A \cdot A^*$

Se propone $A \cdot A^* = I$, donde $A^*$ es la matriz conjugada de $A$:

$$
A^* = \begin{bmatrix} 1 & 1 & 1 \\\\ 1 & a & a^2 \\\\ 1 & a^2 & a \end{bmatrix}
$$

Multiplicando fila por columna, $I_{ij} = \sum_k A_{ik} \, A^*_{kj}$:

**Diagonal:**
$$
I_{11} = 1+1+1 = 3
$$
$$
I_{22} = 1+1+1 = 3
$$
$$
I_{33} = 1+1+1 = 3
$$

**Fuera de la diagonal**, usando la identidad $1+a+a^2=0$ (suma de tres fasores unitarios a 120°):

$$
I_{12} = 1+a+a^2 = 0
$$
$$
I_{13} = 1+a^2+a = 0
$$
$$
I_{21} = 1+a^2+a = 0
$$
$$
I_{23} = 1+a^4+a^2 = 1+a+a^2 = 0
$$
$$
I_{31} = 1+a+a^2 = 0
$$
$$
I_{32} = 1+a^2+a^4 = 1+a^2+a = 0
$$

(se usó $a^3 = 1 \Rightarrow a^4 = a$)

## Paso 3: Resultado

$$
A \cdot A^* = \begin{bmatrix} 3&0&0 \\\\ 0&3&0 \\\\ 0&0&3 \end{bmatrix} = 3I
$$

## Paso 4: Despeje de la inversa

Por definición de matriz inversa, si $A \cdot B = I$, entonces $B = A^{-1}$.

De $A \cdot A^* = 3I$:

$$
A \cdot \left(\frac{1}{3}A^*\right) = I
$$

$$
\boxed{A^{-1} = \frac{1}{3}A^*}
$$

## Aplicación: componentes simétricas

$$
\begin{bmatrix} V_a^{(0)} \\\\ V_a^{(1)} \\\\ V_a^{(2)} \end{bmatrix} = \frac{1}{3}\begin{bmatrix} 1&1&1 \\\\ 1&a&a^2 \\\\ 1&a^2&a \end{bmatrix}\begin{bmatrix} V_a \\\\ V_b \\\\ V_c \end{bmatrix}
$$

$$
V_a^{(0)} = \frac{1}{3}(V_a + V_b + V_c)
$$
$$
V_a^{(1)} = \frac{1}{3}(V_a + aV_b + a^2V_c)
$$
$$
V_a^{(2)} = \frac{1}{3}(V_a + a^2V_b + aV_c)
$$
