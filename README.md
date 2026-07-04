# Desafio técnico retrieval de livros pré RAG

Este projeto foi desenvolvido como parte de um desafio técnico do programa de bolsas AI/R da Compass UOL, cujo objetivo era construir um pipeline de Retrieval-Augmented Generation (RAG) focado exclusivamente na etapa de recuperação de informação, sem o uso de um Large Language Model (LLM).

O desafio consistiu em desenvolver um sistema capaz de processar uma coleção de livros em formato HTML, transformando seu conteúdo em representações vetoriais (embeddings) para realizar buscas semânticas eficientes. Ao final, o sistema deve recuperar os trechos mais relevantes para uma determinada consulta, servindo como a base de um pipeline RAG.

Este projeto implementa todas as etapas propostas, desde a extração e processamento dos documentos até a recuperação dos Top-10 trechos semanticamente mais relevantes, demonstrando como técnicas de embeddings e busca vetorial podem ser utilizadas para construir sistemas inteligentes de recuperação de informação.

---

## 🎯 Objetivo

O sistema realiza todas as etapas necessárias para uma aplicação de recuperação semântica:

- Leitura de livros em formato HTML;
- Extração e limpeza do texto;
- Segmentação do conteúdo em chunks;
- Criação de metadados para cada trecho;
- Geração de embeddings utilizando Sentence Transformers;
- Busca semântica baseada em similaridade de cosseno;
- Retorno dos **Top-10 trechos mais relevantes** para uma consulta.

Neste projeto **não há geração de respostas por IA**, apenas recuperação de contexto.

---

## Pipeline

O projeto é dividido nas seguintes etapas:

### 1. Coleta dos documentos

- Leitura dos arquivos HTML
- Extração do conteúdo textual
- Limpeza do HTML
- Consolidação do texto de cada livro

### 2. Análise dos documentos

São realizadas análises exploratórias como:

- tamanho dos livros;
- quantidade de caracteres;
- distribuição do conteúdo.

### 3. Chunking

Cada livro é dividido em pequenos trechos para facilitar a recuperação semântica.

Cada chunk possui:

- texto;
- título do livro;
- identificador único;
- embedding correspondente.

### 4. Geração dos Embeddings

Cada chunk é convertido para um vetor utilizando o modelo **Sentence Transformers**.

Esses embeddings são armazenados para reutilização futura.

### 5. Busca Semântica

Quando o usuário realiza uma pergunta:

1. A consulta é transformada em embedding;
2. É calculada a similaridade entre a consulta e todos os chunks;
3. Os resultados são ordenados;
4. São retornados os **10 trechos mais relevantes**.

---

## Tecnologias utilizadas

- Python
- BeautifulSoup
- Sentence Transformers
- Transformers
- NumPy
- Scikit-Learn
- Pickle
- Jupyter Notebook

---

##  Dataset

O projeto utiliza aproximadamente **15 livros de domínio público** em formato HTML, incluindo obras como:

- Pride and Prejudice
- Frankenstein
- Romeo and Juliet
- Alice's Adventures in Wonderland
- Sherlock Holmes
- The Great Gatsby
- The Picture of Dorian Gray
- Wuthering Heights
- The Blue Castle
- The Importance of Being Earnest

---

## 📊 Resultados

O sistema consegue recuperar trechos relevantes mesmo quando a consulta não possui correspondência exata de palavras, utilizando similaridade semântica entre embeddings.

A recuperação funciona tanto para perguntas objetivas quanto para consultas mais abstratas relacionadas aos livros.


Projeto desenvolvido como parte do desafio de construção de um pipeline **Pré-RAG**, com foco em recuperação semântica de documentos.
