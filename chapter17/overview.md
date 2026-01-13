# Machine Learning e Power BI para Detecção de Outliers (Anomalias)

## O que é Detecção de Anomalias?

- É uma técnica de Machine Learning (ML) e Estatística que visa identificar padrões incomuns, inesperados ou anômalos nos dados. Esses padrões podem ser diferentes das observações normais de várias maneiras, como magnitude, frequência ou comportamento. A detecção de anomalias é importante porque as anomalias podem indicar problemas, erros, falhas, fraudes ou atividades maliciosas e, em muitos casos, é crucial identificar e analisar esses eventos anômalos para tomar decisões informadas e apropriadas;

- Existem várias abordagens para detectar anomalias em ML, algumas das quais incluem:

    - **Métodos Estatísticos:** Esses métodos baseiam-se na análise estatística dos dados, como testes de hipóteses, distribuições de probabilidade e medidas de dispersão (por exemplo, desvio padrão e intervalos interquartis). Observações que estão significativamente distantes da média ou fora dos intervalos esperados são consideradas anômalas;

    - **Aprendizado Supervisionado:** Nesta abordagem, um modelo de ML é treinado usando um conjunto de dados rotulado, que inclui exemplos de observações normais e anômalas. O modelo aprende a distinguir entre as duas classes e, em seguida, pode ser usado para classificar novas observações como normais ou anômalas;

    - **Aprendizado Não Supervisionado:** Neste caso, os algoritmos de ML são usados para analisar dados não rotulados e identificar padrões ou agrupamentos naturais neles. As anomalias são identificadas como pontos de dados que não se encaixam bem em nenhum desses agrupamentos ou que estão significativamente distantes de outros pontos de dados. Alguns exemplos incluem clustering e técnicas de redução de dimensionalidade;

    - **Aprendizado Semi-Supervisionado:** Esta abordagem combina elementos dos dois anteriores. Os algoritmos são treinados em um conjunto de dados parcialmente rotulado, que contém exemplos de observações normais e um pequeno número de exemplos anômalos. O modelo aprende a distinguir entre as classes e identificar novas anomalias com base nos padrões aprendidos;

    - **Métodos Baseados em Densidade:** Esses métodos identificam anomalias como pontos de dados que estão localizados em áreas de baixa densidade do espaço de recursos (atributos). Um exemplo desse tipo é o DBSCAN.

---

## Principais Áreas de Aplicação da Detecção de Anomalias

- A detecção de anomalias é uma técnica útil em várias áreas, uma vez que ajuda a identificar padrões incomuns ou comportamentos inesperados nos dados. Algumas das áreas mais comuns incluem:

    - **Finanças:** Detecção de fraudes em transações bancárias ou de cartão de crédito. Monitoramento do mercado financeiro para identificar atividades de insider trading ou manipulação de mercado;

    - **Cibersegurança:** Detecção de intrusões em redes, identificando padrões incomuns de tráfego ou comportamento do usuário. Monitoramento de logs de servidores e sistemas para identificar atividades maliciosas ou não autorizadas;

    - **Manutenção Preditiva:** Análise de dados de sensores em equipamentos industriais ou infraestrutura para identificar falhas iminentes ou desempenho degradado. Análise de anomalias em sinais de sensores IoT para identificar padrões incomuns;

    - **Saúde:** Identificação de eventos adversos ou erros médicos em registros de pacientes. Monitoramento de sinais vitais e dados de sensores de pacientes para identificar condições anômalas que possam indicar uma deterioração da saúde do paciente;

    - **Monitoramento Ambiental:** Análise de dados meteorológicos e climáticos para identificar eventos extremos ou mudanças significativas nas condições ambientais. Monitoramento da qualidade do ar e da água para identificar poluição ou contaminação;

    - **Marketing e Vendas:** Análise de padrões de comportamento do consumidor para identificar segmentos de clientes incomuns ou oportunidades de mercado não exploradas. Identificação de atividades fraudulentas em campanhas publicitárias, como cliques falsos ou impressões.

---

## Visão Geral do Laboratório 8 – Detecção de Anomalias em Transações Financeiras com Linguagem R e Power BI

- Inicialmente, após o download dos arquivos da unidade, o professor apresentou as bases de dados utilizadas no laboratório, começando pelo arquivo `dados_historicos.csv`. Esse arquivo contém duas colunas, `transacao1` e `transacao2`, em que cada linha representa um cliente que realizou duas transações em uma instituição financeira fictícia. Os gestores desconfiam que alguns clientes possam estar realizando transações consideradas fraudulentas e, por esse motivo, solicitaram o apoio do analista para investigar o cenário;

- Diante desse contexto, surge o seguinte questionamento: **como o analista pode auxiliar na resolução desse tipo de problema?**. E, ainda, **como identificar transações que potencialmente caracterizam fraudes?**;

