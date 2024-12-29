# AI-ReviewLens-Avaliando-Sentimentos-com-NLP
# README

## Projeto: Classificação de Sentimentos no Contexto do Processamento de Linguagem Natural: Uma Abordagem Integrativa

### **Descrição Geral**
Este projeto utiliza técnicas avançadas de **Processamento de Linguagem Natural (PLN)** para realizar a classificação de sentimentos em avaliações de produtos, com foco em três categorias: **positivo**, **neutro** e **negativo**. Dois códigos principais foram desenvolvidos: um focado no uso de **in-context learning** com modelos da OpenAI (como GPT), e outro implementando diferentes modelos de aprendizado de máquina, como **SVM com Bag-of-Words**, **SVM com embeddings** e **BERT**.

---

## **Código 1: Bônus (bônus.py)**
### **Descrição**
Este código utiliza o modelo **GPT (gpt-3.5-turbo)** para classificar sentimentos em 500 avaliações de produtos, usando **in-context learning**.

### **Etapas Principais**
1. **Carregamento do Dataset**:
   - Avaliações de produtos com colunas "Score" (nota) e "Text" (texto da avaliação).
   - Seleção de 500 amostras aleatórias.

2. **Conversão de "Score" para Sentimento**:
   - **Positivo**: `Score >= 4`
   - **Neutro**: `Score == 3`
   - **Negativo**: `Score < 3`

3. **Uso de Exemplos**:
   - Exemplos de classificações são fornecidos ao modelo GPT para facilitar a interpretação do modelo.

4. **Classificação com GPT**:
   - Um prompt é criado dinamicamente para cada avaliação e enviado para o endpoint da OpenAI.

5. **Avaliação do Modelo**:
   - Métricas como **acurácia**, **precisão**, **revocação** e **F1-Score** são calculadas.
   - Uma matriz de confusão é gerada para visualizar os resultados.

---

## **Código 2: Projeto Final de PLN (projeto_final_de_processamento_de_linguagem_natural.py)**
### **Descrição**
Este código implementa três abordagens de aprendizado de máquina para classificar sentimentos em avaliações de produtos, utilizando um pipeline completo de pré-processamento, treinamento e avaliação.

### **Etapas Principais**

#### **1. Carregamento e Pré-Processamento**
- **Remoção de Nulos**:
  - Colunas "Score" e "Text" são selecionadas e valores nulos são descartados.
- **Conversão de Sentimento**:
  - Mesma lógica de conversão de "Score" para sentimento do código anterior.
- **Limpeza de Texto**:
  - Remoção de números, pontuações e stopwords, além de tokenização e normalização para minúsculas.
- **Divisão de Dados**:
  - Os dados são divididos em treino, validação e teste.

#### **2. Modelos Implementados**
##### **Modelo 1: SVM com Bag-of-Words**
- Os textos são representados por vetores esparsos usando **CountVectorizer**.
- Um modelo **SVM** é treinado com esses vetores para classificar sentimentos.

##### **Modelo 2: SVM com Embeddings**
- Utiliza embeddings pré-treinados (Word2Vec em português).
- Cada texto é convertido para um vetor denso pela média dos vetores das palavras conhecidas.
- Um modelo **SVM** é treinado com essas representações densas.

##### **Modelo 3: BERT**
- Textos são tokenizados usando **BertTokenizerFast**.
- Um modelo **BERT** pré-treinado (“bert-base-uncased”) é ajustado para classificar os textos em três categorias.
- Treinamento ocorre com acumulação de gradientes para otimização de memória.

#### **3. Avaliação de Desempenho**
- Cada modelo é avaliado com as seguintes métricas:
  - **Precisão**, **Revocação**, **F1-Score** e **Acurácia**.
  - Geração de matriz de confusão para análise de erros.

---

## **Comparação dos Dois Códigos**
### **Semelhanças**
- Ambos utilizam o mesmo dataset e conversão de sentimentos.
- Métricas de avaliação são consistentes.

### **Diferenças**
- **Código 1**:
  - Utiliza o GPT para classificação direta com base em exemplos fornecidos.
  - Focado em **in-context learning** sem treinamento direto.
- **Código 2**:
  - Implementa técnicas tradicionais de aprendizado de máquina (SVM) e modelos modernos (BERT).
  - Inclui pipeline de treinamento supervisionado e embeddings.

---

## **Como Executar os Códigos**
### **Pré-Requisitos**
1. **Bibliotecas Python Necessárias**:
   - pandas, numpy, sklearn, matplotlib, seaborn, nltk, gensim, transformers, torch
2. **Chave da API da OpenAI** (para o Código 1):
   - Configurar sua chave como `openai.api_key`.
3. **Dataset**:
   - Certifique-se de que o arquivo `Reviews.csv.zip` esteja no caminho especificado.
4. **Embeddings Pré-Treinados** (para o Código 2):
   - Arquivo `w2v-ptbr-skips50.zip` no caminho correto.

### **Passos**
1. Configure os caminhos para o dataset e embeddings.
2. Execute cada célula do script no Google Colab ou ambiente local.

---

## **Resultados Esperados**
- **Código 1**: Classificação rápida de 500 amostras com acurácia estimada.
- **Código 2**: Comparação detalhada entre os modelos (SVM + BoW, SVM + Embeddings, e BERT) com métricas e matrizes de confusão.

---

## **Possíveis Extensões**
1. Testar outros modelos da OpenAI, como `gpt-4`, no Código 1.
2. Incorporar embeddings contextualizados, como **BERT embeddings**, ao Código 2.
3. Melhorar o balanceamento de classes para desempenho mais uniforme.

---

## **Link para Download da base de dados Amazon Product Reviews Dataset**
A base de dados está disponível publicamente no Kaggle: [Amazon Product Reviews Dataset](https://www.kaggle.com/datasets/arhamrumi/amazon-product-reviews/data)

## **Link para Download da base de dados de Embedding**
A base [skips50](http://nilc.icmc.usp.br/embeddings) é um modelo de embedding de palavras em português, gerado pelo método skip-gram do Word2Vec. Esse modelo foi desenvolvido pelo Núcleo Interinstitucional de Linguística Computacional (NILC), da Universidade de São Paulo (USP), e faz parte do repositório de Word Embeddings específicos para a língua portuguesa.

Word embeddings como o skips50 são amplamente utilizados em tarefas de Processamento de Linguagem Natural (PLN) para representar palavras como vetores densos, capturando relações semânticas e sintáticas entre elas.
---

Se houver dúvidas ou problemas, entre em contato com o desenvolvedor.


