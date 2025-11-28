# Unidade 11: Estatística Fundamental para Data Science

- **O que é e qual a finalidade da estatística?** É um ramo da matemática que lida com a coleta, análise, interpretação e organização de dados. Ela busca extrair informações significativas de conjuntos de dados, permitindo a tomada de decisões e a elaboração de previsões em situações de incerteza. Ela pode ser dividida em 2 áreas principais: a **Estatística Descritiva** e a **Estatística Inferencial**;

- A **Estatística Descritiva** foca na organização e apresentação dos dados de maneira eficiente. As técnicas incluem:

    - **Tabelas e gráficos:** Tabelas de frequência, histogramas, gráficos de barras, gráficos de setores,  gráficos  de  dispersão  e  gráficos  de  linha  são  algumas  das  ferramentas utilizadas para apresentar os dados de forma visual e fácil de interpretar;
    
    - **Medidas de tendência central:** Média, mediana e moda são usadas para descrever o "centro" dos dados, fornecendo uma ideia geral do valor central em torno do qual os dados estão distribuídos;
    
    - **Medidas  de  dispersão:**  Variância,  desvio  padrão  e  amplitude  são  usados  para quantificar a dispersão ou variabilidade dos dados, fornecendo informações sobre a consistência e a diferença entre os valores observados;
    
    - **Medidas  de  posição:**  Quartis,  percentis  e  outros  valores  que  indicam  a  posição relativa de um valor específico dentro do conjunto de dados.

- Já a **Estatística Inferencial** utiliza técnicas e métodos para fazer generalizações e previsões a partir de dados amostrais, permitindo inferências sobre uma população maior. Algumas  das principais  técnicas incluem:

    - **Estimação:** Estimação pontual e intervalar são usadas para estimar parâmetros populacionais, como a média ou a proporção, com base em dados amostrais e um grau de incerteza associado;
    
    - **Testes de hipóteses:** Testes de hipóteses são usados para testar afirmações ou suposições sobre parâmetros populacionais, como comparar médias entre dois grupos ou verificar se uma proporção é significativamente diferente de um valor esperado;
    
    - **Análise de regressão:** A análise de regressão é usada para modelar a relação entre uma variável dependente e uma ou mais variáveis independentes, permitindo prever valores futuros ou identificar variáveis que impactam o resultado de interesse;
    
    - **Análise de variância (ANOVA):** A ANOVA é uma técnica usada para comparar as médias de dois ou mais grupos, verificando se há diferenças significativas entre eles;
    
    - **Modelos probabilísticos e análise de séries temporais:** São usados para analisar e modelar eventos aleatórios e a evolução de variáveis ao longo do tempo.

- É válido lembrar que, embora a estatística seja um componente fundamental em Data Science, a Ciência de Dados vai muito além das técnicas estatísticas, incluindo também aspectos como limpeza de dados, engenharia de recursos, implementação de algoritmos de aprendizado de máquina e comunicação dos resultados obtidos.

--- 

## Big Data Analytics

- É o processo de examinar, analisar e extrair informações valiosas de grandes conjuntos de dados, conhecidos como *Big Data*. Esses dados são caracterizados por seu grande volume, variedade e velocidade, o que os torna complexos e desafiadores de serem processados e analisados por métodos tradicionais;

- *Big Data Analytics* envolve o uso de técnicas avançadas de análise de dados, como aprendizado de máquina, mineração de dados, processamento de linguagem natural (PLN) e análise de texto, bem como ferramentas e tecnologias especializadas para lidar com a escala e complexidade dos dados;

- O **objetivo** é identificar padrões, tendências e correlações ocultas nos dados, permitindo que as empresas tomem decisões mais informadas, melhorem a eficiência operacional, identifiquem novas oportunidades de negócio e obtenham uma vantagem competitiva;

- **Algumas aplicações do Big Data Analytics incluem:**

    - **Análise preditiva:** Usando técnicas de aprendizado de máquina e análise estatística para prever eventos futuros, como demanda do cliente, falhas de equipamentos ou resultados eleitorais;
    
    - **Análise de sentimentos:** Analisando o conteúdo de redes sociais, avaliações e comentários dos clientes para entender o sentimento do público em relação a produtos, serviços ou eventos;
    
    - **Detecção de fraudes:** Identificando atividades suspeitas e padrões de comportamento anormal em transações financeiras, comunicações ou registros de acesso;
    
    - **Análise de risco:** Avaliando riscos e incertezas em setores como finanças, seguros e saúde, usando dados  históricos e em tempo real para modelar e prever possíveis resultados;
    
    - **Recomendação personalizada:** Desenvolvendo sistemas de recomendação que fornecem conteúdo, produtos ou serviços personalizados com base no comportamento passado e nas preferências dos usuários;
    
    - **Otimização da cadeia de suprimentos:** Analisando dados de inventário, logística e vendas para melhorar a eficiência, reduzir custos e prever necessidades futuras.

