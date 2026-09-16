# Aproximação Universal de Funções com Redes Neurais em PyTorch

![Python](https://img.shields.io/badge/Python-3873A9?style=for-the-badge&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-ffffff?style=for-the-badge&logo=Matplotlib&logoColor=black)

> Um aproximador interativo de funções por partes (*piecewise functions*) construído em Python e PyTorch. O projeto permite gerar funções sintéticas complexas, configurar a arquitetura da rede, treinar/continuar treinos e visualizar os resultados graficamente.

---

##  Sobre o Projeto

Este projeto demonstra o **Teorema da Aproximação Universal** por meio de um sistema interativo em terminal. Ele permite ao usuário combinar múltiplos tipos de funções em diferentes intervalos de $X$, adicionar ruído estocástico e treinar uma Rede Neural Perceptron Multicamadas (MLP) para aprender a função resultante.

### Principais Destaques

* **Gerenciador de Modelos (.pth)**: Permite salvar checkpoints completos (pesos, estado do otimizador e configurações de dados) para retomar treinamentos de onde pararam.
* **Gerador Dinâmico de Funções**: Suporte a 12 tipos de funções matemáticas combináveis em subintervalos.
* **Arquiteturas Selecionáveis**: Três opções de tamanho de rede (64, 128 e 256 neurônios por camada).
* **Interface via Terminal**: Menu interativo para ajuste de épocas, taxa de aprendizado (*learning rate*), ruído e quantidade de amostras.
* **Visualização Gráfica**: Renderização automatizada usando Matplotlib com tema escuro (*dark mode*).

---

##  Funções Suportadas

O gerador dinâmico permite combinar as seguintes funções em qualquer subintervalo de $X$:

| ID | Função | ID | Função |
|---|---|---|---|
| 1 | **Linear** | 7 | **Tangente** (com *clip*) |
| 2 | **Quadrática** | 8 | **Sigmoide** |
| 3 | **Cúbica** | 9 | **Exponencial** |
| 4 | **Constante** | 10 | **Raiz Quadrada** |
| 5 | **Seno** | 11 | **Valor Absoluto** |
| 6 | **Cosseno** | 12 | **Serrote** (Sawtooth) |

Também estão disponíveis 5 combinações pré-definidas (A a E) no menu do sistema.

---

##  Arquitetura das Redes

Todas as arquiteturas utilizam **4 camadas ocultas** com função de ativação **ReLU** e erro quadrático médio (**MSELoss**) com o otimizador **Adam**:

* **Rede 1 (Leve)**: Entrada $1 \rightarrow [64 \rightarrow 64 \rightarrow 64 \rightarrow 64] \rightarrow$ Saída $1$
* **Rede 2 (Padrão)**: Entrada $1 \rightarrow [128 \rightarrow 128 \rightarrow 128 \rightarrow 128] \rightarrow$ Saída $1$
* **Rede 3 (Pesada)**: Entrada $1 \rightarrow [256 \rightarrow 256 \rightarrow 256 \rightarrow 256] \rightarrow$ Saída $1$

---

##  Estrutura do Repositório

```text
REDE_NEURAL/
├── code/
│   ├── main.py               # Fluxo principal, menu de modelos, loop de treino e plot
│   └── rede.py               # Funções matemáticas, menu de configuração e arquiteturas PyTorch
├── o mais treinado .pth      # Modelo pré-treinado salvo
└── README.md                 # Documentação do repositório
