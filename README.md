# 👻 O Diagnóstico Fantasma: Investigação de Vieses em SRAG com IA

> **Status:** Concluído ✅ | **Ano:** 2019-2025 | **Algoritmos:** ID3 & Random Forest (From Scratch)

## 📖 Sobre o Projeto

A vigilância epidemiológica da Síndrome Respiratória Aguda Grave (SRAG) enfrenta um desafio crítico: uma grande parcela dos casos é encerrada como **"SRAG Não Especificada"**, sem identificação de vírus (como COVID-19 ou Influenza).

Este projeto investiga a hipótese do **"Diagnóstico Fantasma"**: a premissa de que exacerbações graves de **Asma** estão sendo classificadas incorretamente como SRAG viral devido à sobreposição de sintomas (dispneia e dessaturação), gerando ruído nos dados de saúde pública.

O objetivo foi construir um modelo de Machine Learning capaz de diferenciar casos "Virais Confirmados" de casos "Fantasmas" (Não Especificados) usando apenas dados clínicos de admissão.

---

## 🛠️ Metodologia e Diferenciais

Diferente de projetos tradicionais que utilizam apenas bibliotecas prontas (como *scikit-learn*), este projeto focou na **construção manual dos algoritmos**, seguindo a lógica matemática do livro *"Data Science from Scratch"* (Joel Grus).

### Tecnologias e Técnicas:
- **Linguagem:** Python 3.
- **Bibliotecas:** Pandas, NumPy (Manipulação de dados), Matplotlib/Seaborn (Visualização), Gdown (Coleta de dados).
- **Algoritmos Implementados "Do Zero":**
    - **Árvore de Decisão ID3:** Cálculo manual de Entropia de Shannon e Ganho de Informação.
    - **Random Forest (Floresta Aleatória):** Implementação de *Ensemble* com *Bootstrap Aggregation* e votação majoritária.
    - **Naive Bayes:** Implementação probabilística baseada em contagem de tokens (sintomas).
- **Engenharia de Dados:**
    - Tratamento de nulos com imputação negativa.
    - Balanceamento de classes (*Undersampling*).
    - Categorização de variáveis contínuas (Idade, Tempo de Internação).

---

## 📊 A Base de Dados

Os dados foram obtidos do **SIVEP-Gripe (DataSUS)**, compreendendo o período de **2019 a 2025**.

- **Total de Registros Brutos:** ~4.4 milhões.
- **Variáveis Chave:**
  - `NU_IDADE_N` (Normalizada para Faixa Etária)
  - `FEBRE`, `TOSSE`, `DISPNEIA`, `SATURACAO`
  - `RAIOX_RES` (Resultado do Raio-X de Tórax)
  - `ASMA` (Fator de risco/Comorbidade)

---

## 🚀 Resultados Principais

O estudo comparou diferentes abordagens para "caçar" o diagnóstico fantasma.

| Modelo | Acurácia Global | Recall (Sensibilidade) do Fantasma | Interpretação |
| :--- | :---: | :---: | :--- |
| **Árvore ID3 (Simples)** | ~65% | 0.22 | Modelo tendencioso, falhou em detectar o padrão. |
| **Random Forest (Enriquecida)** | **~60%** | **0.54** | **Sucesso.** O modelo aprendeu a identificar mais da metade dos casos ocultos. |

### Conclusão Científica
A "baixa" acurácia global (60%) não é um erro, mas uma descoberta: ela prova estatisticamente a **sobreposição fenotípica**. Os casos de "SRAG Não Especificada" são clinicamente quase idênticos aos virais.
No entanto, a Inteligência Artificial conseguiu isolar um padrão claro: **Pacientes idosos, sem febre, mas com dispneia e Raio-X sem infiltrado intersticial, têm alta probabilidade de serem casos de "Diagnóstico Fantasma" (Agudização de Asma/DPOC).**

---

## 📂 Estrutura do Repositório

```bash
├── data/                  # (Opcional) Amostras dos dados CSV
├── notebooks/             # Jupyter Notebooks com o código completo
│   └── diagnostico_fantasma.ipynb
├── images/                # Gráficos gerados (Matriz de confusão, Árvores)
├── README.md              # Este arquivo
└── requirements.txt       # Dependências (pandas, numpy, etc.)
```

---

## 💻 Como Executar
Este projeto foi desenvolvido para rodar no Google Colab.

Clone o repositório:

Bash
```
git clone [https://github.com/](https://github.com/)[SEU_USUARIO]/[NOME_DO_REPO].git
Abra o Notebook: Carregue o arquivo .ipynb no Google Colab.
```

Carregamento dos Dados: O notebook está configurado para baixar os dados brutos automaticamente via gdown (links públicos do Drive) ou ler diretamente do GitHub, dependendo da versão. Certifique-se de executar a célula de "Setup/Carga de Dados" no início.

## ✒️ Autores
Gabriel dos Santos Mota Rodrigues - Estudante de Ciência de Dados / Pesquisador
João Victor Pereira Nogueira - Estudante de Ciência de Dados / Pesquisador

Este projeto foi desenvolvido como parte da disciplina Introdução a Ciência de Dados, demonstrando a aplicação prática de algoritmos de Machine Learning sem o uso de caixas-pretas.
