# Bandas de Energia em um Cristal 1D: Comparação entre Modelos de Potencial

Este projeto simula e compara as bandas de energia em um cristal unidimensional usando dois modelos:

1. **Modelo quase-livre**: aproxima o potencial periódico por um termo constante α nas diagonais vizinhas da matriz Hamiltoniana.
2. **Modelo com potencial real**: calcula a matriz do potencial \( V_{m,n} \) a partir da transformada de Fourier de um potencial gaussiano \( V(x) \), e monta o Hamiltoniano completo.

---

## 📘 Objetivo

Investigar como diferentes representações do potencial periódico afetam as bandas de energia de elétrons em um cristal 1D, visualizando:

- Abertura de gaps nas bandas
- Largura das bandas permitidas
- Diferença entre um modelo aproximado (α) e um potencial realista \( V(x) \)

---

## 📂 Estrutura do Código

### 1. **Modelo com α nas diagonais secundárias**

- `build_hamiltonian_with_diag(k_value, alpha, num_G_vectors)`  
  Constroi a matriz Hamiltoniana tridiagonal com termo cinético + acoplamento α entre vetores de onda adjacentes.

- `calculate_bands(alpha, num_G_vectors, k_points)`  
  Para cada valor de \( k \), monta o Hamiltoniano e obtém os autovalores (energias).

### 2. **Modelo com potencial \( V(x) \)**

- `V_gauss(x, A, gamma)`  
  Potencial gaussiano centrado em \( x=0 \), com amplitude \( A \) e largura \( \gamma \).

- `build_V_matrix_gauss(func_V, num_G_vectors, A, gamma)`  
  Constrói a matriz \( V_{m,n} \) usando a equação:
  \[
  V_{m,n} = \int_0^1 V(x) e^{-i2\pi(m-n)x} dx
  \]

- `build_hamiltonian_from_V(k, V_matrix, num_G_vectors)`  
  Monta o Hamiltoniano completo \( H = T + V \), com termo cinético + matriz do potencial.

- `calculate_bands_with_V(V_matrix, num_G_vectors, k_points)`  
  Calcula os autovalores (bandas) para cada valor de \( k \).

---

## 📈 Plotagem dos Resultados

- **Gráfico 1**: mostra as bandas de energia para diferentes valores de \( \alpha \) no modelo quase-livre.
- **Gráfico 2**: compara as bandas obtidas com \( V(x) \) (linha cheia) e com α (linha tracejada) para um valor equivalente de acoplamento.

---

## 🧠 Interpretação

- O modelo com α é uma **simplificação**: só considera interações entre vetores de onda vizinhos.
- A matriz \( V_{m,n} \) contém **mais estrutura**, com múltiplas diagonais preenchidas, e leva em conta a **forma espacial do potencial**.
- Comparando os gráficos:
  - Diferenças podem aparecer nos **gaps de energia** e na **curvatura das bandas**.
  - O modelo com \( V(x) \) permite observar **efeitos mais sutis** do potencial sobre os elétrons.
