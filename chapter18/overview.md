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

- O professor inicia o laboratório destacando a importância do **tempo** na análise de dados. Em seguida, aborda um dos ramos mais relevantes e complexos da Ciência de Dados: a **análise de séries temporais**, que envolve um conjunto de técnicas, procedimentos, teorias e regras que precisam ser devidamente validadas para possibilitar a correta análise de um fenômeno ao longo do tempo;

- Nesse contexto, o laboratório propõe a aplicação desses conceitos utilizando um cenário de **engenharia de produção no Power BI**, explorando um recurso de **Inteligência Artificial** disponibilizado pela ferramenta. O objetivo é analisar e compreender o comportamento da **produção industrial ao longo do tempo**, evidenciando padrões, tendências e variações temporais a partir dos dados.

---

### Compreendendo o que é uma Série Temporal

- Antes de iniciar o processamento dos dados, o professor orientou a realização de uma **análise exploratória** do conjunto de dados no Excel. A base utilizada contém os seguintes campos: `Período`, `Turno`, `Range Idade Funcionários` e `Total Unidades Produzidas`, representando dados de produção industrial de uma empresa. Nessa planilha, o fator tempo está presente na coluna `Período`, registrada no formato **dd/mm/aaaa**, enquanto o fenômeno observado ao longo do tempo é o `Total Unidades Produzidas`. Os demais campos atuam como variáveis complementares que ajudam a contextualizar o comportamento da produção. Assim, a série temporal em análise é o `Total Unidades Produzidas`, entendido como um evento ou fenômeno que ocorre e varia ao longo do tempo;

- Observou-se que o formato de data carregado no Excel estava como **dd/mm/aaaa**. Além disso, os dados encontram-se segmentados por **turno** (manhã e tarde) e por **faixa etária dos funcionários**. Para cada combinação desses fatores, há um valor correspondente ao total de unidades produzidas, o que caracteriza uma estrutura de dados mais complexa, e não uma série temporal simples e direta;

- Diante desse cenário, o professor levantou o seguinte questionamento: *“Qual é o nosso trabalho aqui?”*. A resposta envolve, primeiramente, a análise dos dados com o objetivo de extrair **insights relevantes** sobre o comportamento da produção ao longo do tempo. Em seguida, o próximo passo consiste na **construção de um modelo preditivo**, utilizando recursos disponíveis no Power BI, para apoiar a tomada de decisão com base em previsões futuras.

---

### Analisando a Produção Industrial ao Longo do Tempo

- Após o carregamento dos dados no Power BI, foi possível observar que a ferramenta identificou corretamente todos os campos, incluindo o `Período`, para o qual foi criada automaticamente a hierarquia de datas. Ao acessar o **Power Query** para verificar os tipos de dados, constatou-se que a coluna `Período` estava marcada com o ícone de calendário, indicando que foi reconhecida como do tipo **data**. As colunas `Turno` e `Range Idade Funcionários` foram identificadas como **texto**, enquanto `Total Unidades Produzidas` foi reconhecida como um campo **numérico inteiro**;

- O primeiro visual criado foi um **gráfico de barras**, no qual se utilizou o campo `Ano` no eixo X e `Total Unidades Produzidas` no eixo Y, configurado para exibir a **média**. A partir desse gráfico, foi possível identificar que o ano de **2023** apresentou o menor valor médio de unidades produzidas, enquanto **2020** foi o ano com o maior volume de produção. Em seguida, o professor destacou que, para análises de **séries temporais**, o gráfico mais adequado é o **gráfico de linhas**, pois ele facilita a visualização de tendências e variações ao longo do tempo. Por esse motivo, o gráfico de barras foi substituído por um gráfico de linhas, tornando a interpretação do comportamento da produção ao longo dos anos mais clara e intuitiva.

---

### Navegando pela Hierarquia de Datas no Power BI – Mudança de Nível

- Ao selecionar o gráfico criado anteriormente, observa-se, na parte superior do visual, a presença de ícones que permitem a navegação pela hierarquia de datas. Todavia, o professor destacou um ponto fundamental: para que essa navegação funcione corretamente, é necessário que a **hierarquia completa de datas** esteja inserida no gráfico. Inicialmente, apenas o campo **Ano** havia sido utilizado. Para corrigir isso, o campo **Ano** foi removido e a hierarquia de datas completa foi adicionada. Após essa alteração, os ícones de navegação passaram a ser exibidos corretamente, possibilitando ações como **fazer drill up**, **habilitar o drill down** e outras opções relacionadas à exploração dos níveis da hierarquia;

- O primeiro ícone, representado por uma seta apontando para cima, corresponde à ação **fazer drill up**, que permite *subir na hierarquia*. Para compreender esse conceito, é importante observar a estrutura hierárquica: o nível mais alto é o **Ano**, enquanto o nível mais baixo é o **Dia**. Assim, ao clicar nesse ícone, o gráfico passa a exibir níveis mais agregados, ou seja, níveis superiores àquele que está sendo visualizado no momento;

- Para descer na hierarquia, utiliza-se o **drill down**, representado por ícones com setas apontando para baixo. Nesse caso, existem diferentes opções de navegação:  

    - o ícone com **uma seta para baixo** permite descer **nível por nível** na hierarquia;  
  
    - o ícone com **duas setas para baixo** possibilita descer diretamente para um nível inferior específico;  
  
    - o ícone da **seta bifurcada** tem a função de **expandir um nível abaixo na hierarquia**, exibindo simultaneamente os valores do nível atual e do nível imediatamente inferior. Nesse caso, ocorre uma visualização combinada, envolvendo o nível atual e o próximo, diferentemente da simples mudança de nível, que apresenta apenas a agregação de um único nível por vez.

- Ao utilizar o ícone com **duas setas para baixo** ou a **seta bifurcada**, obtêm-se visões distintas dos dados. Por esse motivo, o professor ressaltou a importância de atenção na escolha da ação, uma vez que cada opção gera um tipo diferente de análise e interpretação dos dados;

- Por fim, o professor mencionou que a navegação pela hierarquia de datas também pode ser realizada por meio da aba **Dados/Analisar**, onde estão disponíveis as opções de **fazer drill up**, **fazer drill down** e outras funcionalidades voltadas à exploração e detalhamento dos dados.

---

### Calculando as Estatísticas Média e Média Móvel no Power BI
