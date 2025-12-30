# Machine Learning e Power BI para Segmentação de Clientes

## O que é Machine Learning (Aprendizado de Máquina)?

- É uma área da Inteligência Artificial que se concentra no desenvolvimento de algoritmos e técnicas que permitem que os computadores aprendam a executar tarefas sem serem explicitamente programados para isso. O **objetivo** é desenvolver modelos que possam *identificar padrões, fazer previsões e tomar decisões com base nos dados fornecidos*;

- O aprendizado de máquina pode ser dividido em 3 categorias:

    - **Aprendizado supervisionado:** Neste tipo de aprendizado, o algoritmo é treinado com um conjunto de dados rotulados, ou seja, com entradas e saídas conhecidas. O algoritmo utiliza esses dados para aprender a mapear as entradas nas saídas corretas. Exemplos comuns incluem classificação de imagens e previsão de preços;

    - **Aprendizado não supervisionado:** Aqui, o algoritmo é treinado com um conjunto de dados não rotulados, e seu objetivo é encontrar padrões e estruturas subjacentes nos dados. Exemplos comuns incluem agrupamento e redução de dimensionalidade;

    - **Aprendizado por reforço:** Neste tipo de aprendizado, o algoritmo, chamado de agente, aprende a tomar decisões com base em recompensas e punições. O agente interage com um ambiente e ajusta suas ações para maximizar as recompensas a longo prazo. Exemplos comuns incluem jogos e robótica.

- A verdade é que *Machine Learning* tem uma ampla gama de aplicações, desde a análise de dados e previsão até a automação e desenvolvimento de sistemas de recomendação. É uma área em rápido crescimento e desempenha um papel crucial no desenvolvimento de tecnologias avançadas. Além disso, é uma das atividades principais em projetos de Data Science. O foco desta unidade é o **aprendizado não supervisionado**.

---

## O que é Segmentação de Clientes?

- É o processo de **dividir a base de clientes de uma empresa em grupos distintos** com base em *características comuns, necessidades, comportamentos ou preferências*;

- O **objetivo** é entender melhor as necessidades e desejos de diferentes grupos de clientes e, assim, adaptar as estratégias de marketing, comunicação e vendas para atender a essas necessidades de maneira mais eficaz e personalizada;   

- A segmentação pode ser feita com base em diversos critérios, como:

    - **Demográficos:** Idade, sexo, estado civil, renda, ocupação, nível de educação e tamanho da família;

    - **Geográficos:** Localização, clima, densidade populacional e fronteiras políticas ou culturais;

    - **Psicográficos:** Estilo de vida, personalidade, valores, atitudes e interesses;

    - **Comportamentais:** Padrões de compra, frequência de uso, lealdade à marca, preferências e atitudes em relação a produtos e serviços.

- **A segmentação pode beneficiar as empresas de várias maneiras, incluindo:**

    - Compreender melhor as necessidades e expectativas de diferentes grupos de clientes;

    - Desenvolver campanhas de marketing e comunicação mais eficazes e personalizadas;

    - Identificar oportunidades de mercado e nichos ainda não explorados;

    - Melhorar a satisfação e retenção de clientes, oferecendo produtos e serviços mais adequados às suas necessidades;

    - Otimizar a alocação de recursos, concentrando-se nos segmentos de clientes mais lucrativos ou com maior potencial de crescimento.

- As empresas podem utilizar técnicas de análise de dados e aprendizado de máquina para segmentar sua base de clientes de forma mais precisa e sofisticada, identificando padrões e relações complexas entre diferentes variáveis e comportamentos.

---

## Laboratório 7 - Machine Learning com Python e Power BI no Jupyter Notebook

- O Power BI não é uma ferramenta voltada para projetos de aprendizado de máquina; por isso, é necessário utilizar outra ferramenta. Neste caso, a escolhida foi o **Jupyter Notebook**;

- Assim como nas unidades anteriores, o professor inicialmente examinou a base de dados para visualizar os campos, a quantidade de registros (500) e o conteúdo dos dados. A partir dessa análise, foi possível observar que, para realizar a segregação solicitada neste laboratório, seria necessário desenvolver um algoritmo capaz de dividir a base com precisão em três grupos distintos;

- Contudo, existe uma alternativa mais simples: a aplicação de técnicas de *Machine Learning*, que disponibilizam algoritmos prontos capazes de analisar os dados, identificar similaridades e realizar o agrupamento automaticamente, muitas vezes com apenas uma linha de código. Dessa forma, evita-se a necessidade de criar diversas regras manuais para realizar a segregação dos perfis.

