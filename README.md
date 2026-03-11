# Projeto de Aprendizagem de Máquina - Explicabilidade de IA (xAI)

Este repositório contém a solução para o projeto da disciplina de Aprendizagem de Máquina, focando na explicabilidade de modelos "caixa-preta" e na melhoria da interpretabilidade de valores gerados por métodos agnósticos.

## Objetivo do Experimento (Questão 1.2)

O objetivo central é avaliar se um Large Language Model (LLM) consegue sintetizar uma explicação forte e coerente a partir de um grande número (N) de explicações "pobres" geradas via texto. 

Uma explicação "pobre" é definida como aquela gerada com custo computacional reduzido (menor número de inferências) utilizando métodos como LIME ou SHAP. Utilizaremos o Small Language Model (SLM) Qwen2.5 para a geração textual local.

## Estrutura do Repositório

* `environment/`: Contém o `Dockerfile` e `requirements.txt` para construir o ambiente Python.
* `src/`: Diretório persistido contendo os notebooks e scripts do experimento.
  * `training/`: Contém o notebook `experimento.ipynb` com o pipeline de dados e treinamento.
* `docker-compose.yml`: Orquestração principal do ambiente de desenvolvimento.
* `docker-compose-ollama.yml`: Orquestração auxiliar para execução do SLM em ambientes Linux nativos.

## Como Executar o Projeto

O projeto utiliza contêineres Docker para garantir a reprodutibliidade. Existem duas formas de iniciar o Small Language Model (SLM), dependendo do seu sistema operacional.

### Opção 1: Ambientes Windows/Mac (Docker Desktop)

Esta é a abordagem oficial utilizando o Docker Model Runner.

1. Abra um terminal e inicie o SLM Qwen2.5:
   docker model run ai/qwen2.5

2. Em um segundo terminal, na raiz do projeto, inicie o ambiente Jupyter:
   docker compose up --build

3. Acesse http://127.0.0.1:8888/lab no seu navegador.

### Opção 2: Ambientes Linux Nativos (ex: Arch Linux)

Como o Docker Engine nativo não possui o plugin específico, utilizamos o Ollama via contêiner para expor o modelo na rede interna.

1. Na raiz do projeto, suba a infraestrutura completa:
   docker compose -f docker-compose.yml -f docker-compose-ollama.yml up -d --build

2. Baixe e inicie o modelo Qwen2.5 no contêiner do Ollama:
   docker compose exec qwen_slm ollama run qwen2.5

3. Acesse http://127.0.0.1:8888/lab no seu navegador.

## Progresso Atual

Em desenvolvimento...