- O ponto de partida consiste na busca por **anomalias (outliers)**, isto é, eventos que fogem do padrão observado no conjunto de dados. A partir da identificação dessas anomalias, os resultados são entregues aos gestores, possibilitando que a área de segurança da empresa realize uma investigação mais detalhada e avalie se tais registros correspondem, de fato, a fraudes ou tentativas suspeitas em transações financeiras;

- É importante ressaltar que a presença de valores negativos nesse contexto financeiro não é, necessariamente, algo incomum. Além disso, uma análise manual da base de dados torna difícil a identificação de anomalias apenas “a olho nu”. Nesse sentido, destaca-se a importância da aplicação de técnicas de **Machine Learning**, que permitem varrer automaticamente o conjunto de dados e identificar registros que se desviam do padrão esperado. Com base nesses cálculos matemáticos, torna-se possível classificar e sinalizar potenciais anomalias;

- O **Power BI** não é uma ferramenta voltada à construção de modelos de **Machine Learning**, razão pela qual ele não será utilizado nessa etapa de modelagem. Assim, optou-se pelo uso da **linguagem R** para a criação do modelo de detecção de anomalias. Após a construção do modelo, os resultados serão apresentados por meio de visualizações gráficas no Power BI;

- Um dos gráficos que se deseja apresentar no relatório é o **boxplot**, o qual não é disponibilizado de forma nativa no Power BI. Para contornar essa limitação, será utilizada a funcionalidade **R Script Visual**, que permite a criação de gráficos personalizados diretamente em linguagem R dentro do ambiente do Power BI.

---

### Instalando R, RTools e RStudio no Windows

- É importante destacar que esse processo também poderia ser realizado utilizando a linguagem Python. Porém, o professor optou por apresentar uma alternativa diferente. Conforme ressaltado em aula, as empresas buscam profissionais capazes de **resolver problemas**, e o conhecimento de um maior número de ferramentas contribui para que o analista se destaque no mercado de trabalho;

- A linguagem **R** é uma linguagem estatística com características de linguagem de programação, amplamente utilizada em projetos de **Ciência de Dados**. Diferentemente do Python, que é uma linguagem de uso geral e possui bibliotecas voltadas à análise estatística, o R foi desenvolvido com um propósito específico: **realizar análises estatísticas**. Por esse motivo, trata-se de uma linguagem bastante poderosa e completa para esse tipo de aplicação;

- Por se tratar de uma linguagem interpretada, é necessário instalar tanto o **interpretador da linguagem R** quanto um **ambiente de desenvolvimento integrado (IDE)**. Neste projeto, a IDE utilizada será o **RStudio**. Inicialmente, o professor apresentou o site oficial da linguagem R, disponível em `cran.r-project.org`, que funciona como repositório oficial. Ao acessar esse endereço, deve-se selecionar a opção **Download R for Windows**. Na interface seguinte, são apresentados diversos links, porém apenas dois são necessários: `base` e `RTools` (este último corresponde a um conjunto de ferramentas de compilação);

- Ao clicar em `base`, o usuário é direcionado para uma nova interface que exibe a opção **Download R-4.5.2 for Windows**. Entretanto, essa versão não foi utilizada neste projeto por se tratar de uma versão mais recente, o que poderia gerar problemas de compatibilidade com outros pacotes. Assim, optou-se pelo caminho **Previous releases → R-4.2.3 → R-4.2.3-win.exe**. Essa versão foi escolhida por ser a versão estável imediatamente anterior à mais recente. O arquivo `.exe` corresponde ao interpretador da linguagem R;

- Para a instalação do **RTools**, seguiu-se o caminho **RTools → RTools 4.2 → RTools42 installer**, versão compatível com o R-4.2.3. O RTools é necessário porque a linguagem R foi desenvolvida em **C**, e a instalação de determinados pacotes exige a compilação de código-fonte. Como a linguagem C é compilada, faz-se necessário um compilador, que é fornecido pelo RTools. Em sistemas **macOS** e **Linux**, essa etapa não é necessária, pois esses sistemas operacionais já incluem compiladores nativos;

- Outra instalação essencial refere-se à IDE utilizada para o desenvolvimento dos scripts: o **RStudio**. Para isso, acessa-se o site `posit.co`, seleciona-se a opção **Download RStudio** e, em seguida, **RStudio Desktop (Download)**;

- Após a realização do download dos três arquivos (**R**, **RTools** e **RStudio**), procede-se à instalação de cada um deles, seguindo as instruções padrão do instalador. Inicialmente, realiza-se a instalação do interpretador da linguagem R (`R-4.2.3-win.exe`); em seguida, efetua-se a instalação do **RTools**; e, por fim, conclui-se o processo com a instalação do **RStudio**.

---

### Customizando o RStudio