---

### Como o Power BI Pode Ser Usado em Projetos de Machine Learning?

- Após a finalização do trabalho de modelagem, o conjunto de dados devidamente limpo e modelado pode ser importado para o Power BI. A partir disso, é possível criar relatórios e gráficos com base nos resultados obtidos durante a etapa de modelagem em Machine Learning, permitindo a análise e a visualização dos padrões identificados.

---

### Iniciando o Jupyter Notebook

- Para este projeto, o professor definiu que seria utilizada exclusivamente essa ferramenta tanto para a execução de códigos em linguagem Python, por meio do interpretador Anaconda Python, quanto para a elaboração dos relatórios no Power BI ao final do trabalho de modelagem. Para isso, foi necessário realizar previamente a instalação do **Anaconda**, uma distribuição gratuita de Python e R voltada para ciência de dados, aprendizado de máquina e IA. Essa distribuição facilita o gerenciamento de ambientes e pacotes, além de incluir, de forma nativa, ferramentas como o **Jupyter Notebook** e bibliotecas essenciais (por exemplo, NumPy e Pandas), tornando mais simples a configuração do ambiente de análise de dados em um único local;

- Após a instalação, foi aberto o **Prompt de Comando (CMD)** em modo administrador. Em seguida, dentro da pasta onde se encontra a base de dados, copiou-se o caminho do diretório e executou-se o comando `cd` seguido do respectivo caminho. Já no diretório correto, digitou-se o comando `jupyter notebook`, o que resultou na abertura da ferramenta no navegador. Por fim, no ambiente do Jupyter, bastou clicar no arquivo `Lab7.ipynb` para iniciar as atividades.

---

### Definição do Problema de Negócio

- No ambiente do **Jupyter Notebook**, o professor apresentou alguns comandos importantes, como **Kernel → Restart Kernel and Clear Outputs** e **Kernel → Restart Kernel and Run All Cells**, além de reforçar a importância de sempre clicar no ícone de salvamento, a fim de evitar a perda de alterações realizadas no notebook;

- Todo projeto de **Data Science** e **Machine Learning** tem início com a **definição do problema de negócio**. Neste caso, o problema proposto foi: *“Considerando dados históricos de clientes que realizaram compras em nossa empresa, realizar o agrupamento (segmentação) dos clientes por similaridade de características em três grupos e enviar o relatório para a equipe de Marketing”*. A partir dessa definição, o analista consegue determinar quais dados serão utilizados, como será realizado o pré-processamento, qual algoritmo de Machine Learning será aplicado e de que forma os resultados serão entregues. Assim, cada problema de negócio dá origem a um projeto específico;

- Sempre que são utilizadas técnicas de **Machine Learning**, faz-se necessário o uso de **dados históricos**. Caso a empresa não possua esses dados, não há matéria-prima suficiente para a aplicação das técnicas nesse momento. Nessa situação, o analista deve iniciar a coleta de dados e, após um período adequado (por exemplo, três ou quatro meses), retomar o projeto para aplicar os modelos de aprendizado de máquina;

- No contexto apresentado, **agrupamento** é sinônimo de **segmentação**, com o objetivo inicial de formar três grupos de clientes. Entretanto, surge um questionamento relevante: *será que três grupos são suficientes para representar adequadamente os padrões presentes nos dados históricos?*. Essa é uma reflexão que cabe ao analista, uma vez que a solicitação do negócio nem sempre corresponde à solução ideal do ponto de vista analítico. Por fim, é necessário encaminhar o relatório à equipe de Marketing. Embora a ferramenta não tenha sido explicitamente definida, cabe ao analista verificar se a empresa possui licença de algum software disponível. Neste projeto, optou-se pelo uso do **Power BI**.

---

### Carregando os Dados

- **Como esses dados podem ser obtidos?** Após a definição do problema de negócio, que pode partir da área de negócios, da equipe de TI ou de projetos, ou até mesmo do próprio analista/cientista de dados, que é convidado a compreender a demanda e auxiliar na formulação do problema, cabe ao analista buscar a matéria-prima do projeto. Esses dados podem ser obtidos, por exemplo, a partir de **bancos de dados internos da empresa**, planilhas ou sistemas de gestão de clientes (CRM/CLM), bem como de outros sistemas internos. Uma vez identificada a fonte, os dados são carregados e inicia-se o processo de análise;

