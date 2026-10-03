# cqv-hac-mopso

Implementação prática de um Classificador Quântico Variacional (CQV) utilizando aprendizado de máquina quântico (QML) com o objetivo de otimizar a estrutura de circuitos quânticos parametrizados (Ansatz) para dispositivos NISQ.

Além dos templates fixos tradicionais, o código implementa duas etapas de otimização estrutural baseadas no artigo *Adaptive quantum ansatz circuit design and optimization*:

*   **Busca de Topologia (HAC-SA):** Utiliza *Simulated Annealing* para encontrar a melhor combinação de emaranhamento entre os qubits.
*   **Otimização de Portas (MOPSO):** Aplica Enxame de Partículas Multi-Objetivo para selecionar as portas lógicas ideais, equilibrando a expressividade do circuito e mantendo uma baixa profundidade.
*   **Camada de Interferência:** Solução implementada para evitar o colapso de gradientes (*barren plateaus*), garantindo a convergência do modelo.
*   **Visualização PCA:** Geração de um gráfico bidimensional através de Análise de Componentes Principais para visualizar a fronteira de decisão quântica.

## Tecnologias Utilizadas

*   [PennyLane](https://pennylane.ai/) - Framework principal para a programação quântica diferencial.
*   [Scikit-Learn](https://scikit-learn.org/) - Para o dataset Iris e redução de dimensionalidade (PCA).
*   [NumPy](https://numpy.org/) e [Matplotlib](https://matplotlib.org/) - Para manipulação de tensores e geração de gráficos.

## Como Executar

1. Clone o repositório:
   ```bash
   git clone [https://github.com/laiimour/cqv-hac-mopso.git](https://github.com/laiimour/cqv-hac-mopso.git)

## Referências e Créditos
  **Artigo Base:** CHENG, Xueyun et al. Adaptive quantum ansatz circuit design and optimization. Quantum Machine Intelligence, v. 8, n. 86, 2026. DOI: 10.1007/s42484-026-00428-y.
  **Código base:** Inspirado e adaptado do tutorial oficial do PennyLane [Variational Quantum Classifier - PennyLane Demos](https://pennylane.ai/demos/tutorial_variational_classifier/).