- Inicialmente, o professor realizou a customização dos painéis do **RStudio**. Para isso, acessou o caminho **Tools → Global Options → Pane Layout**. Nessa etapa, foram selecionadas as opções `Console` e `Source` para o painel do lado esquerdo e, no painel do lado direito, as opções `Environment` e `Files`. Após realizar essas configurações, as alterações foram aplicadas;

- Em seguida, foi realizada a configuração do diretório de trabalho padrão. Para isso, acessou-se o menu **Tools → Global Options → General**. No campo **Default working directory**, o valor padrão era `~`, que representa o diretório *home* da máquina. Contudo, esse caminho foi alterado para apontar diretamente para o diretório de trabalho do projeto, onde se encontram os arquivos do curso, mais especificamente a pasta `cap17`, que contém os arquivos utilizados neste laboratório. Para isso, utilizou-se a opção **Browse**, selecionou-se a pasta desejada e, em seguida, clicou-se em **Apply** e **OK**;

- Após essas configurações, o RStudio foi fechado e aberto novamente para garantir que as alterações fossem reconhecidas corretamente. Caso haja dúvida se o diretório foi configurado de forma adequada, pode-se utilizar o comando `getwd()` para verificar o diretório de trabalho atual.

---

### Instalação de Pacotes R para Detecção de Anomalias, Manipulação e Visualização de Dados

- Inicialmente, o professor orientou que cada aluno verificasse, no **Power BI**, se a versão da linguagem R estava corretamente instalada. Para isso, acessou-se o caminho **Arquivo → Opções e Configurações → Script R**. Após a confirmação da versão instalada, a ferramenta foi fechada e o foco passou a ser a construção do modelo de *Machine Learning* na ferramenta **RStudio**;

- Como a configuração da pasta já havia sido realizada em uma etapa anterior, neste momento o professor acessou a opção **Files**, que abriu o painel de arquivos. Em seguida, foi selecionado o arquivo **`Lab8.R`**, que continha o script a ser trabalhado;

- O **RStudio** não reconheceu corretamente algumas palavras. Para corrigir esse problema, seguiram-se os seguintes passos: **Tools → Global Options → Spelling**. Nessa tela, foram desmarcadas todas as opções relacionadas a **Ignore** e **Checking**, desativando, assim, as verificações ortográficas;

- Para a instalação dos pacotes, o procedimento foi realizado de forma manual. Na linguagem R, esse processo precisou ser executado **linha por linha**. Ou seja, selecionou-se a linha de código desejada e clicou-se no botão **Run**, que executou o comando e exibiu o resultado. Esse procedimento foi repetido para cada pacote. Vale ressaltar que foi necessário ter **acesso à internet** para que a instalação fosse concluída com sucesso;

- Após a instalação, fez-se necessário o **carregamento dos pacotes**. Para isso, foram selecionados todos os comandos que iniciavam com `library` e, em seguida, clicou-se em **Run**.

--- 

### Carregando Dados Históricos com Linguagem R

- Depois do carregamento dos pacotes, foi executada a linha de código responsável pelo carregamento da base de dados e, em seguida, a linha de visualização. Com isso, foi possível observar a base `dados_historicos_dsa`.

---

### Aprendizado Não Supervisionado para Detecção de Anomalias

- Existem duas possibilidades em *Machine Learning*: trabalhar com aprendizado supervisionado ou não supervisionado. Contudo, para utilizar o aprendizado supervisionado, seria necessário acrescentar uma nova coluna à base de dados que indicasse se cada registro representava ou não uma fraude/anomalia. Para isso, ao analisar a base de dados históricos, um especialista deveria avaliar, por exemplo, se a primeira linha correspondeu a uma fraude ou a uma anomalia. Em seguida, o especialista indicaria “sim” ou “não”, preenchendo essa terceira coluna. Esse processo é conhecido como **etiquetagem** e é necessário quando se deseja utilizar aprendizado supervisionado. Esse procedimento pode ser automatizado, desde que o analista conheça a regra que define uma anomalia, ou seja, se alguém do time de negócio consegue responder à pergunta: *“O que define uma anomalia?”*. A partir dessa definição, a regra é incorporada ao algoritmo, criando-se a coluna de saída, tendo `transacao1` e `transacao2` como dados de entrada e a terceira coluna como dado de saída;

- Para este projeto, o procedimento de etiquetagem não foi realizado. Dessa forma, aplicou-se o **aprendizado não supervisionado**. Nesse caso, os dados foram fornecidos ao algoritmo, que buscou identificar padrões existentes na base. A partir desses padrões, o algoritmo passou a identificar os registros que se encontravam fora do comportamento esperado. Para isso, os dados foram agrupados por meio de técnicas estatísticas, e aquilo que ficou fora do padrão foi considerado como uma possível anomalia, ficando a validação final sob responsabilidade do analista. Essa abordagem é indicada quando se dispõe apenas de dados de entrada e não há regras previamente definidas;

