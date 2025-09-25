# Projeto: Score de Crédito com IA (Python)

> **Direto ao ponto:** classificar clientes em **Ruim**, **Ok** ou **Bom** usando aprendizado de máquina (Random Forest e KNN) a partir de um CSV de clientes. Depois, prever o score para **novos_clientes.csv**.

## 📌 Visão Geral
Este projeto treina um modelo de classificação para **score de crédito** de clientes de um banco, com base em atributos como **profissão**, **mix de crédito** e **comportamento de pagamento**.  
O fluxo está implementado no notebook **`inicial.ipynb`**.

### Pipeline (resumo)
1. **Importação dos dados**: `clientes.csv`
2. **Preparação**: *Label Encoding* para variáveis categóricas (`profissao`, `mix_credito`, `comportamento_pagamento`)
3. **Split treino/teste**: `train_test_split` (30% teste)
4. **Treino de modelos**: `RandomForestClassifier` e `KNeighborsClassifier`
5. **Avaliação**: Acurácia no conjunto de teste
6. **Predição em novos dados**: `novos_clientes.csv` → `model_forest.predict(...)`

## 🧱 Estrutura Esperada
```
.
├── inicial.ipynb          # Notebook principal (pipeline do projeto)
├── clientes.csv           # Base histórica rotulada (com 'score_credito')
├── novos_clientes.csv     # Base sem rótulo para previsão
└── README.md              # Este arquivo
```

## 🗂️ Esquema dos Dados

### `clientes.csv` (treino)
- `id_cliente` *(opcional, descartado)*
- `profissao` *(categórica)*
- `mix_credito` *(categórica)*
- `comportamento_pagamento` *(categórica)*
- **`score_credito`** *(alvo: "Ruim" | "Ok" | "Bom")*

### `novos_clientes.csv` (predição)
- Mesmo esquema **sem** a coluna `score_credito`.

> Observação: As variáveis categóricas são codificadas com **LabelEncoder**. Para manter consistência, o notebook já aplica **o mesmo codificador** aprendido no treino.

## 🧪 Requisitos
- Python 3.10+
- Jupyter Notebook / JupyterLab
- Pacotes:
  - `pandas`
  - `scikit-learn`

Instalação rápida (recomendado usar ambiente virtual):
```bash
python -m venv .venv
source .venv/bin/activate  # Linux/Mac
# .venv\Scripts\activate # Windows PowerShell
pip install pandas scikit-learn jupyter
```

## ▶️ Como Rodar
1. Coloque `clientes.csv` e `novos_clientes.csv` na raiz do projeto.
2. Abra o notebook:
   ```bash
   jupyter notebook inicial.ipynb
   ```
3. Execute as células em ordem. Ao final você verá:
   - **Acurácia** dos modelos (Random Forest e KNN)
   - **Predições** do melhor modelo (Random Forest) para `novos_clientes.csv`

## 📈 Métrica
- **Acurácia** em `x_teste`/`y_teste` usando `accuracy_score`.

> **Por quê Random Forest?** No notebook, a acurácia do Random Forest tende a superar o KNN no teste. A escolha é **empírica** (o melhor no seu dado).

## 🧩 Decisões de Modelagem
- **Codificação**: `LabelEncoder` para transformar categorias em números.
- **Modelos**: comparação simples entre **RandomForestClassifier** e **KNeighborsClassifier**.
- **Split**: 70% treino, 30% teste (default do `train_test_split` no notebook).

## 🧯 Solução de Problemas Comuns
- **Erro ao ler CSV**: confirme nomes/colunas e separador (`,` vs `;`).  
- **Mismatch de categorias**: garanta que `novos_clientes.csv` use **categorias existentes** (ou trate categorias novas antes de prever).
- **ImportError**: instale os pacotes indicados em *Requisitos*.

---

**Resumo nerd e rápido:** o notebook treina **RF vs KNN**, mede acurácia e usa **RF** para prever score em `novos_clientes.csv`. Sem rodeio.