---

## Conceitos Importantes

- **População:** também conhecida como população-alvo ou universo, é o conjunto completo de elementos ou unidades de interesse em um estudo ou pesquisa. A população pode incluir pessoas, animais, objetos ou eventos e pode ser finita ou infinita, dependendo do contexto;

- **Amostra:** é um subconjunto da população que é selecionado para representá-la em um estudo ou pesquisa. Esse subconjunto deve ser selecionado usando métodos adequados de amostragem, como amostragem aleatória simples, estratificada ou por conglomerados, para garantir que as características da população sejam adequadamente refletidas e que as inferências feitas a partir da amostra sejam válidas.

---

### Técnicas de Amostragem

- São métodos usados para selecionar uma amostra representativa da população em um estudo ou pesquisa. As principais técnicas podem ser categorizadas em 2 grupos: **amostragem probabilística e amostragem não probabilística**;

- **Amostragem probabilística:** nas técnicas desse tipo, cada elemento da população tem uma chance conhecida e não nula de ser selecionado para a amostra. Essas técnicas geralmente resultam em amostrar mais representativas e permitem o cálculo de medidas de incerteza, como margem de erro e intervalos de confiança. As principais:

    - **Amostragem aleatória simples:** Cada elemento da população tem igual probabilidade de ser selecionado. É como um sorteio onde todos os elementos têm a mesma chance de serem escolhidos;

    - **Amostragem sistemática:** Os elementos da população são selecionados em intervalos fixos, a partir de um ponto de partida aleatório;

    - **Amostragem estratificada:** A população é dividida em subgrupos homogêneos, chamados estratos, e uma amostra aleatória é selecionada de cada estrato. Isso garante que todos os segmentos da população sejam adequadamente representados na amostra;

    - **Amostragem por conglomerados:** A população é dividida em grupos heterogêneos, chamados conglomerados. Alguns conglomerados são selecionados aleatoriamente e todos os elementos desses conglomerados são incluídos na amostra.

- **Amostragem não probabilística:** nas técnicas desse tipo, a seleção dos elementos da população não é baseada na probabilidade. Essas técnicas são mais fáceis e mais rápidas de serem executadas, mas podem resultar em amostras menos representativas e não permitem o cálculo de medidas de incerteza. As principais:

    - **Amostragem por conveniência:** A seleção dos elementos é baseada na facilidade de acesso e na disponibilidade. Essa técnica pode ser enviesada, já que nem todos os elementos têm a mesma chance de serem selecionados;

    - **Amostragem por julgamento:** O pesquisador seleciona os elementos da amostra com base em seu conhecimento e critério;

    - **Amostragem por quotas:** Semelhante à estratificada, a população é dividida em subgrupos. Porém, os elementos são selecionados de forma não aleatória, com base em características específicas, até que uma quota pré-determinada seja atingida.

---

## Parâmetro vs Estatística

- **Parâmetro:** é uma medida numérica que descreve uma característica específica de uma **população**. Ele é um valor fixo e desconhecido, já que geralmente não é possível analisar todos os elementos da população. Os parâmetros são frequentemente representados por letras gregas. Eles fornecem informações valiosas sobre a população e são o objetivo final de muitas análises estatísticas;

- **Estatística:** é uma medida numérica calculada a partir de uma **amostra** selecionada da população. As estatísticas são usadas para estimar parâmetros populacionais e são representadas por letras latinas. Uma estatística é uma variável aleatória, já que seu valor varia de uma amostra para outro, e é possível calcular intervalos de confiança e margens de erro em torno dela.

---

## Dados Primários vs Dados Secundários

- **Dados primários:** são informações coletadas diretamente pelo pesquisador ou sua equipe para responder a uma pergunta específica de pesquisa ou atender a um objetivo específico. Esses dados são coletados pela primeira vez e são originais, ou seja, não foram utilizados em pesquisas anteriores. Eles geralmente são coletados por meio de métodos como entrevistas, questionários, observações, experimentos ou outros meios diretos de coleta de informações;

    - **Vantagens:** relevância direta para a questão de pesquisa, a possibilidade de personalização das perguntas e a capacidade de controlar a qualidade e a confiabilidade dos dados;

    - **Desvantagens:** demora e custo elevado.