- O algoritmo escolhido foi o **Isolation Forest**, disponibilizado no pacote `solitude`.

---

### Construindo o Modelo de Machine Learning para Detecção de Anomalias

- Inicialmente, o professor pontuou que algumas etapas foram adiantadas, uma vez que os dados já estavam devidamente formatados. Dessa forma, não se fez necessária a limpeza e manipulação prévia da base de dados;

- Para a **criação do modelo**, o procedimento seguiu o mesmo padrão das etapas anteriores: selecionou-se a linha de código e clicou-se em `Run`. O comando executado foi:

```r

    modelo_ml_dsa = isolationForest$new() 

```

- Esse comando chama o objeto `isolationForest` e o método `new`, responsável por instanciar o modelo, cujo resultado foi armazenado na variável `modelo_ml_dsa`;

- Após a criação do modelo, realizou-se a etapa de **treinamento**. Para isso, foi executado o seguinte comando:

```r

    modelo_ml_dsa$fit(dados_historicos_dsa)

```

- Para o treinamento, foi chamado o método `fit`, indicando que o modelo seria ajustado utilizando os dados históricos previamente carregados. Durante esse processo, o algoritmo “varreu” a base de dados em busca de padrões de similaridade, formando grupos com características semelhantes. Dentro de cada grupo, foram calculadas as similaridades internas entre os pontos de dados. Em seguida, o algoritmo avaliou todos os registros e identificou como anomalias aqueles que se encontravam mais distantes do centro de seus respectivos grupos.

---

### Fazendo Previsões com o Modelo de Detecção de Anomalias

- Antes de iniciar, o professor pontuou que é comum surgirem alguns questionamentos, como: *“Como eu sei qual algoritmo usar?”*. Para responder a isso, ele destacou que a **experimentação** é fundamental. A escolha do algoritmo deve partir do conhecimento prévio que se tem sobre ele e da avaliação dos resultados obtidos. Em um projeto do dia a dia, o analista precisa, primeiramente, carregar os dados e, em seguida, realizar as etapas de checagem, análise exploratória, limpeza, pré-processamento e transformação. Somente após essas fases é feita a construção do modelo;

- Para realizar a previsão, procedeu-se da seguinte forma: o conjunto de dados foi chamado, concatenado com as previsões geradas pelo modelo e, posteriormente, ordenado pelo *score* de anomalia. Em outras palavras, o que se está dizendo ao interpretador da linguagem R é: pegue os dados, gere as previsões a partir do modelo e, por fim, ordene os registros pelo *score* de anomalia em ordem decrescente. O resultado desse processo foi armazenado na variável `previsoes_historico`. O script ficou da seguinte forma:

```r

    # Faz as previsões com o modelo usando os dados históricos
    previsoes_historico = dados_historicos_dsa %>%
    modelo_ml_dsa$predict() %>%
    arrange(desc(anomaly_score))

```

- Após a execução dessas linhas, foi executada outra etapa, a de visualização (`View`), que retornou uma tabela com as colunas `id`, `average_depth` (profundidade média) e `anomaly_score`. Esse *score* indica o quanto uma observação está fora do padrão: quanto **menor** o valor, mais dentro do padrão ela se encontra; quanto **maior**, maior a probabilidade de ser uma anomalia;

- Posteriormente, foi gerado um *plot* de densidade para analisar a distribuição dos *scores* de anomalia. Nesse *plot*, utilizou-se o conjunto de dados, mais especificamente a coluna `anomaly_score`. Ao aplicar a função `plot` e executar essa linha, foi gerado um gráfico no qual:

    - o **Eixo X** representa o *score* de anomalia, que varia aproximadamente de 0 até 0,75. Esse valor é produzido pelo algoritmo e, como mencionado anteriormente, quanto maior o *score*, maior a chance de o registro ser uma anomalia;

    - o **Eixo Y** representa a densidade, ou seja, a frequência de ocorrência dos valores.

- No gráfico gerado, foi possível observar que a maioria dos registros apresenta *scores* de anomalia abaixo de 0,60, o que indica que valores inferiores a esse limiar tendem a representar o comportamento padrão. Assim, valores acima de 0,60 podem indicar possíveis anomalias, funcionando como um indício de observações fora do padrão;

- Surge, então, o seguinte questionamento: *“Como definir, de fato, o que é uma anomalia? O ponto de corte deve ser 0,60, 0,70, 0,45…?”*, o algoritmo não fornece explicitamente quais registros são anômalos; ele apenas atribui *scores*. Cabe ao cientista de dados definir o ponto de corte mais adequado, considerando o contexto do problema, a distribuição dos dados e o impacto de falsos positivos e falsos negativos.

---

### Definindo o Score de Anomalia
