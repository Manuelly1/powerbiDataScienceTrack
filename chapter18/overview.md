# Inteligência Artificial e Análise de Séries Temporais com Power BI

## O que são séries temporais?

- São um **conjunto de pontos de dados coletados em intervalos sequenciais ao longo do tempo**. Elas são usadas para *prever futuros pontos de dados* com base em dados históricos;

- Esses conjuntos de dados são frequentemente coletados em intervalos regulares. **Exemplos:** o preço das ações ao final de cada dia de negociação; a temperatura média diária durante um ano; as vendas mensais de uma empresa ou o PIB trimestral de um país;

- A **análise de séries temporais** é uma técnica estatística que lida com dados de séries temporais para *extrair funções úteis e ajudar na previsão de dados futuros*. Essa análise pode levar em conta tendências, sazonalidade e ciclos presentes nos dados;

- Alguns exemplos comuns de utilização de séries temporais incluem a previsão do tempo, análise econômica, engenharia de controle de processos, dentre outros.

---

## Principais Técnicas para Análise de Séries Temporais

- Existem várias técnicas de análise de séries temporais, que vão desde modelos estatísticos clássicos a abordagens mais modernas de Aprendizado de Máquina e Inteligência Artificial. As técnicas mais comuns incluem:

    - **Análise de Tendências:** esta é uma das técnicas mais simples, onde se procura uma tendência persistente ao longo do tempo. Por exemplo, um aumento constante ou uma queda nos dados;

    - **Médias Móveis e Suavização Exponencial:** estas são técnicas para remover o "ruído" de uma série temporal, fazendo a média de pontos de dados de um determinado número de períodos de tempo;

    - **Decomposição:** esta técnica envolve a separação da série temporal em componentes de tendência, sazonalidade e resíduos (o que resta depois de remover a tendência e sazonalidade);

    - **Modelos Autorregressivos (AR):** em um modelo AR, o valor de uma variável em um determinado momento é suposto ser uma função linear dos valores anteriores;

    - **Modelos de Médias Móveis (MA):** em um modelo MA, o valor de uma variável em um determinado momento é suposto ser uma função linear dos erros de previsão dos pontos anteriores;

    - **Modelos ARIMA (Autoregressive Integrated Moving Average):** estes modelos combinam modelos AR e MA e também incluem um termo de "diferenciação" para tornar a série temporal estacionária;

    - **Modelos de Aprendizado de Máquina (Machine Learning):** modelos de aprendizado de máquina como redes neurais, SVMs, florestas aleatórias, gradient boosting, dentre outros; podem ser usados para modelar séries temporais. Especificamente, redes neurais como LSTMs e GRUs são particularmente adequadas para séries temporais por causa de sua capacidade de "lembrar" valores passados;

    - **Modelos de Aprendizado Profundo (Deep Learning):** Redes Neurais Recorrentes (RNNs) e suas variantes como Long Short Term Memory (LSTM) e Gated Recurrent Units (GRUs) são amplamente usadas para modelagem de séries temporais. Mais recentemente, modelos baseados em Transformers estão sendo aplicados à análise de séries temporais.

- A escolha da técnica depende do *problema específico da série temporal, da natureza dos dados, da disponibilidade de recursos computacionais e de outros fatores*. O **Power BI não é uma ferramenta para análise de séries temporais**, mas oferece um recurso simples que pode ser usado para uma análise geral. 

---

## Lab 9 - Engenharia de Produção com Power BI e IA - Prevendo a Produção Industrial ao Longo do Tempo

### O que é Engenharia de Produção?

- É um ramo da engenharia que se *ocupa do projeto, melhoria e instalação de sistemas integrados de pessoas, materiais, informações, equipamentos e energia*. O **objetivo é otimizar o desempenho de uma organização**, considerando fatores como eficiência, eficácia, produtividade, qualidade e sustentabilidade;

- Essa engenharia integra princípios e métodos de engenharia e ciências físicas e sociais, juntamento com princípios e métodos de análise e design de engenharia, para especificar, prever e avaliar os resultados a serem obtidos de tais sistemas.

---

### Visão Geral do Lab 9