- **Dados secundários:** são informações já coletadas e disponíveis, que foram obtidas ou geradas em pesquisas ou projetos anteriores, ou que são coletadas regularmente por organizações ou agências. Esses dados não são coletados especificamente para a pergunta de pesquisa em questão, mas podem ser aplicados ou reutilizados para responder a novas perguntas. Eles podem incluir relatórios de pesquisa, estudos acadêmicos, registros administrativos, dados de censo, informações financeiras e estatísticas governamentais.

    - **Vantagens:** economia de tempo e recursos, existência de diversas fontes e diversidade de informações para quantificação de questões;

    - **Desvantagens:** falta de controle, podem conter dados inadequados e desatualizados, fontes não confiáveis e dificuldade de reproduzir um estudo obtendo os mesmos resultados.

---

## Registros vs Variáveis

- **Registros:** são as unidades individuais de informação em um conjunto de dados. Cada observação (registro) representa uma instância única de um objeto, pessoa, evento ou situação que foi medido ou registrado. Em um conjunto de dados, os registros são geralmente **organizados em linhas**;

- **Variáveis:** são os atributos medidos ou registrados para cada observação. As variáveis descrevem as propriedades, qualidades ou quantidades que variam entre as observações. Em um conjunto de dados, as variáveis são geralmente **organizadas em colunas**.

---

### Tipos de Variáveis

- Os dados podem conter variáveis:
    
    - **Qualitativas:** utilizam termos descritivos para descrever algo de interesse, ex: cor dos olhos, estado civil, religião, gênero, grau de escolaridade etc. Dentro desta classificação, pode-se ter variáveis: **nominais** (não há uma ordem natural, ex: profissão, sexo, religião) e **ordinais** (possuem uma ordem natural, ex: escolaridade, classe social, fila);

    - **Quantitativas:** representadas por valores numéricos que podem ser contados ou medidos, ex: número de crianças em uma sala de aula, peso do corpo humano, idade etc. Dentro desta classificação, pode-se ter variáveis: **discretas** (os possíveis valores são contáveis, ex: número de filhos, número de carros, número de acessos) e **contínuas** (podem ser observados quaisquer valores dentro de um intervalo, ex: altura, peso, salário);

    - **Atenção:** um dado classificado como `Idade` pode ser quantitativo, ex: 10, 20, 90, 4, 5 anos. Porém, se esse dado for informado por "faixa etária", ele é qualitativo (ordinal), ex: 0 - 5 anos; 6 - 12 anos; 13 - 18 anos...

---

## Medidas de Posição

- As medidas de posição, também conhecidas como **medidas de tendência central**, são valores que descrevem o centro ou a posição central de um conjunto de dados. As três mais comuns são:

### Média

- É a soma de todos os valores de um conjunto de dados dividida pelo número total de valores. É frequentemente usada para representar o valor "típico" de um conjunto de dados. Ela pode ser afetada por **valores extremos (outliers)** e pode **não ser a melhor representação do centro dos dados em tais casos**.

### Mediana

- É o valor que separa um conjunto de dados ordenado em duas metades iguais. Se o número total de valores no conjunto de dados é ímpar, a mediana é o valor do meio. Se o número total de valores no conjunto de dados é par, a mediana é a média dos dois valores centrais. A mediana é **menos sensível a outliers** e pode ser uma medida **mais representativa do centro dos dados quando a distribuição é assimétrica ou contém outliers**.

### Moda

- É o valor que ocorre com maior frequência em um conjunto de dados. Um conjunto de dados pode ter nenhuma moda, uma moda (unimodal) ou várias modas (multimodal). A moda pode ser **usada para dados numéricos ou categóricos** e é uma **medida útil da tendência central**, especialmente quando a média e a mediana não são aplicáveis ou não fornecem uma representação adequada do centro dos dados.

---

## Medidas de Dispersão

- As medidas de dispersão são estatísticas que **quantificam a dispersão, a variabilidade ou a dispersão dos valores** em um conjunto de dados. Elas ajudam a entender o quão dispersos estão os valores em torno da medida central (como a média). As mais comuns:

### Variância

- É uma medida que indica o quanto os valores em um conjunto de dados variam em torno da média. Uma **variância maior** indica uma maior dispersão dos valores, enquanto uma **variância menor** sugere que os valores estão mais próximos da média. A variância é **calculada como a média dos quadrados das diferenças entre cada valor e a média do conjunto de dados**.

### Desvio Padrão

- É a **raiz quadrada da variância** e também mede a dispersão dos valores em um conjunto de dados. Ele é expresso na mesma unidade de medida dos valores originais, o que o torna mais fácil de interpretar em comparação com a variância. Um **desvio padrão maior** indica maior variabilidade dos valores, enquanto um **desvio padrão menor** sugere que os valores estão mais próximos da média. 

