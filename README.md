# Componentes Simétricas — Transformación de Fortescue

Implementación en Python de la transformación de componentes simétricas (secuencia positiva, negativa y cero) a partir de valores de fase desbalanceados, incluyendo la demostración analítica de la matriz inversa de Fortescue.

## Contenido

- **Demostración matemática** ([`demostracion.md`](./demostracion.md)): derivación de A⁻¹ = (1/3)A* a partir de la propiedad de números complejos z·z* = |z|², sin recurrir a inversión numérica genérica.
- **Notebook** ([`Componentes_Simetricas.ipynb`](./Componentes_Simetricas.ipynb)): cálculo de componentes de secuencia (V₀, V₁, V₂ / I₀, I₁, I₂) a partir de valores de fase (a, b, c), reconstrucción inversa y verificación numérica.

## Fundamento teórico

La transformación de Fortescue relaciona las magnitudes de fase con sus componentes simétricas mediante:

$$
\begin{bmatrix} V_a \\\\ V_b \\\\ V_c \end{bmatrix} = A \begin{bmatrix} V_a^{(0)} \\\\ V_a^{(1)} \\\\ V_a^{(2)} \end{bmatrix}, \qquad
A = \begin{bmatrix} 1&1&1 \\\\ 1&a^2&a \\\\ 1&a&a^2 \end{bmatrix}, \quad a = 1\angle120^\circ
$$

Se demuestra que $A^{-1} = \frac{1}{3}A^*$ (ver [`demostracion.md`](./demostracion.md) para la derivación completa), lo cual permite obtener las componentes simétricas sin recurrir a inversión matricial genérica:

$$
\begin{bmatrix} V_a^{(0)} \\\\ V_a^{(1)} \\\\ V_a^{(2)} \end{bmatrix} = \frac{1}{3}\begin{bmatrix} 1&1&1 \\\\ 1&a&a^2 \\\\ 1&a^2&a \end{bmatrix}\begin{bmatrix} V_a \\\\ V_b \\\\ V_c \end{bmatrix}
$$

## Uso

```python
import numpy as np

a = np.exp(1j * np.deg2rad(120))
A = np.array([[1,1,1],[1,a**2,a],[1,a,a**2]])
A_inv = (1/3) * np.conj(A)

Va = 220 + 0j
Vb = 150 * np.exp(1j*np.deg2rad(-130))
Vc = 180 * np.exp(1j*np.deg2rad(115))

V_abc = np.array([Va, Vb, Vc])
V_012 = A_inv @ V_abc   # V0, V1, V2
```

## Requisitos

- Python 3.x
- NumPy

## Motivación

Este cálculo es de uso constante en análisis de fallas asimétricas y sistemas desbalanceados en ingeniería de sistemas de potencia. El objetivo de este repositorio es tener la herramienta lista y verificada, con la demostración matemática documentada en vez de tratarla como una "caja negra".