- Para o carregamento dos dados deste projeto, utilizou-se a **linguagem Python** no ambiente do **Jupyter Notebook**. Após a definição da linguagem, tornou-se necessário o uso de alguns pacotes, os quais já se encontram disponíveis após a instalação do **Anaconda**. Neste caso, foi utilizada a biblioteca **Pandas**, amplamente empregada para manipulação e análise de dados (frequentemente comparada ao Excel no contexto do Python), bem como a biblioteca **Scikit-learn (Sklearn)**, que é um dos principais frameworks de **Machine Learning** para a linguagem Python. Mais especificamente, utilizou-se o pacote `cluster`, com a função **KMeans**, responsável pelo algoritmo de aprendizado de máquina não supervisionado. Além disso, para possibilitar o treinamento adequado do modelo, foi necessário realizar o pré-processamento dos dados, utilizando o pacote `preprocessing` da Sklearn, que disponibiliza a função **StandardScaler**;

- Uma dúvida recorrente é: *como sabemos quais pacotes devem ser utilizados?* A resposta está diretamente relacionada à definição do problema de negócio. A partir dela, o cientista ou analista de dados já consegue identificar a técnica a ser aplicada. Neste projeto, como o objetivo é o **agrupamento (segmentação)** de clientes, utiliza-se a técnica de **clusterização**, que, na nomenclatura de Machine Learning, corresponde ao algoritmo **KMeans**, um método de aprendizado **não supervisionado**;

- Após a realização das importações necessárias, procedeu-se também ao carregamento da base de dados, conforme apresentado a seguir:

```python

    # Versão da Linguagem Python
    from platform import python_version
    print('Versão da Linguagem Python Usada Neste Jupyter Notebook:', python_version())

    # Imports
    import pandas as pd
    from sklearn.cluster import KMeans
    from sklearn.preprocessing import StandardScaler

    # Carrega os dados
    df_dsa = pd.read_csv('dataset/dados_clientes.csv')
    type(df_dsa)

    # Visualiza as 10 primeiras linhas
    df_dsa.head(10)

```

---

### Análise Exploratória

- Conforme orientado pelo professor, a primeira questão a ser levantada nesta etapa é: *“Os dados apresentam algum tipo de problema?”*. Para responder a essa pergunta, iniciou-se a **análise exploratória dos dados**, começando pela geração de um **resumo estatístico** de três variáveis de interesse: `idade`, `renda_anual` e `pontuacao_gastos`. Para isso, utilizou-se o método `describe`, que retorna uma tabela contendo estatísticas descritivas (essa etapa poderia ser feita no Power BI, conforme já visto em outra unidade);

- Inicialmente, analisa-se o valor de `count`, que representa a quantidade de registros em cada coluna. Neste projeto, o número de linhas é o mesmo para as três variáveis, o que indica a ausência de valores nulos ou ausentes. Em seguida, são avaliadas as demais métricas estatísticas, como média, desvio padrão, valores mínimo e máximo, com o objetivo de verificar se os dados estão em conformidade ou se apresentam valores atípicos (**outliers**). No conjunto de dados analisado, não foram identificadas inconsistências ou valores fora do padrão esperado;

- O resumo estatístico das variáveis selecionadas pode ser observado no trecho de código a seguir:

```python

    # Resumo estatístico
    df_dsa[['idade', 'renda_anual', 'pontuacao_gastos']].describe()

```

---

### Pré-Processamento dos Dados

- Como não foram identificados problemas na etapa de análise exploratória, o próximo passo consiste no **pré-processamento dos dados**, que envolve a aplicação de técnicas necessárias para preparar os dados para a utilização do algoritmo de Machine Learning selecionado. Neste projeto, o algoritmo escolhido foi o **K-Means**, o qual possui como pré-requisito a utilização de dados padronizados;

- A padronização é necessária porque o algoritmo K-Means é sensível à escala das variáveis, uma vez que utiliza medidas de distância para formar os agrupamentos. Dessa forma, variáveis em escalas diferentes poderiam influenciar de maneira desproporcional o resultado do modelo. Por esse motivo, torna-se fundamental que todas as variáveis de interesse estejam na mesma escala;

- Para realizar esse procedimento, utilizou-se a classe `StandardScaler()` da biblioteca **Scikit-learn**, responsável por padronizar os dados de modo que apresentem média igual a zero e desvio padrão igual a um. Inicialmente, criou-se o padronizador e, em seguida, aplicou-se o método `fit_transform` apenas às variáveis de interesse (`idade`, `renda_anual` e `pontuacao_gastos`), resultando em um conjunto de dados pronto para a aplicação do algoritmo de clusterização;

- O processo de padronização pode ser observado no trecho de código a seguir:

```python

    # Cria o padronizador dos dados
    padronizador = StandardScaler()

    # Aplica o padronizador somente nas colunas de interesse
    dados_padronizados = padronizador.fit_transform(df_dsa[['idade', 'renda_anual', 'pontuacao_gastos']])

    # Visualiza os dados padronizados
    print(dados_padronizados)

```

- Essa etapa deve ser realizada em conformidade com os pré-requisitos do algoritmo selecionado para aplicação.

---

### Construção do Modelo de Machine Learning para Segmentação de Clientes

- Conforme apresentado anteriormente, o algoritmo selecionado para a segmentação dos clientes foi o **K-Means**. Esse algoritmo possui alguns parâmetros que permitem controlar o seu comportamento durante o processo de aprendizado. Um dos principais parâmetros é o número de **clusters** (`k`), que indica ao algoritmo quantos grupos devem ser formados a partir dos dados;

- No contexto do problema de negócio, foi solicitada a criação de **três grupos de clientes**, portanto definiu-se inicialmente `k = 3`. Entretanto, surge um questionamento importante: *três grupos são realmente suficientes para representar adequadamente a estrutura dos dados?*. Em cenários reais, recomenda-se realizar uma etapa prévia de validação para determinar o valor ideal de `k`, utilizando técnicas como o método do cotovelo (*elbow method*). Neste projeto específico, o valor de `k` foi previamente validado pelo professor. Contudo, no ambiente corporativo, cabe ao analista avaliar criticamente essa escolha e, se necessário, propor um valor diferente, devidamente justificado, mesmo que a demanda inicial indique outro número de grupos;

- Com o valor de `k` definido, iniciou-se a construção do modelo por meio da criação do objeto responsável pela execução do algoritmo K-Means, conforme apresentado a seguir:

```python

    # Definimos o número de clusters (k)
    k = 3

    # Criamos o modelo K-means
    kmeans = KMeans(n_clusters = k)

```

- Em seguida, o modelo foi treinado utilizando os **dados previamente padronizados**, etapa fundamental para que o algoritmo pudesse identificar padrões e similaridades entre os clientes:

```python

    # Treinamento do modelo com os dados padronizados
    kmeans.fit(dados_padronizados)

```

- Após o treinamento, o modelo passou a possuir os agrupamentos definidos. Na sequência, os **rótulos dos clusters** gerados pelo algoritmo foram associados ao conjunto de dados original, criando-se uma nova variável denominada `cluster`, que indica a qual grupo cada cliente pertence. Por fim, os resultados foram visualizados e salvos em disco para posterior análise e geração de relatórios:

```python

    # Atribuímos os rótulos dos clusters aos clientes
    df_dsa['cluster'] = kmeans.labels_

    # Exibe o resultado (10 primeiras linhas)
    df_dsa.head(10)

    # Salvamos o resultado em disco
    df_dsa.to_csv('dataset/segmentos.csv', index = False)

```

- Mas como o modelo chegou a esse resultado? Como os clusters foram definidos para cada cliente? Após o treinamento, os clientes passam a ser identificados por rótulos (0, 1 e 2), sendo que o objetivo do algoritmo é garantir a **maior similaridade possível entre os elementos de um mesmo grupo** e a **maior diferença entre grupos distintos**;

- O algoritmo **K-Means** alcança esse resultado por meio de cálculos matemáticos baseados em medidas de distância. Inicialmente, o modelo define centróides (pontos centrais) para cada cluster. Em seguida, cada vetor de dados (ou seja, cada cliente representado pelas variáveis analisadas) tem sua distância calculada em relação a esses centróides, geralmente utilizando a **distância euclidiana**;

- Cada cliente é então atribuído ao cluster cujo centróide apresenta a menor distância. Após essa atribuição inicial, os centróides são recalculados com base na média dos pontos pertencentes a cada grupo. Esse processo de atribuição e atualização dos centróides se repete de forma iterativa até que não ocorram mais mudanças significativas nos agrupamentos, indicando a convergência do modelo;

- Dessa forma, o K-Means consegue segmentar os clientes em grupos que apresentam características semelhantes entre si, garantindo maior coerência interna dentro de cada cluster e maior separação entre os diferentes grupos.
**ATENÇÃO**: Para fazer a autenticação é necessário ter uma conta no Power BI Service, criada com e-mail de estudante ou corporativo. Caso você não tenha, apenas acompanhe as aulas e ao final mostraremos como abrir o relatório no Power BI  Desktop, que será fornecido ao final do capítulo.

---