### Coeficiente de Variação (CV)

- Também conhecido como **coeficiente de variação relativa**, é uma medida estatística que expressa **a relação entre o desvio padrão e a média** de um conjunto de dados. Ele é **usado para comparar a variabilidade entre conjuntos de dados** com médias diferentes e unidades de medida distintas. O CV é comumente expresso como um percentual;

- Ele é especialmente útil quando se deseja comparar a dispersão de 2 ou mais conjuntos de dados que possuem diferentes escalas ou unidades de medida. Ele permite que os pesquisadores determinem qual conjunto de dados tem maior variabilidade relativa, independentemente das unidades em que os dados são expressos;

- **Fórmula:**

        CV = (Desvio Padrão / Média) x 100

- Um **CV menor** indica que os dados são menos dispersos em relação à média, enquanto um **CV maior** indica que os dados são mais dispersos.

---

## Medidas de Posição Relativa

- As medidas de posição relativa são estatísticas que **descrevem a posição de um valor específico em relação a outros valores** em um conjunto de dados. As mais comuns:

### Percentis

- São medidas que **dividem um conjunto de dados ordenado em 100 partes iguais**. O percentil de um valor específico indica a **porcentagem de valores no conjunto de dados que são menores ou iguais a esse valor**. Por exemplo, um valor no percentil 25 (`P25`) indica que 25% dos valores no conjunto de dados são menores ou iguais a esse valor. Eles são **úteis para comparar a posição relativa de um valor dentro de diferentes conjuntos de dados e para entender a dispersão dos dados**.

### Quartis

- São semelhantes aos percentis, mas **dividem um conjunto de dados ordenado em 4 partes iguais**. Existem **3 quartis**: o primeiro quartil (`Q1`), o segundo quartil (`Q2`) e o terceiro quartil (`Q3`). `Q1` corresponde ao percentil 25 (`P25`), `Q2` corresponde à mediana (percentil 50 - `P50`) e `Q3` corresponde ao percentil 75 (`P75`). Os quartis ajudam a entender a **dispersão dos dados e a identificar a presença de outliers**.

### Z-score

- É uma medida que **expressa a posição relativa de um valor em relação à média e ao desvio padrão** de um conjunto de dados. Ele **indica quantos desvios padrão um valor específico está acima ou abaixo da média** do conjunto de dados. Um **z-score positivo** indica que o valor está acima da média, enquanto um **z-score negativo** indica que o valor está abaixo da média. Eles são úteis para **comparar a posição relativa de valores em diferentes conjuntos de dados e para identificar outliers**.

---

## Métodos Estatísticos para Análise de Dados

- Os métodos mais comuns para análise de dados são:

    - **Análise descritiva:** envolve a descrição e resumo dos dados por meio de medidas de tendência central (média, mediana, moda), medidas de dispersão (variância, desvio padrão, coeficiente de variação), e medidas de posição relativa (percentis, quartis, z-score). Essa análise fornece uma visão geral dos dados e ajuda a entender sua distribuição e características básicas;

    - **Análise exploratória de dados (EDA):** é uma abordagem para analisar conjuntos de dados, geralmente com o objetivo de identificar padrões, tendências, outliers e relações entre variáveis. Essa análise envolve a criação de gráficos, como histogramas, gráficos de dispersão, gráficos de caixa e gráficos de barras, para visualizar os dados e gerar insights;

    - **Testes de hipóteses:** são métodos estatísticos que envolvem a formulação de hipóteses nulas e alternativas sobre os parâmetros de uma população e o uso de dados amostrais para testar a validade dessas hipóteses;

    - **Regressão:** é um método estatístico utilizado para modelar a relação entre uma variável dependente e uma ou mais variáveis independentes. A regressão linear é a forma mais simples de regressão e descreve a relação linear entre as variáveis;

    - **Análise de variância (ANOVA):** é um método usado para comparar as médias de 3 ou mais grupos, determinando se existem diferenças significativas entre eles;

    - **Análise de séries temporais:** envolve a análise de dados coletados ao longo do tempo para identificar padrões, tendências e ciclos. Essa análise pode incluir a decomposição da série temporal em componentes sazonais e de tendência, a aplicação de modelos autorregressivos e de médias móveis (ARIMA) e a previsão de valores futuros;

    - **Análise de agrupamento (clusterização):** é um método de aprendizado não supervisionado que agrupa observações (registros) com base em suas características e semelhanças;

    - **Análise de componentes principais (PCA):** é uma técnica de redução de dimensionalidade que transforma um conjunto de dados com muitas variáveis correlacionadas em um conjunto de dados com variáveis não correlacionadas chamadas de componentes principais.  

