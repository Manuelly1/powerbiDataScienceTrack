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

## Técnicas de Amostragem

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
    