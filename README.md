# cqv-hac-mopso

Este repositório contém duas abordagens práticas para a implementação de Classificadores Quânticos Variacionais (CQV) utilizando o dataset Iris. O projeto está dividido em um laboratório didático de exploração de hiperparâmetros e uma implementação avançada baseada em otimização estrutural de ponta para dispositivos NISQ.

## Estrutura do Projeto

### 1. Laboratório Aberto (CQV Básico)
O módulo `01_Laboratorio_CQV_Basico.ipynb` é focado no entendimento das mecânicas fundamentais do CQV. O código foi desenhado para permitir a manipulação direta de parâmetros clássicos e quânticos, observando seus impactos na convergência e no fenômeno de *barren plateaus*:
*   **Profundidade do Circuito (`num_layers`):** Controle prático da capacidade expressiva do modelo quântico.
*   **Taxa de Aprendizagem e Lotes (`stepsize` e `batch_size`):** Avaliação de estabilidade na otimização e controle da velocidade de convergência.
*   **Early Stopping (`patience`):** Aplicação de critério de parada dinâmica para evitar *overfitting* e economizar recursos de processamento.
*   Na configuração padrão de 2 qubits e 6 camadas, este laboratório alcança uma acurácia de teste de 100% nas 4 características principais do dataset.

### 2. Implementação Avançada (CQV Adaptativo)
O módulo `02_CQV_Adaptativo.ipynb` executa os algoritmos complexos propostos no artigo *Adaptive quantum ansatz circuit design and optimization*. O pipeline metodológico engloba:
*   **Preparação e Particionamento:** Uso de Análise de Componentes Principais (PCA) para reduzir o dataset a 4 características, que são duplicadas para simular duas partições lógicas mapeadas em 8 qubits.
*   **Busca de Topologia (HAC-SA):** Utiliza *Simulated Annealing* (Recozimento Simulado) para procurar a melhor fusão adaptativa entre os qubits das partições.
*   **Otimização Multi-Objetivo (MOPSO):** Aplica o Enxame de Partículas para eleger a configuração ideal de portas lógicas (Ex: CRX, CRY, RY) na Fronteira de Pareto. A aptidão de cada configuração é avaliada com base na minimização da profundidade do circuito, maximização da expressividade (calculada via Divergência KL) e maximização do emaranhamento (medida de Meyer-Wallach).
*   **Treinamento Híbrido:** Avaliação do custo através de *Binary Cross-Entropy* e treinamento de camadas paralelas antes da junção global interativa.

## Tecnologias Utilizadas
*   [PennyLane](https://pennylane.ai/) - Framework central para a programação quântica diferencial.
*   [Scikit-Learn](https://scikit-learn.org/) - Redução de dimensionalidade e padronização (PCA e StandardScaler).
*   [NumPy](https://numpy.org/) e [Matplotlib](https://matplotlib.org/) - Processamento de tensores de matriz de densidade e renderização gráfica da Superfície de Decisão Quântica.
*   [SciPy](https://scipy.org/) - Cálculo estatístico de entropia para a métrica de expressividade.

## Como Executar

1. Clone o repositório:
   ```bash
   git clone [https://github.com/laiimour/cqv-hac-mopso.git](https://github.com/laiimour/cqv-hac-mopso.git)

## Referências e Créditos
  **Artigo Base:** CHENG, Xueyun et al. Adaptive quantum ansatz circuit design and optimization. Quantum Machine Intelligence, v. 8, n. 86, 2026. DOI: 10.1007/s42484-026-00428-y.
  
  **Código base:** Inspirado e adaptado do tutorial oficial do PennyLane [Variational Quantum Classifier - PennyLane Demos](https://pennylane.ai/demos/tutorial_variational_classifier/).
