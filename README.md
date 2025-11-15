# Avaliação do spaCy (pt_core_news_sm) para NER em Português

![Python](https://img.shields.io/badge/Python-3.10-blue.svg)
![spaCy](https://img.shields.io/badge/spaCy-v3.8.0-brightgreen.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)

Este repositório contém o código e a análise do artigo **"Avaliação do `pt_core_news_sm` para NER em Português Brasileiro"**. O estudo investiga o desempenho do modelo "pequeno" (`sm`) da biblioteca spaCy para tarefas de Reconhecimento de Entidades Nomeadas (NER) em um conjunto de dados customizado.

## 💡 Principais Conclusões

O objetivo principal era testar a adequação do modelo `pt_core_news_sm` para extração contextual. A análise concluiu que o modelo **não é adequado** para esta tarefa específica.

* **Desempenho Geral Fraco:** O modelo atingiu um F1-score (macro avg) de apenas **0.370**, indicando um baixo equilíbrio entre precisão e revocação.
* **Falha Total em 'PROD':** O modelo foi **incapaz de identificar uma única entidade** da classe "Produto" (PROD), zerando todas as métricas para esta categoria.
* **Baixo Desempenho em 'ORG':** A performance na classe "Organização" (ORG) foi péssima, com um Recall de apenas **0.125** (encontrou apenas 1 de 8 entidades).
* **Conclusão:** Modelos "pequenos" (`sm`) são rápidos, mas carecem da capacidade contextual necessária para domínios específicos. Para aplicações robustas, é recomendado o uso de modelos maiores (como `pt_core_news_lg` ou Transformers como BERTimbau).

---

## 🚀 Como Executar o Projeto

Você pode replicar esta análise seguindo os passos abaixo.

### 1. Pré-requisitos

* Python 3.8+
* Git

### 2. Instalação

1.  Clone este repositório:
    ```bash
    git clone [https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git](https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git)
    cd SEU-REPOSITORIO
    ```

2.  Crie e ative um ambiente virtual (recomendado):
    ```bash
    python -m venv venv
    source venv/bin/activate  # No Windows: venv\Scripts\activate
    ```

3.  Instale as dependências:
    ```bash
    pip install -r requirements.txt
    ```

4.  Baixe o modelo spaCy utilizado no estudo:
    ```bash
    python -m spacy download pt_core_news_sm
    ```

### 3. Execução

1.  Inicie o servidor Jupyter:
    ```bash
    jupyter notebook
    ```
2.  No seu navegador, abra o arquivo `Extração contextual.ipynb`.
3.  Você pode executar todas as células ("Run All") para ver os resultados sendo gerados em tempo real.

---

## 📦 Conteúdo do Repositório

* **`Extração contextual.ipynb`**: O Jupyter Notebook contendo todo o processo de carregamento, execução do modelo, comparação e geração de métricas.
* **`Basefictícia.csv`**: O conjunto de dados (gabarito) usado para avaliar o modelo.
* **`requirements.txt`**: A lista de bibliotecas Python necessárias para rodar o projeto.

## 📊 Resultados Detalhados

O Relatório de Classificação final, que fundamenta a conclusão do estudo, foi o seguinte:

````

```
          precision    recall  f1-score   support

     LOC      0.500     1.000     0.667         8
    MISC      0.000     0.000     0.000         0
     ORG      0.333     0.125     0.182         8
     PER      1.000     1.000     1.000         8
    PROD      0.000     0.000     0.000         8

accuracy                          0.531        32
```

macro avg      0.367     0.425     0.370        32
weighted avg      0.458     0.531     0.462        32

```

## 📚 Trabalhos Futuros

* Comparar o desempenho com modelos maiores (`md` e `lg`) da spaCy.
* Realizar *fine-tuning* (ajuste fino) em modelos Transformers (ex: BERTimbau) com dados de domínio específico.
* Validar os modelos em bases de dados reais (notícias, documentos jurídicos) para testar a generalização.

## 📄 Licença

Distribuído sob a licença MIT. Veja `LICENSE.txt` para mais informações.

### Arquivo `requirements.txt`

Para completar o repositório, crie um arquivo chamado `requirements.txt` e coloque o seguinte conteúdo nele:

```
pandas
spacy==3.8.0
scikit-learn
matplotlib
notebook
```
