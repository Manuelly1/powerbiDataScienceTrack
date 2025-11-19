# Curso: Microsoft Power BI para Business Intelligence e Ciência de Dados

## Conceitos Importantes de Dados

- **Data Warehouse:** é um banco de dados central que reúne e organiza grandes volumes de dados históricos vindos de várias fontes da empresa (sistemas de vendas, RH, marketing etc), com o objetivo de facilitar análises e tomadas de decisão;

- **Data Mart:** é como um “mini data warehouse”, voltado para um departamento específico (por exemplo, um data mart de vendas ou de finanças). Ele contém apenas os dados relevantes para aquela área;

- **ETL (Extract, Transform, Load):** é o processo de extração, transformação e carga dos dados, ou seja, buscar os dados das fontes, limpá-los e padronizá-los, e armazená-los no data warehouse;

- **OLAP (Online Analytical Processing):** são ferramentas e técnicas para análise multidimensional dos dados, permitindo explorar informações de diferentes ângulos (por exemplo, vendas por região, tempo e produto);

- **Data Lake:** é um repositório que guarda dados brutos e não estruturados (textos, imagens, logs etc), geralmente usado antes de um processamento mais analítico;

- **BI (Business Intelligence):** é um conceito aplicado a um conjunto de ferramentas e práticas que visa transformar os dados do data warehouse em relatórios, dashboards e insights valiosos para o negócio.

---

## Unidade 2: Laboratório Prático I

- A base de dados `dataset.csv` foi disponibilizada e, após ser conectada e carregada na ferramenta, submeteu-se à aplicação de diferentes métricas analíticas;

### Aula - Cartão de Métricas

- O professor iniciou respondendo à primeira pergunta do roteiro: **“Qual o valor total vendido?”**, que corresponde a uma métrica numérica. Em outras palavras: **“Considerando todas as vendas, qual foi o total vendido?**”;

- No Power BI, ele inseriu um **cartão visual** e adicionou o campo `Total_Vendas`, que já continha o somatório dos valores. Dessa forma, foi possível responder já a primeira questão;

- **Observação:** Se o campo `Total_Vendas` não existisse pronto no `dataset`, seria preciso criar essa métrica manualmente dentro do Power BI usando DAX;

    - **Seria algo assim:**

    - Iria em uma `Nova Medida` e em seguida adicionaria uma fórmula DAX parecida com esta:

        `Total_Vendas = SUMX(dataset, dataset[Quantidade] * dataset[Preco_Unitario] * (1 - dataset[Desconto]))`

    - Se o valor de cada item já estiver em uma coluna (por exemplo, `Valor_Venda`):

        `Total_Vendas = SUM(dataset[Valor_Venda])`
        
    - O correto é utilizar o `preço × quantidade`, aplicando o `desconto` apenas quando necessário. Como neste caso ele é considerado, foi incluído na fórmula apresentada acima.

---

### Aula - Gráfico de Pizza

- O professor iniciou respondendo à segunda pergunta do roteiro: **“Quantas vendas foram realizadas por categoria de produto?”**. Ele escolheu o **gráfico de pizza**, pois, primeiramente, selecionou esse tipo de visual e, em seguida, adicionou o campo `Categoria` em `Legenda`. Depois, inseriu `ID_Pedido` em `Valores`, e o Power BI retornou automaticamente a contagem de `ID_Pedido` por `Categoria`, ou seja, já resolveu o problema, uma vez que fez a contagem do número de registros para cada `Categoria`;

- **Observação:** Segundo o professor, como a base possui poucas categorias, o gráfico de pizza é uma boa opção para representar esse cenário. Caso houvesse mais de três categorias, o uso desse tipo de gráfico já não seria recomendado.

---

### Aula - Gráfico de Barras Empilhadas

- O professor respondeu à terceira pergunta do roteiro: **“Quantas vendas foram realizadas por país considerando a prioridade de entrega?”**. Nesse caso, o gráfico precisava apresentar **três informações simultâneas**: a **quantidade de vendas realizadas**, os **países** em que ocorreram e a **prioridade de entrega**. Portanto, o gráfico mais adequado seria aquele capaz de representar múltiplas variáveis, sendo assim, o **gráfico de barras empilhadas** foi a escolha ideal;  

- Primeiramente, ele adicionou a variável **`País`** no **`Eixo Y`**. Em seguida, como o objetivo era exibir a quantidade de vendas por país, inseriu a variável **`ID_Pedido`** no **`Eixo X`**, onde o Power BI realizou automaticamente a **contagem dos registros**. Por fim, para incluir a dimensão referente à **prioridade de entrega**, adicionou o campo **`Prioridade`** em **`Legenda`**, concluindo assim a construção do gráfico e respondendo à terceira questão do roteiro.  

---

### Aula - Gráfico de Barras Horizontais 

- O professor ensinou como responder à quarta pergunta do roteiro: **“Qual foi a média de desconto nas vendas por subcategoria de produto?”**;

- Antes de montar o gráfico, o professor verificou a quantidade de elementos presentes na variável **`Subcategoria`** e percebeu que havia **muitos valores distintos**. Por esse motivo, o **gráfico de pizza** não seria indicado, sendo o **gráfico de barras horizontais** uma escolha mais adequada para representar os dados;

- Após selecionar o tipo de gráfico, ele adicionou **`Subcategoria`** em **`Eixo X`** e **`Desconto`** em **`Eixo Y`**. Inicialmente, o Power BI aplicou o **somatório dos valores** por padrão. Para ajustar, o professor clicou na **“setinha”** ao lado do campo **`Desconto`** e alterou a agregação para **média**, obtendo assim o resultado desejado.

---

### Aula - Mapa Mundial 

- O professor ensinou como responder à quinta pergunta do roteiro: **“Quais países tiveram maior média de valor de venda? Demonstre em um mapa.”**. Para isso, ele iniciou **selecionando o elemento do mapa** e, em seguida, adicionou o campo **`País`** em **`Localização`**;

- Como o objetivo era identificar a **média de valor de venda**, o professor inseriu o campo **`Total_Vendas`** em **`Tamanho da bolha`** e alterou a agregação para **média**. Dessa forma, cada bolha passou a representar a média de vendas por país;

- Por fim, como a pergunta pedia apenas para exibir **os países com maior média**, o professor aplicou **filtros** para destacar esses casos (procedimento que foi aprofundado na **aula seguinte**).

---

### Aulas - Aplicando Filtros e Segmentações de Dados

- Utilizando o **mapa** desenvolvido na aula anterior, foi necessário **destacar apenas os países com as maiores médias de valor de venda**. Para isso, o professor criou um **filtro** no Power BI;

- Ele destacou que, quando o enunciado **não especifica um valor limite**, é o **analista** quem define esse parâmetro, por exemplo, **“médias acima de 250”**. Assim, o professor acessou a seção de **`Filtros`**, clicou na **setinha** ao lado da opção **`Média de Total_Vendas`**, selecionou a condição **“é maior que”** e inseriu o valor **250**. Em seguida, aplicou o filtro para exibir apenas os países que atendiam a esse critério 

- Por fim, ele recomendou **renomear o título do gráfico** para algo mais descritivo, como **“Países com Maior Média de Valor de Venda (acima de 250)”**, de modo que o **usuário entenda claramente** que o filtro está sendo aplicado;

- Na aula seguinte, ele demonstrou como aplicar filtros no próprio dashboard, para que o usuário possa escolher de forma clara. Como fazer isso? A partir do elemento visual chamado de `Segmentação de Dados`, que na prática é a aplicação de filtros por meio de colunas/campos que serão disponibilizados no seu dashboard;

- Como pedido no roteiro, é preciso dar ao usuário a possibilidade de filtrar os dados **por ano, por segmento e por país**. Portanto, ele começou selecionando o elemento `Segmentação de Dados` e adicionando o campo `País`. Pronto, ele fez o primeiro filtro prático;

- Em seguida, ele fez esse mesmo processo, mas adicionando outros dois elementos de `Segmentação de Dados`, com o objetivo de fazer um filtro contendo o campo `Segmento` e outro para `Data_Pedido` (para este, em específico, ele foi neste campo, mas clicou em `Hierarquia de Datas` e adicionou apenas o campo `Ano`).

---

## Uso dos Cartões e Gráficos

- **Quando usar um cartão?**  
  
    Utiliza-se o **cartão** quando se deseja **exibir apenas uma métrica**, ou seja, um único valor numérico (como total de vendas, média, ou lucro total).

- **Quando usar um gráfico de pizza?**  

    O **gráfico de pizza** é indicado quando se deseja **comparar duas informações**, por exemplo, a **quantidade de vendas por categoria**. Usado também quando **há poucas categorias** envolvidas (geralmente até três).

- **Quando usar um gráfico de barras empilhadas?**  
  
    O **gráfico de barras empilhadas** é apropriado quando se deseja **analisar três informações simultaneamente**, permitindo visualizar **como cada parte contribui para o total** dentro de diferentes categorias (por exemplo, **vendas por país e prioridade de entrega**).

---

## Unidade 3: Modelagem, Relacionamentos e DAX

### O que é Modelagem de Dados?

- É o processo de criar uma **representação visual**, ou esquema, que define os sistemas de coleta e gerenciamento de informações de qualquer organização;

- Esse "blueprint" ou modelo de dados ajuda diferentes partes interessadas, como Analistas de Dados, Cientistas de Dados, Arquitetos e Engenheiros de Dados, a criar uma visão unificada dos dados da organização;

- O modelo **descreve quais dados a empresa coleta, a relação entre diferentes conjuntos de dados e os métodos** que serão usados para armazenar e analisar esses dados;

- De forma mais técnica, a Modelagem de Dados é o processo de criação de um **modelo conceitual, lógico e físico de dados**;

    - O modelo conceitual define os conceitos e as relações entre os dados. É mais uma compreensão dos dados;

    - O modelo lógico especifica como os dados serão armazenados e como as relações serão representadas em um banco de dados;

    - O modelo físico descreve como os dados serão armazenados em um sistema de armazenamento específico.

- **Observação:** O Power BI simplifica de forma significativa esse processo criando um modelo de dados básico, ele também evita que erros de relacionamentos ocorram se os dados não estiverem organizados corretamente, porém, ele não criará os relacionamentos entre os dados se os dados não estiverem corretamente conectados. É trabalho do analista averiguar isso.

#### Como Aplicamos Modelagem de Dados em BI?

- É válido lembrar que **BI não é ferramenta, mas sim uma Inteligência de Negócios**, que combina análise de negócios, mineração de dados, visualização de dados, ferramentas/infraestrutura de dados e práticas recomendadas para ajudar as organizações a tomar decisões impulsionadas por dados;

- O **foco em BI é analisar o passado** compreendendo métricas, indicadores, padrões e relacionamentos. O objetivo maior é a **análise descritiva** do que aconteceu;

- BI faz parte do universo da **Ciência de Dados**, mas a Data Science tem foco maior em **análise preditiva**, a fim de compreender o que pode acontecer;

- A Modelagem de Dados é uma parte importante no processo de BI, ela ajuda a garantir que os dados sejam armazenados de forma organizada e consistente, o que facilita a recuperação e análise de dados. **Algumas das maneiras como ela pode ser usada em BI incluem:**

    - **Criação de um Data Warehouse (DW):** A modelagem de Dados é usada para criar um DW, que é um repositório centralizado de dados de negócios que é usado para suportar a análise e tomada de decisão;

    - **Design de Cubos Multidimensionais:** A modelagem é usada para projetar esses cubos, que são estruturas de dados que ajudam a agregar e analisar dados de várias fontes;

    - **Criação de Modelos Estrela (Star Schema):** A modelagem de Dados Estrela é uma técnica comumente aplicada para projetar DWs, que ajuda a garantir a consistência e a facilidade de acesso aos dados;

    - **Otimização de Consultas:** A modelagem também é utilizada para otimizar as consultas a um DW, garantindo que as consultas sejam executadas de forma eficiente;

    - **Integração de Dados:** A modelagem permite integrar dados de várias fontes, garantindo a consistência e a qualidade dos dados;

    - **Governança de Dados:** A modelagem também é importante para garantir a qualidade dos dados e para implementar medidas de governança de dados, como rastreamento de alterações e auditoria.

#### Quais os Benefícios da Modelagem de Dados no Power BI?

- O Power BI tem 3 painéis principais: o painel de relatórios, o painel de dados e o de modelagem de dados;

- Alguns dos benefícios:

    - **Importação de Dados:** O Power BI permite importar dados de uma variedade de fontes, como banco de dados, arquivos e serviços na nuvem. A modelagem é usada para preparar os dados importados, garantindo que eles estejam em um formato consistente e estruturado para análise;

    - **Criação de Tabelas e Relações:** A modelagem é aplicada para criar tabelas e estabelecer relações entre elas, garantindo que os dados estejam organizados de forma lógica e coerente;

    - **Medidas e Cálculos:** O Power BI permite criar medidas e cálculos personalizados como somas, médias e percentuais. A modelagem é aplicada para garantir que esses cálculos sejam aplicados de forma consistente e correta;

    - **Filtros e Segmentação:** A modelagem é utilizada para criar filtros e segmentações para os relatórios, permitindo que os usuários explorem os dados de forma mais precisa e detalhada;

    - **Publicação de Relatórios e Dashboards:** O Power BI permite publicar relatórios e dashboards baseados na modelagem, para que os usuários possam acessá-los e explorá-los facilmente.

- **Observações:**

    - Compreenda o que são relacionamentos de negócio, por exemplo: cada produto pode estar associado a mais de uma venda; e estabeleça o relacionamento no Power BI;

    - Observe os relacionamentos entre os dados e considere desmembrar uma única planilha ou tabela em diferentes partes para construir o relacionamento adequado;

    - Faça os ajustes e correções nos dados para estabelecer os relacionamentos.

---

## Laboratório Prático 2: Dashboard de Vendas, Custo e Margem de Lucro e KPI

### Aulas - Carregando os Datasets, "Será que esse Gráfico está Correto?" e Removendo Duplicatas nos Dados

- Nas bases fornecidas, localizadas na pasta `chapter3/datasets`, ao serem carregadas para a ferramenta, foram constatados alguns erros, como a ausência dos nomes das colunas. Para corrigir, foi necessário apenas aplicar o comando que define a primeira linha como cabeçalho;

- O Power BI reconheceu automaticamente o relacionamento entre as tabelas `Clientes` e `Vendas`, mas não entre as demais, o que indica a existência de algum erro na modelagem (que não é responsabilidade da ferramenta fazer).

---

### Aulas - Modelagem de Dados e Verificando os Relacionamentos

- Para corrigir o problema, foi necessário criar manualmente uma nova relação, já que ela não foi identificada automaticamente. No entanto, ao tentar estabelecer a relação entre as tabelas `Produtos` e `Vendas` por meio do campo `ID Produto`, com a cardinalidade `1:*`, a operação não foi concluída devido a inconsistências nos dados, embora a ferramenta não informe exatamente qual é o erro;

- Diante disso, o professor acessou a seção **Transformar dados** e iniciou uma análise exploratória. Na tabela `Produtos`, foi possível observar a existência de IDs duplicados já nas duas primeiras linhas. Mas, **e se não fosse algo tão evidente? Como identificaríamos registros duplicados?**  

    - Basta clicar com o botão direito sobre a coluna desejada e selecionar **Agrupar por**. Em seguida, realiza-se a contagem das ocorrências, o que permite verificar quantas vezes cada valor aparece. No caso da coluna `ID Produto`, o esperado seria que cada ID aparecesse apenas uma vez, o que não ocorreu.

- **Como remover os dados duplicados?**  

    - O professor utilizou o ícone de tabela que aparece ao lado da coluna de índice. Nesse menu, há diversas opções, entre elas **Remover duplicatas**, que foi aplicada à coluna para eliminar registros repetidos. O mesmo procedimento foi realizado na tabela `Pedidos`;
    
    - Além disso, ainda na tabela `Pedidos`, foi utilizada a opção **Transformar → Cortar**, acessada pelo botão direito sobre a coluna `ID Pedido`, a fim de remover espaços em branco extras presentes nos dados. Apesar do problema mesmo ser os dados duplicados, ele quis demonstrar outra forma de limpeza.

- Após a limpeza dos dados, bastou utilizar a opção **"Detecção automática"**, e as novas relações foram identificadas corretamente pela ferramenta.

---

### Aulas - Relacionamentos e Cardinalidades

- Os relacionamentos entre tabelas representam as **regras de negócio** que definem como os dados se conectam, determinando também a **cardinalidade** (`1:1`, `1:*`, `*:1`, `*:*`) de cada vínculo. Essas cardinalidades expressam o **nível de granularidade** das relações, indicando quantos registros de uma tabela podem se associar a registros de outra;

- Por exemplo, “um pedido pode estar associado a várias vendas”. Nesse caso, a cardinalidade é `1:*`, partindo de `Pedidos` para `Vendas`, pois na tabela `Pedidos` cada `ID Pedido` aparece apenas uma vez, enquanto na tabela `Vendas` esse mesmo identificador pode se repetir em múltiplos registros;

- No caso da tabela `Produtos`, que também possui um relacionamento `1:*` com a de `Vendas`, pode-se interpretar da seguinte forma: “um produto pode participar de uma ou mais vendas”. Se a leitura fosse feita a partir da tabela `Vendas`, então seria: “muitas vendas podem estar associadas a um único produto”;

- Já a cardinalidade `1:1` representa um relacionamento **um para um**, em que **cada registro de uma tabela está vinculado a, no máximo, um registro da outra**. Esse tipo de relação é comum quando os dados foram separados por motivos de organização, desempenho ou segurança;
  
    - Por exemplo, em um sistema de clientes, pode haver uma tabela `Clientes` e outra `EnderecosDetalhados`, onde cada cliente possui exatamente um endereço cadastrado, e cada endereço pertence a apenas um cliente.

- Em relação a `*:*`, que representa um relacionamento **muitos para muitos**, digamos que temos 2 tabelas: `Cidades` e `Vendas`, **daria para ter esse relacionamento de muitos para muitos?** Sim, pois muitas vendas são feitas em muitas cidades, uma mesma venda pode estar associada a mais de uma cidade. Isso causa alguns problemas, o ideal, quando identifica-se um caso de `*:*` é criar uma tabela intermediária entre essas outras duas e, assim, deixar a cardinalidade entre elas como `1:*`. No caso do exemplo seria uma tabela intermediária chamada `Estado`.

---

### Aulas - Power Query M Language x DAX

- O **Power Query** utiliza a linguagem **M**. Assim, ao clicar em uma das etapas da seção **Transformar dados**, é possível visualizar o código correspondente às transformações realizadas, ou seja, ver internamente o que foi executado pela ferramenta.

- Dominar a linguagem **M** permite **personalizar e automatizar** processos no Power Query, elevando o nível de uso da ferramenta para um patamar mais avançado.

#### Diferença entre M e DAX

- A linguagem **M** é usada na etapa de **pré-processamento dos dados**, ou seja, na **extração, transformação e carga (ETL)**. Com ela, você realiza tarefas como:
    
    - Limpar e transformar dados;
    
    - Combinar ou mesclar tabelas;
    
    - Criar colunas calculadas baseadas em regras fixas;
    
    - Ajustar o formato ou o tipo dos dados antes de carregá-los para o modelo.

- Já a linguagem **DAX (Data Analysis Expressions)** é utilizada **depois que os dados já estão carregados no modelo**, para criar **cálculos dinâmicos e análises**. Com DAX, você pode:

    - Criar **medidas** e **colunas calculadas**;

    - Definir **agregações condicionais**;

    - Trabalhar com **contextos de filtro** e **tempo (time intelligence)**, como comparar vendas entre períodos.

#### Medidas

- São funções semelhantes às utilizadas no Excel, criadas para realizar **cálculos e análises dinâmicas** dentro do modelo de dados. Elas são escritas em **DAX** e permitem calcular métricas específicas, como totais, médias, percentuais e outros indicadores que se atualizam automaticamente conforme os filtros e segmentações aplicados no relatório;

- É necessário conhecer as **funções DAX**.

---

### Aula - Gráfico de Cascata e Primeira Questão do Lab 2

- Para responder à pergunta **“Qual foi o total de valor de venda considerando cada modo de envio dos pedidos?”**, utilizou-se o **gráfico de cascata**, conforme indicado pelo próprio enunciado. Esse tipo de gráfico é particularmente útil quando se trabalha com **poucas categorias** em uma variável, pois facilita a visualização do **impacto de cada categoria sobre o total final**;

- Como o objetivo era analisar o campo `Modo de Envio` dos `Pedidos`, esse campo foi inserido em **Categoria**, enquanto o campo `Total de Valor Venda` foi adicionado ao **Eixo Y**;

- **Gráfico de Cascata:**  

    - Esse tipo de gráfico mostra o **impacto incremental de cada categoria** em relação ao total. As barras representam aumentos ou diminuições no valor acumulado:

    - **Aumentar (Increase):** indica um acréscimo em relação ao total anterior;

    - **Diminuir (Decrease):** indica uma redução;  

    - **Total:** mostra o valor acumulado final após todas as variações;

    - No caso analisado, observa-se que cada modo de envio **aumenta progressivamente o total de vendas**, sem haver reduções. A **Classe Padrão** foi a que mais contribuiu, **acrescentando cerca de R$ 7,6 milhões** ao total de vendas, seguida pela **Segunda Classe** e pela **Primeira Classe**, até atingir o valor acumulado de aproximadamente **R$ 12,6 milhões**;

    - **Observação:** As **categorias/classes** exibidas no gráfico de cascata não são criadas automaticamente pelo gráfico. Elas derivam de um **campo categórico do conjunto de dados** selecionado para o eixo do gráfico. No caso apresentado, o campo utilizado foi `Modo de envio`, cujos valores distintos originam as classes como *Classe Padrão*, *Segunda Classe*, *Primeira Classe* e *Entrega no mesmo dia*;
    - O gráfico de cascata, portanto, **não define as categorias**, mas sim as utiliza para **demonstrar o impacto individual de cada uma sobre o total acumulado**, indicando visualmente quanto cada classe **aumenta ou diminui** o valor total.

---

### Aula - Gráfico de Treemap e Segunda Questão do Lab 2

- O **gráfico de Treemap** é ideal para representar comparações entre categorias quando o número de grupos não é muito grande (em torno de 10 a 15);

- Na segunda questão: **“Quais mercados tiveram o maior custo médio de envio dos produtos vendidos?”**, o procedimento foi o seguinte:  

    1. Inseriu-se o visual de **Treemap** no relatório;  

    2. Em **Categoria**, foi adicionado o campo `Mercado` da tabela **Clientes**;  

    3. Em **Valores**, foi adicionado o campo `Custo de venda` da tabela **Vendas**.

- Com essas configurações, o Power BI gera automaticamente um **Treemap** que permite visualizar, de forma hierárquica e proporcional, quais mercados apresentaram os maiores custos médios de envio dos produtos vendidos. Na formatação, adicionou-se rótulos de dados, para exbir os valores.

---

### Aula - Criando Indicador Chave de Performance (KPI) e Terceira Questão do Lab 2

- A terceira questão propõe: **"A empresa tem como objetivo (meta) manter uma média de 350 para o valor de venda todos os meses. Mostre um indicador (KPI) com o valor médio de venda. A empresa ficou abaixo ou acima da meta no mês de Abril/2014?"**

- O desenvolvimento foi realizado da seguinte forma:

    1. Primeiramente, inseriu-se o visual de **Indicador (KPI)** no relatório;
  
    2. Como a medida solicitada é a **média do valor de vendas**, foi adicionado o campo `Valor Venda` da tabela **Vendas** na área de **Valores**;
  
    3. Em seguida, foi necessário definir uma **linha de meta** para comparar o desempenho com o objetivo proposto.  
        
        - No painel **Formatar visual**, acessou-se a seção **Eixo do medidor**;  
    
        - Definiu-se o valor **mínimo** como `0`, o **máximo** como `500`, e o **Destino (meta)** como `350`, conforme indicado na questão;  

    4. Para que a análise fosse feita especificamente para **abril de 2014**, foi adicionada uma **Segmentação de dados**:  
    
        - Utilizou-se o campo `Data pedido` da tabela **Pedidos**;  
    
        - Selecionou-se a **hierarquia de data** (ano e mês) para permitir o filtro por períodos específicos;  

    5. Após aplicar o filtro para **abril/2014**, observou-se que o valor médio de venda ficou **abaixo da meta**, indicando que a empresa **não atingiu o objetivo estabelecido** para aquele mês.

---

### Aula - Coluna Calculada para o Lucro e Quarta Questão do Lab 2

- A quarta questão propõe: **"Considere que o lucro é equivalente a: valor venda - custo envio. Qual categoria de produto apresentou maior lucro médio?"**

- O desenvolvimento foi realizado da seguinte forma:

    1. Inicialmente, verificou-se que a tabela **Vendas** não possuía uma coluna chamada `Lucro`. Assim, foi necessário **criar uma nova coluna (calculada)** que representasse o lucro de cada venda.  
    
        - Para isso, utilizou-se a opção **Nova Coluna** no Power BI;  
    
        - Em seguida, foi adicionada a expressão: 

        ```DAX
        Lucro = Vendas[Valor Venda] - Vendas[Custo Envio]
        ```
        - Essa fórmula subtrai o custo de envio do valor de venda, resultando no lucro por transação individual.

    2. Após a criação da coluna, inseriu-se um **gráfico de rosca** para visualizar qual categoria apresentou maior lucro médio.  

        - No campo **Legenda**, adicionou-se `Categoria` (presente na tabela `Produtos`); 

        - No campo **Valores**, adicionou-se a nova coluna `Lucro`;  

        - O Power BI então calculou automaticamente a média dos lucros por categoria, permitindo identificar visualmente qual delas apresentou o melhor desempenho.

- Dessa forma, o gráfico de rosca passou a representar de forma clara **a distribuição do lucro médio por categoria de produto**, conforme solicitado na questão.

---

### Aula - Calculando a Margem de Lucro Usando DAX e Quinta Questão do Lab 2

- A questão proposta foi: **"Qual foi o comportamento da margem de lucro ao longo do tempo? Considere a margem de lucro como o lucro dividido pelo valor de venda."**

- Na tabela `Vendas`, temos as colunas `Valor Venda` e `Lucro`, mas ainda não existe a coluna que representa a **margem de lucro**. Para criá-la, foi necessário adicionar uma **nova coluna calculada** seguindo os passos abaixo:

    1. Selecionar a tabela `Vendas` e clicar em **Nova Coluna**;

    2. Inserir a seguinte expressão DAX:

   ```DAX
        MargemLucro = ROUND(DIVIDE(Vendas[Lucro], Vendas[Valor Venda]) * 100, 2)
    ```
    - A função `ROUND` arredonda o valor para duas casas decimais.

    3. Após criar a coluna, foi inserido um **gráfico de linhas**, utilizando a hierarquia completa do campo `Data Pedido` no `eixo X` e a nova coluna `MargemLucro` no `eixo Y`.Dessa forma, tornou-se possível visualizar o comportamento da margem de lucro ao longo do tempo.

---

## Unidade 4: Power BI para Análise de Dados de Marketing

- **O que é marketing?** A unidade começa esclarecendo esse conceito, definido como o processo de **planejar e executar a concepção, o preço, a promoção e a distribuição de ideias, bens e serviços** com o objetivo de criar **trocas que satisfaçam tanto os objetivos individuais quanto os organizacionais**. O marketing é responsável por **atrair e manter clientes**, envolvendo atividades como **pesquisa de mercado**, **análise de concorrência**, **definição de estratégias** e **planejamento de campanhas publicitárias**.

### Principais KPIs de Marketing

- Existem muitos indicadores de marketing que as empresas podem usar para medir o sucesso de suas estratégias e campanhas, como:

    - **Taxa de conversação:** A proporção de visitantes do site que realizam uma ação desejada, como comprar um produto ou preencher um formulário de contato;

    - **Taxa de retenção do cliente:** A proporção de clientes que compram de uma empresa novamente;

    - **Custo por aquisição de cliente (CAC):** O custo total de adquirir um novo cliente, incluindo despesas com publicidade e marketing;

    - **Retorno sobre investimento (ROI):** O lucro ou prejuízo obtido em relação ao investimento feito em uma campanha de marketing;

    - **Conscientização da marca:** A medida da familiaridade e reconhecimento da marca entre o público-alvo;

    - **Engajamento:** A medida da interação dos usuários com conteúdo, campanhas e canais de marketing;

    - **Net Promoter Score (NPS):** Uma medida da lealdade dos clientes, baseada em sua disposição para recomendar uma empresa ou produto para outras pessoas;

    - **Tráfego do website:** Número de visitas no website.

---

### Mini-Projeto 1: Análise de Campanhas de Marketing

- O **objetivo** é colocar o aluno em um cenário de negócio real, semelhante ao que será encontrado no mercado de trabalho;

- Nesse ambiente, desenvolveremos muito mais do que a criação de gráficos: realizaremos análises, responderemos a perguntas de negócio, observaremos os dados sob diferentes perspectivas, corrigiremos inconsistências, calcularemos métricas e extrairemos insights para apoiar os tomadores de decisão;

- **O mini-projeto foi dividido em 4 etapas/visões:**

    1. **Visão do Cliente** (ex: "Qual a média salarial dos clientes?"; "E o grau de escolaridade?"; "Como estão divididos em termos de estado civil?"; "Os clientes têm criança em casa/adolescente?"...);

    2. **Visão do Comportamento de Compra do Cliente** (ex: "Se o cliente é solteiro ou casado, isso influencia no padrão de compra?");

    3. **Visão da Performance das Campanhas de Marketing** (ex: "A empresa fez 5 campanhas de marketing, qual delas obteve o maior retorno?"; "Considerando as campanhas de marketing, teve diferença se por acaso o cliente era casado ou solteiro?"; "Considerando as campanhas de marketing, quanto tempo foi necessário para que o cliente realmente fizesse a compra?");

    4. **Visão dos Padrões de Compra no Ponto de Venda - País**, neste caso (ex: "Aonde o produto foi vendido?"; "Aonde está a empresa que vendeu o produto? Isso faz diferença?"; "Qual foi a performance dos pontos de venda?").

- Para a elaboração deste projeto, foi disponibilizada uma base de dados de marketing, a qual foi carregada na ferramenta. Em seguida, iniciou-se o processo de **exploração dos dados**, isto é, o reconhecimento da base para compreender a tabela e identificar o que poderá ser analisado;

    - O professor destacou que, nesse momento de exploração, um recurso de grande auxílio é o **dicionário de dados**, ou seja, um documento que descreve cada coluna de um determinado conjunto de dados;

    - Mas quem é responsável por criar esse dicionário? Geralmente, quem gerou os dados, pois é quem possui essas informações. Contudo, no mundo real, nem sempre se tem a disponibilização/produção desse documento, então cabe ao analista compreender cada campo. Se não souber, procure o departamento de negócio e questione, ou busque na internet;

    - O campo **"Dias desde a última compra"** possui um nome especial: **recência**, que indica o tempo decorrido desde a última aquisição;

    - Os campos **"Compra na Campanha 1"**, **"Compra na Campanha 2"**, **"Compra na Campanha 3"**, **"Compra na Campanha 4"** e **"Compra na Campanha 5"** são colunas binárias que indicam se, a partir de cada disparo de campanha, houve ou não a realização de uma compra.

- Como neste projeto foi solicitada a incrementação de 4 visões, aplicou-se o recurso de paginação, para que não fique poluído. Portanto, criou-se uma página para cada visão.

---

#### Visão Cliente

- Nesta visão, o professor iniciou a análise com a pergunta: **"Quantos clientes há neste conjunto de dados?"**  

    - Como essa informação ainda não havia sido verificada, ele inseriu um **cartão** no Power BI e adicionou o campo `ID`, obtendo como resultado **2.000 clientes**.

- Em seguida, questionou: **"Qual é a média salarial dos clientes?"**  
  
    - Para descobrir, adicionou outro **cartão** e selecionou o campo `Salário Anual`, resultando em uma **média salarial de R$ 52.290,00**.

- Depois, ele buscou entender **em quais canais de compra os clientes mais adquiriram produtos**, perguntando: **"Os clientes compraram mais na loja física, pela web, via catálogo ou por meio de descontos?"**  

    - Assim, foram criados cartões individuais para os campos:

        - `Número de Compras na Loja`

        - `Número de Compras na Web`

        - `Número de Compras via Catálogo`

        - `Número de Compras com Desconto`

    - Ao comparar os valores, observou-se que **as compras na loja física apresentaram o maior volume (12.000)**, enquanto **as compras com desconto tiveram o menor número (4.665)**.

- **Alguns dos insights obtidos:**

    - Total de clientes: **2.000**;

    - Média salarial - anual: **R$ 52.290,00**;

    - Canal com maior número de compras: **Loja física (12.000)**;

    - Canal com menor número de compras: **Compras com desconto (4.665)**.

- Após realizar as análises iniciais, o professor comentou que gostaria de **conhecer melhor o perfil dos clientes** com base em seu **grau de escolaridade**. Para isso, ele adicionou um **gráfico de barras** no Power BI, configurando:

    - **Eixo X:** `Escolaridade`;

    - **Eixo Y:** `ID`.

- Dessa forma, foi possível visualizar o **número de clientes em cada nível de escolaridade**;

- Em seguida, o professor criou **outro gráfico de barras**, desta vez para analisar os clientes conforme o **estado civil**. Ele configurou:
  
    - **Eixo X:** `Estado Civil`;

    - **Eixo Y:** `ID`.

- Assim, tornou-se possível observar **quantos clientes pertencem a cada categoria de estado civil**;

- Por fim, ele adicionou uma **segmentação de dados** utilizando o campo `País`, possibilitando **filtrar os gráficos de acordo com o país selecionado**, tornando a análise mais dinâmica e direcionada;

- Após a criação de todos os **gráficos e cartões**, o professor aplicou uma **formatação geral** à página para melhorar a **apresentação visual e a leitura dos dados**. Foram ajustados elementos como **cores, tamanhos de fonte, alinhamento e títulos** dos visuais;

- **Observação:** nos **cartões**, é possível **renomear o título** para um nome mais claro e legível, facilitando a compreensão das informações.

---

#### Visão Comportamento

- Para esta nova etapa da análise, foi criada uma **nova página no relatório** denominada `Visão Comportamento`;

- Nessa visão, o professor iniciou adicionando um **gráfico de dispersão**, utilizado para **análises bivariadas**, ou seja, aquelas que envolvem **duas variáveis**. Os campos selecionados foram:

    - **Eixo X:** `Salário Anual` *(com a opção “Não resumir” habilitada)*;

    - **Eixo Y:** `Gasto com Alimentos`  

- Após a configuração, ele questionou: **"O que podemos interpretar a partir deste gráfico?"** A conclusão foi que **à medida que o salário anual aumenta, o gasto com alimentos também tende a crescer**;

- Durante a observação do gráfico, notou-se a presença de **um ponto fora do padrão** (“desgarrado”), o que indicava um **outlier** na variável `Salário Anual`. Esses valores extremos podem **distorcer as análises e a visualização dos dados**. Diante disso, o professor explicou duas alternativas:

    1. **Manter o outlier**, mas **ajustar a visualização**:  
    
    - No eixo X, ativar a opção **“Escala logarítmica”**, o que redistribui melhor os valores e suaviza o impacto do ponto fora da curva;

  2. **Remover o outlier**:  
    
    - Acessar a guia **Transformar dados**;  
    
    - Selecionar o campo `Salário Anual`;  
    
    - Clicar na **setinha** ao lado do nome do campo e escolher **“Classificar em ordem decrescente”**, para que o salário mais alto apareça primeiro;  
    
    - Em seguida, ir em **“Remover linhas” → “Remover linhas superiores”** e remover **a primeira linha** (correspondente ao valor extremo).  

- Após esse procedimento, o conjunto de dados fica **livre do outlier**, permitindo uma visualização mais limpa e precisa;

- Além disso, ao examinar a base de dados, observou-se que existem **diversos tipos de gastos** registrados: `Gasto com Alimentos`, `Gasto com Brinquedos`, `Gasto com Eletrônicos`, `Gasto com Móveis`, `Gasto com Utilidades` e `Gasto com Vestuário`. Diante disso, o professor destacou que **não seria eficiente criar um gráfico de dispersão para cada tipo de gasto**;

- Assim, foi proposta uma **abordagem mais prática de análise**: criar uma **medida personalizada** que representasse o **total de gastos por cliente**, somando todos esses campos. Como o conjunto de dados **não possuía uma coluna específica para o gasto total**, foi criada uma **Nova Medida** no Power BI com a seguinte fórmula DAX:

```DAX
    TotalGasto =
        SUMX(
            DadosMarketing,
            DadosMarketing[Gasto com Alimentos] +
            DadosMarketing[Gasto com Brinquedos] +
            DadosMarketing[Gasto com Eletronicos] +
            DadosMarketing[Gasto com Moveis] +
            DadosMarketing[Gasto com Utilidades] +
            DadosMarketing[Gasto com Vestuario]
        )
```

- Após criar a medida `TotalGasto`, o professor substituiu o campo `Gasto com Alimentos` do eixo Y no gráfico de dispersão por `TotalGasto`;

- Dessa forma, o gráfico passou a representar o gasto total de cada cliente em relação ao seu salário anual, fornecendo uma visão mais ampla e consolidada do comportamento de consumo;

- Em seguida, o professor levantou a questão: **"Será que existe uma relação entre o gasto total e o número de filhos?"**. Embora a resposta pareça intuitiva, ele ressaltou a importância de **demonstrar essa relação com base nos dados**;

- Ao observar a base, verificou-se a presença dos campos `Filhos em casa` e `Adolescentes em casa`, além da medida criada anteriormente, `TotalGasto`. Nesse ponto, surgiu a dúvida: **Qual seria o gráfico mais adequado para essa análise?**;

- O professor explicou que o **gráfico de dispersão** não seria apropriado neste caso, pois ele é indicado para **variáveis numéricas contínuas**, aquelas que podem assumir uma grande variedade de valores dentro de um intervalo (como salário, altura, temperatura etc). Já os campos `Filhos em casa` e `Adolescentes em casa` são **variáveis numéricas discretas**, ou seja, representam **quantidades específicas** (0, 1, 2, 3) e não uma medida contínua. Assim, o gráfico de dispersão não seria eficaz para representar esses dados;

- Diante disso, optou-se pelo **gráfico de barras**, configurado da seguinte forma:

    - **Eixo X:** `Filhos em casa` (depois fez com `Adolescentes em casa`);

    - **Eixo Y:** `TotalGasto`.

- O gráfico resultante mostrou que **clientes sem filhos tendem a gastar significativamente mais**. Ao refletir sobre o motivo, o professor destacou que a **análise de contexto** é essencial: o **estado civil predominante entre os clientes é o de solteiro**, e a maioria deles **não possui filhos**. Dessa forma, **o maior gasto entre quem não tem filhos** reflete o **perfil predominante do público analisado**;

- Em seguida, o professor propôs **cruzar informações de três variáveis diferentes** para obter uma análise mais detalhada do comportamento dos clientes. O gráfico mais adequado para esse tipo de visualização é a **árvore hierárquica**, que permite **analisar uma métrica principal** e **explicá-la a partir de diferentes dimensões**;

- Nesse caso, a configuração foi feita da seguinte forma:

    - **Campo a analisar:** `TotalGasto`;

    - **Campos para explicar por:** `Escolaridade` e `Estado Civil`.

- Após configurar, basta clicar no ícone **“+”** que aparece na visualização da árvore hierárquica para **expandir os níveis de detalhamento** e explorar as relações entre as variáveis;

    - Por exemplo: ao expandir o campo `Estado Civil`, pode-se visualizar o grupo **Solteiro**, e ao aprofundar mais um nível, será exibido o **valor correspondente ao gasto total desse grupo por nível de escolaridade**, como identificar que **solteiros com curso superior** apresentam os **maiores valores de gasto**.

- A análise revelou que o **perfil de cliente solteiro e com curso superior** foi o que **apresentou o maior gasto total**, sendo, portanto, o grupo que **mais adquiriu produtos da empresa**;

- **Observação:** Enquanto na **Visão Cliente** as análises foram realizadas **com apenas uma variável por vez**, por exemplo, número de clientes, média salarial ou tipo de compra, na **Visão Comportamento** o foco passou a ser **a relação entre duas ou mais variáveis**, buscando compreender **como elas se comportam em conjunto** e **quais padrões ou correlações** podem ser identificados nos dados.

---

#### Visão da Performance das Campanhas

- Para analisar a **performance das campanhas de marketing**, observou-se que a base de dados contém diversas **colunas binarizadas** que indicam se o cliente **realizou ou não uma compra** em cada campanha, como: `Compra na Campanha 1`, `Compra na Campanha 2`, `Compra na Campanha 3`, e assim por diante. Além disso, há o campo `Comprou`, que mostra **se o cliente adquiriu algum produto em pelo menos uma campanha**;

- Para compreender a **efetividade geral das campanhas**, foi necessário **cruzar essas informações**. O primeiro passo foi verificar **quantas pessoas compraram e quantas não compraram**. Para isso, utilizou-se um **gráfico de pizza**, configurado da seguinte forma:

    - **Legenda:** `Comprou`;

    - **Valores:** `ID` (para representar a contagem de clientes)

- O gráfico revelou que **16% dos clientes responderam às campanhas de marketing**, realizando ao menos uma compra. Como o campo `Comprou` representa uma **categoria** (e não uma medida numérica), o professor acessou a opção **Transformar dados** e alterou o **tipo de dado de `Comprou` para Texto**, garantindo que fosse tratado corretamente como uma **variável categórica**;

- Em seguida, o professor levantou uma nova questão: **"Será que existe diferença na média salarial entre os clientes que compraram e os que não compraram durante as campanhas de marketing?"**

- Para investigar essa hipótese, foi inserido um **gráfico de barras**, configurado da seguinte forma:

    - **Eixo X:** `Comprou`;

    - **Eixo Y:** `Salário Anual` (modificado para exibir a **média** em vez da soma).

- O resultado mostrou que, na categoria **1** (clientes que compraram), a **média salarial é mais alta** do que na categoria **0** (clientes que não compraram). Essa diferença indica que **a renda média influencia o comportamento de compra** nas campanhas;

- A partir desse insight, o professor destacou a importância dessa informação para a **equipe de marketing**: em campanhas futuras, será essencial aplicar **segmentações de clientes**, por exemplo, filtrar o público **por faixa salarial** ou por outros critérios relevantes, a fim de **personalizar as estratégias** e **aumentar a efetividade** das ações. Dessa forma:

    - Clientes com **menor poder aquisitivo** podem receber **campanhas com foco em descontos**;
    
    - Já os clientes com **salário mais elevado** podem ser direcionados a **produtos de maior valor agregado**.

- Posteriormente, o professor propôs uma nova reflexão:  
  **"Será que o website da empresa contribuiu para o aumento das vendas durante as campanhas de marketing?"**;

- Para responder a essa pergunta, ele utilizou a ferramenta e **criou uma tabela**, configurada da seguinte forma:
  
    - Primeiramente, adicionou a coluna **`Comprou`**, para identificar se o cliente realizou ou não uma compra;  

    - Em seguida, incluiu a coluna **`Número de Visitas Website Mês`**, configurada para exibir a **soma** das visitas.

- A partir da tabela, foi possível gerar **insights importantes**: observou-se que **mais de 8 mil clientes acessaram o site, mas não efetuaram nenhuma compra**, enquanto **cerca de 1.700 realizaram a compra após a visita**. Isso indica que, embora o número de visitas tenha sido alto, a **taxa de conversão em vendas foi baixa**, evidenciando a necessidade de **revisar estratégias de marketing digital e usabilidade do site**;

- Ademais, o professor **converteu a visualização de tabela em uma matriz**, o que **organizou melhor as informações** e **facilitou a interpretação dos resultados**;

- Na aula seguinte, ainda trabalhando com a **matriz**, o professor aprimorou a análise ao **adicionar novas dimensões de segmentação**. Inicialmente, ele inseriu o campo **`Escolaridade`** em **Colunas**, fazendo com que a ferramenta passasse a **exibir os dados de acordo com o nível de escolaridade dos clientes**;

- Em seguida, acrescentou o campo **`Estado Civil`** em **Linhas**, criando assim uma **tabela cruzada**, pois passou a relacionar diferentes variáveis dentro da mesma visualização;

- Por último, adicionou o campo **`País`** também em **Linhas**, permitindo uma **análise ainda mais detalhada**, já que agora era possível observar os dados **por país, estado civil e escolaridade** simultaneamente;

- Os **valores exibidos** continuaram sendo representados pelo campo **`Número de Visitas Website Mês`** (soma). O professor ressaltou que é **preferível utilizar a matriz** em vez da tabela nesse tipo de caso, pois **a matriz permite navegação entre os níveis hierárquicos** e **facilita a exploração interativa dos dados**;

- Na aula seguinte, o professor propôs uma nova análise: **"Será que o fato de ter filhos em casa influenciou na efetividade das campanhas de marketing?"**;

- O objetivo era identificar:  

    - Entre as pessoas **que têm filhos em casa**, quantas **compraram** e quantas **não compraram**;  

    - E entre as que **não têm filhos**, quantas **compraram** e quantas **não compraram**.

- Para realizar essa análise, foi utilizado um **gráfico de barras**. Inicialmente, configurou-se da seguinte forma:  

    - **Eixo X:** `Filhos em casa`;  

    - **Eixo Y:** `Comprou`.

- No entanto, esse primeiro gráfico apenas **contava a ocorrência da variável `Comprou`**, sem oferecer o cruzamento desejado. Para corrigir isso, o professor **reorganizou os campos**:

    - **Eixo X:** `Filhos em casa`;

    - **Eixo Y:** contagem de `Filhos em casa`;

    - **Legenda:** `Comprou` (por ser uma variável categórica).

- Com essa configuração, o gráfico passou a exibir corretamente **quantas pessoas compraram ou não**, considerando se tinham ou não filhos em casa. Contudo, a presença dos valores **0** e **1** no campo `Comprou` dificultava a leitura dos resultados;

- Para tornar o gráfico mais claro, o professor acessou **Transformar dados**, selecionou o campo **`Comprou`** e substituiu os valores:  

    - **1 → “Sim”**;

    - **0 → “Não”**.

- Após essa modificação, a visualização ficou **muito mais legível**, permitindo compreender facilmente **a relação entre ter filhos e o comportamento de compra nas campanhas**.

---

#### Visão dos Padrões de Compra por Ponto de Venda

- Para esta visão, foram utilizados dois gráficos. O primeiro é o **gráfico de colunas agrupadas e linha**, que requer pelo menos três campos: eixo X, eixo Y da coluna e eixo Y da linha.  

- Nele, foram aplicados os seguintes campos: `País` no eixo X; no eixo Y da coluna, os campos relacionados aos gastos, como `Gasto com Alimentação`, `Gasto com Brinquedos`, entre outros, que são os valores exibidos no gráfico. Já no eixo Y da linha, foi adicionado o campo `ID` (contagem);

- **O que foi possível concluir com esse gráfico?**  

    - Ao observar a Espanha, nota-se que o maior gasto total é com eletrônicos. A linha indica que o país possui um total de **302 clientes**. Desse total, os clientes gastaram **94.282** com eletrônicos e **11.962** com utilidades, por exemplo. A mesma análise pode ser estendida aos demais países.

- O outro gráfico utilizado foi o **gráfico de linhas**, no qual o eixo Y recebeu o campo `TotalGasto`, a legenda foi composta pelo campo `País` e o eixo X representou o `Ano` proveniente do campo `Data Cadastro`;

- **O que foi possível analisar com esse?**  

    - Esse gráfico permitiu observar a **evolução do total gasto ao longo do tempo**, com cada linha representando um país;

    - Verifica-se que o comportamento entre os países é bastante semelhante: houve um **crescimento acentuado em 2020**, seguido por uma **queda em 2021** e uma **retomada do crescimento em 2022**. Algo que se deve, por exemplo, a pandemia que ocorreu nesse período.

---

## Unidade 5: Power BI para Análise de Dados Comerciais

- A **área comercial** de uma empresa é responsável por garantir a venda de produtos ou serviços da empresa e por conseguir novos clientes;

- Sendo assim, é o departamento responsável por estabelecer as **estratégias de vendas**, **realizar negociações**, **fechar contratos** e **acompanhar o desempenho das vendas**.

### Principais KPIs da Área Comercial

- São indicadores que medem o desempenho e a eficiência das atividades de vendas. Alguns dos mais usados:

    - **Volume de vendas:** quantidade de produtos ou serviços vendidos;

    - **Ticket médio:** valor médio das vendas por transação;

    - **Taxa de conversão:** proporção de visitantes do site ou contatos que se tornam clientes;

    - **Ciclo de vendas:** tempo médio que leva para fechar uma venda, desde o primeiro contato com o cliente até o fechamento;

    - **Retenção de clientes:** taxa de clientes que compram novamente após a primeira compra;

    - **Lucratividade:** receita líquida obtida pela venda de produtos ou serviços, descontados os custos;

    - **Produtividade da equipe de vendas:** quantidade de vendas realizadas por vendedor por período;

    - **Satisfação do cliente:** medida da satisfação dos clientes com a empresa, produtos e serviços oferecidos.

---

### Mini-Projeto 2: Dashboard Comercial - Performance de Vendas

- Antes de iniciar o projeto, o professor começou a unidade **explorando a base de dados fornecida**, a fim de se familiarizar com os campos disponíveis. Na coluna `Segmento`, por exemplo, ao clicar na seta de filtro, é possível visualizar os valores existentes: **Corporativo**, **Doméstico** e **Industrial**, que representam os três segmentos onde a empresa realiza suas vendas;

- Há também a coluna `Vendedor`, que contém o nome de cada profissional, e o campo `ID-Vendedor`, que identifica cada um de forma única;

- Em seguida, o professor abriu o **Power Query** (na opção **Transformar Dados**) para **verificar os tipos de dados** de cada coluna. Após a análise, constatou-se que todos estavam corretamente definidos;

- **Observação:** basta haver **uma letra** em uma célula para que o Power BI **classifique automaticamente a coluna como texto**, o que ocorre, por exemplo, com colunas de **códigos**;

- O próximo passo foi a **definição dos relatórios** que iriam compor o dashboard.  
  
  - Nesta parte, o professor indicou a criação de uma **página de índice**, que serviria como **página de navegação** para as demais páginas do dashboard, uma forma de tornar a navegação **mais fluida, clara e intuitiva**;

  - Ele também ressaltou a importância de **não sobrecarregar** uma única página com muitos gráficos:  
  
  > “Tente usar no máximo quatro elementos por página. Dependendo da finalidade, em algumas páginas apenas um gráfico ou mapa é suficiente para garantir uma leitura mais clara.”

- Para este dashboard, foram selecionados **quatro relatórios principais**:

    1. **Narrativa inteligente**;

    2. **Principais influenciadores de venda**;

    3. **Faixas de vendas por categoria e ponto de venda**; 
  
    4. **Performance dos vendedores por região**.

---

#### Relatório: Narrativa Inteligente

- Neste relatório, o professor iniciou explicando a construção do **gráfico de pizza**, que foi o primeiro elemento adicionado à página. Nele, foram utilizados os seguintes campos:

    - `Segmento` em **Legenda** (por ser uma variável categórica);  

    - `Valor Venda` em **Valores** (renomeado para `Total Valor Venda`).

- Em seguida, foi inserido o **gráfico de funil**, configurado da seguinte forma:

    - `Categoria` em **Categoria**;  

    - `Valor Venda` em **Valores** (também renomeado para `Total Valor Venda`),
  
- Esse tipo de visualização é indicado **quando há poucas categorias**, o que se aplica ao caso, já que havia apenas quatro;

- Outro elemento incluído foi o **gráfico de colunas clusterizado**, configurado com:

    - `Fabricante` em **Eixo X**;  

    - `Valor Venda` em **Eixo Y** (renomeado para `Total Valor Venda`);

- O **gráfico de barras/colunas** é o mais indicado **quando se tem muitas categorias**, o que o torna ideal neste contexto, já que havia diversos fabricantes (como *Electrolux*, *Sony*, *LG*, *Samsung*, *Dell*, entre outros). Durante a **formatação**, foram **removidos os títulos dos eixos**, pois o **título do gráfico: “Total Valor Venda por Fabricante”** já deixa o conteúdo claro;

- Por último, o professor apresentou um recurso bastante interessante do Power BI: a **Narrativa Inteligente**. Esse recurso, representado por um ícone específico na ferramenta, gera **um resumo automático** com base nos dados e visualizações presentes no relatório, destacando **os principais insights identificados**;

- A **Narrativa Inteligente** é especialmente útil para **analistas**, pois permite **resgatar e interpretar rapidamente conclusões relevantes** a partir das informações exibidas. Além disso, trata-se de um recurso **interativo**, ou seja, caso o usuário selecione outro gráfico ou realize um filtro, o texto da narrativa **é automaticamente atualizado** para refletir o novo contexto dos dados.

---

#### Relatório: Principais Influenciadores de Vendas

- Neste relatório, o professor inseriu **poucos elementos visuais**, mas suficientes para **responder perguntas estratégicas** sobre os fatores que influenciam o desempenho das vendas. Um dos questionamentos analisados foi: **“O que influencia o Valor de Venda a aumentar?”**; 

- Ao aplicar essa análise, observou-se que **quando o segmento é corporativo**, a **média do `Valor Venda` aumenta** significativamente. A partir desse insight, conclui-se que a empresa pode **direcionar mais esforços a esse segmento**, investindo em:

    - maior número de vendedores especializados;

    - ampliação do portfólio de produtos voltados ao público corporativo;

    - compreensão mais profunda das necessidades desse tipo de cliente.

- Para criar esse tipo de visual, foi utilizado o ícone **Principais Influenciadores** no Power BI, um recurso que realiza uma **análise automática dos fatores** que impactam uma métrica específica. No caso deste relatório:

    - O campo `Valor Venda` foi adicionado em **“Analisar”**;  

    - Os campos `Segmento` e `Categoria` foram inseridos em **“Explicar por”**.  

- Assim, o Power BI gerou automaticamente o **gráfico de principais influenciadores**, permitindo visualizar **quais variáveis contribuem para o aumento ou a redução** da média de vendas, de forma intuitiva e explicativa.

---

#### Relatório: Total de Venda por Categoria e Ponto de Venda (Gráfico de Faixas)

- Neste relatório, o professor utilizou o **gráfico de faixas**, um tipo de visual voltado para **comparar variações de vendas entre categorias** dentro de um mesmo ponto de venda, por exemplo. Esse gráfico é útil para **identificar aumentos ou reduções nas vendas** de uma categoria para outra, mas requer **cuidado na interpretação**, pois pode ser de **difícil compreensão** para a audiência caso o analista não conduza a leitura de forma clara;

- No gráfico foram adicionados os seguintes campos:  

    - `Categoria` no **Eixo X**;  

    - `Valor Venda` no **Eixo Y**;  

    - `Loja` em **Legenda**.  

- Ao interagir com o gráfico (por exemplo, passando o mouse sobre as faixas), é possível observar informações detalhadas.Exemplo: ao posicionar o cursor sobre o **primeiro e maior elemento**, o Power BI exibe:  

    - **Categoria:** Eletrodomésticos;  

    - **Loja:** SP8822;  

    - **Total de Valor Venda:** 40.542,44.  

- Ao mover o cursor dentro da mesma faixa e selecionar outro item, nota-se, por exemplo:  

    - **Categoria:** Celulares;  

    - **Loja:** SP8822;  

    - **Total de Valor Venda:** 36.912,00.  

- Ao clicar sobre a faixa (representada por tons de verde mais suave), a ferramenta mostra um **resumo completo** das categorias relacionadas àquela loja, incluindo a **diferença percentual ou absoluta entre os valores de venda**, o que permite visualizar **a queda ou o aumento de desempenho** entre as categorias no mesmo ponto de venda;

- Como esse tipo de gráfico pode gerar dúvidas no público, o professor recomenda **acrescentar uma nota explicativa** no relatório, destacando um exemplo de sequência interpretada. Além disso, sugeriu **habilitar o controle deslizante (scroll)** para **facilitar a navegação** entre os itens, tornando a visualização das faixas, especialmente as que estão mais próximas, mais intuitiva e organizada.

---

#### Relatório: Performance dos Vendedores por Região

- Para este relatório, foi utilizado um **mapa com filtros**. Semelhante ao relatório anterior, o professor optou por demonstrá-lo em apenas uma página, pois essa é a forma mais indicada de apresentar esses elementos, garantindo uma visualização mais limpa, objetiva e legível;

- Foram aplicados os seguintes campos: 

    - `Estado` em **localização**;
    
    - `Vendedor` em **legenda**;
    
    - `Valor Venda` em **tamanho da bolha** (posteriormente ajustado para `Total Valor Venda`).

- Além disso, foi adicionado um filtro em `Total Valor Venda` maior que **30.000**, com o objetivo de destacar apenas os estados que apresentaram volumes de vendas mais elevados.

---

#### Criando Menu/Índice para os Relatórios

- O professor recomendou a criação de um **índice (menu de navegação)** para facilitar o acesso entre as páginas dos relatórios, aproveitando a paginação de forma organizada e evitando a poluição visual da dashboard;

- Para criar o índice: **Inserir → Botões → Navigator → Navigator de Página**;

- A navegação entre as páginas ocorre utilizando **Ctrl + Clique**;

- Após inserir o menu, basta realizar as **formatações desejadas**, ajustando cores, tamanhos e posições conforme o estilo do relatório.

---

## Unidade 6: Power BI para Análise de Dados de RH

- **Qual a função da área de Recursos Humanos?** Gerenciar o capital humano da empresa, cuidando de todo o ciclo de vida do colaborador, desde o recrutamento e seleção até a demissão, além de administrar benefícios, folha de pagamento e garantir o cumprimento da legislação trabalhista, atuando como ponte entre os interesses da empresa e dos funcionários para promover um bom clima organizacional, engajamento e desenvolvimento profissional. 

### Principais KPIs na Área de RH

- São indicadores que ajudam a avaliar o sucesso da área:

    - **Taxa de rotatividade:** mede a frequência com que os funcionários estão deixando a empresa, o que pode indicar problemas com o ambiente de trabalho, remuneração ou oportunidades de desenvolvimento;

    - **Satisfação do funcionário:** mede o grau de satisfação dos funcionários com relação ao trabalho, remuneração, ambiente de trabalho e oportunidades de desenvolvimento;

    - **Tempo médio para preenchimento de vagas:** mede o tempo necessário para preencher uma vaga aberta, o que pode indicar a eficiência do processo de recrutamento e seleção;

    - **Custo de contratação por funcionário:** mede o custo total de contratar um novo funcionário, incluindo gastos com anúncios de vagas, entrevistas, testes e treinamento;

    - **Participação em treinamentos:** mede o número de funcionários que participam de programas de treinamento e desenvolvimento, o que pode indicar o interesse dos funcionários em melhorar suas habilidades e desenvolver suas carreiras;

    - **Avaliação de desempenho:** mede a avaliação do funcionário em um ciclo de trabalho, normalmente 6 ou 12 meses;

    - **Nível de absenteísmo:** mede a frequência com que os funcionários faltam ao trabalho, o que pode indicar problemas com o ambiente de trabalho ou saúde dos funcionários;

    - **Nível de engajamento:** escala que define quão engajados os funcionários estão, normalmente medida com base no nível de absenteísmo, pontualidade, avaliação de desempenho etc.

---

### Mini-Projeto 3: Análise de Dados de RH

- Antes de iniciar o projeto, o professor compartilhou o roteiro e pediu que cada aluno o realizasse de forma independente, sem auxílio. A seguir, descrevo os passos que segui durante o desenvolvimento (sem considerar a parte de formatação):

    - Primeiramente, realizei o **download da base de dados** e a **conectei ao Power BI**;

    - Em seguida, **examinei a base** e percebi que **não havia campos que necessitassem de limpeza ou transformação**, então segui direto para a criação do relatório;

    - Para a primeira questão: **"Qual o total de funcionários atualmente na empresa?"**, adicionei um **cartão** à tela e inseri o campo `Id_Funcionario` (contagem), obtendo automaticamente o total de funcionários;

    - Na segunda questão: **"Qual o tempo médio de experiência dos funcionários (em anos)?"**, adicionei outro **cartão** e utilizei o campo `Anos_Experiencia` (média);

    - Para a terceira questão: **"Qual o total e percentual de funcionários do gênero masculino e feminino?"**, criei algumas **medidas DAX**. Embora exista uma forma mais direta, optei por detalhar o processo criando medidas separadas para o total e o percentual de cada gênero. As medidas foram:

    ```dax

        Qtd_Masculino = CALCULATE(COUNTROWS(DatasetRH), DatasetRH[Genero] = "Masculino")
        Qtd_Feminino = CALCULATE(COUNTROWS(DatasetRH), DatasetRH[Genero] = "Feminino")
        Total_Funcionarios = COUNTROWS(DatasetRH)
        Pct_Masculino = DIVIDE([Qtd_Masculino], [Total_Funcionarios], 0) 
        Pct_Feminino = DIVIDE([Qtd_Feminino], [Total_Funcionarios], 0) 

    ```

    - Após criar as medidas, adicionei **cartões individuais** para exibir `Qtd_Masculino`, `Qtd_Feminino`, `Pct_Masculino` e `Pct_Feminino`;

    - Para a quarta questão: **"Qual a média salarial mensal?"**, criei outro **cartão** e utilizei o campo `Salario_Mensal` (média);

    - Na quinta questão: **"Qual o total de funcionários por função?"**, utilizei um **gráfico de barras empilhadas**, configurando `Funcao` no eixo Y e `Total_Funcionarios` no eixo X;

    - Na sexta questão: **"Qual o percentual de funcionários disponíveis para fazer hora extra?"**, antes de inserir o gráfico, acessei **Transformar Dados**, localizei a coluna `Disponivel_Hora_Extra` e substituí os valores **S → Sim** e **N → Não**, uma padronização que já deveria ter sido realizada no segundo passo, já que manter apenas “S” e “N” não é tão legível. Em seguida, adicionei um **gráfico de rosca**, utilizando:

        - **Legenda:** `Disponivel_Hora_Extra`;

        - **Valores:** `Total_Funcionarios`.

    - Na sétima questão: **"Qual o nível de envolvimento dos funcionários no trabalho considerando 4 categorias: Ruim, Baixo, Médio e Alto?"**, acessei a aba **Transformar Dados** e criei uma **coluna condicional** chamada `Categoria_Indice_Envolvimento`, definindo:

        - 1 → Ruim

        - 2 → Baixo 

        - 3 → Médio 

        - 4 → Alto  

    - Em seguida, voltei ao relatório e inseri um **gráfico de pizza**, utilizando `Categoria_Indice_Envolvimento` como legenda e `Id_Funcionario` (contagem) como valores;

    - Por último, na questão 8: **"Este item não deve estar no Dashboard, mas precisa ser calculado: Qual o total e o percentual de funcionários que devem receber promoção? Considere a coluna 'Anos Desde a Última Promoção' com a seguinte regra: se o funcionário tiver 5 anos ou mais desde a última promoção, deve ter a promoção considerada; caso contrário, a promoção não deve ser considerada agora."**, para respondê-la, criei uma **nova coluna** com a seguinte fórmula DAX:

    ```dax

        Promocao_Considerada = IF(DatasetRH[Anos_Desde_Ultima_Promocao] >= 5, "Sim", "Não")

    ```

    - Como o professor especificou que essa informação **não deveria ser exibida no dashboard**, optei por **manter a coluna apenas na base de dados**, de modo que possa ser utilizada em **análises futuras**.

---

#### Pontos Compartilhados pelo Professor na Unidade 6

- O professor criou uma **tabela de medidas** para organizar melhor o projeto (uma prática muito utilizada no mercado de trabalho, pois facilita a localização e manutenção das medidas no relatório). Nessa tabela, foram adicionadas as seguintes medidas: `TotalMasculino`, `TotalFeminino`, `% Masculino`, `% Feminino`, `TotalFunc`, `SalarioMedio`, `TotalFuncPromover`, `TotalFuncNaoPromover`, `% Promover` e `% Nao Promover`;

- Para criar essa tabela, ele acessou: **Inserir dados** → **Carregar**;

- Depois, para inserir as medidas, ele selecionou a tabela criada e clicou em **Nova medida**;

- Foram adicionadas as seguintes medidas à tabela:

    ```dax

        TotalFunc = COUNTROWS(DatasetRH)

        TotalFeminino = CALCULATE([TotalFunc], DatasetRH[Genero] = "Feminino")

        TotalMasculino = CALCULATE([TotalFunc], DatasetRH[Genero] = "Masculino")

        % Feminino = DIVIDE([TotalFeminino], [TotalFunc], 0)

        % Masculino = DIVIDE([TotalMasculino], [TotalFunc], 0)

        SalarioMedio = AVERAGE(DatasetRH[Salario_Mensal])

        TotalFuncPromover = CALCULATE([TotalFunc], DatasetRH[StatusPromo] = "Considerar Promoção")

        TotalFuncNaoPromover = CALCULATE([TotalFunc], DatasetRH[StatusPromo] = "Não Considerar Promoção")

        % Promover = DIVIDE([TotalFuncPromover], [TotalFunc], 0)

        % Nao Promover = DIVIDE([TotalFuncNaoPromover], [TotalFunc], 0)

    ```

- A criação da tabela deixou as funções DAX muito mais organizadas e fáceis de compreender. Para seguir o fluxo do professor, criei uma nova página no relatório dedicada exclusivamente às medidas que ele desenvolveu;

- Após isso, o professor criou uma **coluna condicional** (a qual também incluí na base). Em vez de criar uma medida para indicar quem deveria ser promovido, ele gerou a coluna `StatusPromo`, baseada em `Anos_Desde_Ultima_Promocao`:  

    - Se o valor for **maior ou igual a 5**, então: **"Considerar Promoção"**;  

    - Caso contrário: **"Não Considerar Promoção"**.  

- Essa coluna serviu de base para as medidas `TotalFuncPromover` e `TotalFuncNaoPromover`;

- Ele reforçou que criou mais medidas do que o necessário para o relatório atual, pois isso facilita análises futuras para o RH, evitando retrabalhos desnecessários;

- Posteriormente, inseriu os gráficos solicitados no relatório utilizando essas medidas. Também criou uma nova coluna categorizando `Indice_Envolvimento_Trabalho`, assim como eu havia feito;

- Para formatar as medidas percentuais, ele ensinou um macete: acesse a **Exibição de modelo**, selecione a medida (ex: `% Masculino`), role até as propriedades e altere o **Formato** para **Porcentagem**;

- Na parte estética, ele adicionou caixas sobre cada visual para destacar os elementos e ajustou a transparência para melhorar a apresentação.

---

## Unidade 7: Power BI para Análise de Dados de Logística

- **Qual a função da área de logística?** Essa área tem a função de gerenciar o fluxo de produtos e informações desde o ponto de origem até o destino final, de forma eficiente e econômica. Isso inclui a coordenação de várias atividades, como o transporte, armazenamento, distribuição, embalagem, gerenciamento de estoque e o gerenciamento de cadeia de suprimentos;

- Ao gerenciar a cadeia de suprimentos de forma eficaz, a logística pode garantir que as mercadorias estejam disponíveis no momento certo, no lugar certo e nas condições adequadas, além de otimizar os recursos e minimizar os custos.

### Principais KPIs de Logística

- Alguns dos principais KPIs da área de logística incluem:

    - **Tempo de ciclo:** o tempo necessário para atender um pedido, desde o momento em que é feito até o momento em que é entregue ao cliente;

    - **Taxa de entrega no prazo:** a porcentagem de pedidos entregues dentro do prazo acordado;

    - **Custo de transporte:** o custo médio por unidade ou por pedido para transportar os produtos;

    - **Nível de estoque:** o número de dias ou semanas de suprimento de estoque disponível;

    - **Taxa de devolução:** a porcentagem de pedidos devolvidos pelos clientes;

    - **Índice de acurácia de estoque:** a precisão do estoque registrado em relação ao estoque real;

    - **Taxa de utilização de armazenamento:** a porcentagem do espaço de armazenamento disponível que está sendo utilizado;

    - **Nível de serviço ao cliente:** a satisfação geral do cliente com o serviço de logística, incluindo tempo de entrega, qualidade do produto e atendimento ao cliente;

    - **Taxa de ocorrência de avarias:** a porcentagem de produtos que sofrem danos durante o transporte ou armazenamento;

    - **Índice de retorno sobre investimento (ROI):** o retorno financeiro gerado pelos investimentos em logística, como sistemas de gerenciamento de armazéns ou software de rastreamento de pedidos.

---

### Mini-Projeto 4: Desconstruindo o Dashboard e Resolvendo Problemas de Análise na Área de Logística

-  Eles, primeiramente, entregaram um dashboard repleto de problemas e erros, para que o aluno refizesse o dashboard e entregasse suas análises de forma profissional;

- A descrição do cenário: uma empresa de logística solicitou que um profissional fornecesse um Dashboard para compreender como está o processo de entrega de produtos da empresa. O profissional não parecia ter muito conhecimento sobre Power BI e entregou um trabalho com nítidos problemas e erros;

- O professor, após mostrar alguns dos erros, focou na construção do primeiro KPI: **"Total de Entregas no Prazo Por Canal de Entrega"**.;

- No dashboard incorreto, haviam usado um **gráfico de área** com `Canal_Entrega` no eixo X e `Status_Entrega` (contagem) no eixo Y, o que gerou um resultado inválido, pois **não contava as entregas realmente concluídas no prazo**;

- Para corrigir, o professor iniciou um novo relatório e reconstruiu o KPI da forma adequada:

    - Inseriu um **gráfico de área**;  

    - Colocou **`Canal_Entrega` no eixo X**;  

    - Colocou **`ID_Pedido` (contagem)** no eixo Y, corretamente representando o número total de entregas realizadas;  

    - Em seguida, aplicou um **filtro por Status**, arrastando o campo `Status_Entrega` para o painel de filtros e marcando apenas a opção **"No Prazo"**, garantindo que o gráfico exibisse **somente as entregas concluídas dentro do prazo**.

- No próximo KPI: **"Percentual de Entregas Antecipadas por Equipe de Entrega"**, foi aplicado um **gráfico de barras horizontal**, onde se adicionou `Equipe_Entrega` no eixo Y e `ID_Pedido` (contagem) no eixo X. Para visualizar o percentual, clicou-se na setinha de `ID_Pedido` e selecionou **Mostrar valor como → Percentual do total geral**;

- Para o terceiro KPI: **"Total de Entregas por Mês"**, foi mantido o **gráfico de linhas**, adicionando `Data_Entrega_Realizada` (mês) no eixo X e `ID_Pedido` (contagem) no eixo Y. Como essa contagem seria usada repetidas vezes, foi criada a medida **TotalEntregas**, centralizando o cálculo. Como cada linha da tabela representa uma entrega, a medida ficou:

```dax

    TotalEntregas = COUNTROWS(Logistica)

```

- Após criar a medida, todos os locais onde havia `ID_Pedido` (contagem) foram substituídos por `TotalEntregas`;

- Para o KPI: **"Total de Entregas de Produtos dos Top 5 Vendedores"**, inicialmente foi utilizado um **gráfico de rosca**, com `ID_Vendedor` como legenda e `TotalEntregas` em valores. Em seguida, aplicou-se o filtro **N superior → Superior 5 por TotalEntregas**. Como o gráfico de rosca não era o mais adequado para esse tipo de análise, ele foi substituído por uma **tabela**;

- Para o quinto KPI: **"Total de Entregas com Atraso por Cidade"**, devido à grande quantidade de cidades, um gráfico de barras não seria adequado. Em cenários assim, recomenda-se aplicar filtros: primeiro selecionando apenas o status Atrasado e, se necessário, refinando ainda mais conforme orientação da área de negócios. O professor adicionou uma **tabela** com `ID_Cidade` (não resumir) e `TotalEntregas` nas colunas. Depois, em filtro, adicionou `Status_Entrega` e selecionou apenas o status Atrasado;

- Para o último KPI: **"Percentual de Entregas por Status de Entrega"**, foi adicionado um **gráfico de barras**, com `Status_Entrega` no eixo X e `TotalEntregas` no eixo Y. Para exibir o percentual, clicou-se na setinha de `TotalEntregas` e selecionou: **Mostrar valor como → Percentual do total geral**;

- Posteriormente, ele acrescentou mais dois recursos ao dashboard. O primeiro foi uma classificação (rating) na tabela que exibe os top 5 vendedores. Para isso, na tabela **Medidas**, selecionou **Novas medidas rápidas**, onde existe o cálculo **Classificação por estrelas**, que converte um valor numérico em uma classificação variável. Nessa configuração, ele utilizou `TotalEntregas` como valor base, definiu **5 estrelas**, e ajustou os limites observando a tabela: como o menor valor era cerca de 1600, definiu **1500** como valor mínimo e **2500** como valor máximo. Por fim, renomeou a medida para **Rating**;

- Depois disso, na tabela **"Total de Entregas de Produtos dos Top 5 Vendedores"**, ele adicionou a medida **Rating**, permitindo ao gestor visualizar facilmente quais vendedores possuem melhor desempenho;

- O segundo recurso utilizado foi a aplicação de filtros usando DAX. Primeiro, adicionou um **cartão** com o valor de `TotalEntregas`. Em seguida, criou outro cartão para exibir apenas o total de entregas realizadas no prazo. Ele ressaltou que tanto o status **Antecipado** quanto **No Prazo** representam entregas consideradas dentro do prazo. Assim, desenvolveu a seguinte medida:

```dax

    TotalEntregasPrazo = CALCULATE([TotalEntregas], FILTER(Logistica, Logistica[Status_Entrega] = "Antecipado" || Logistica[Status_Entrega] = "No Prazo"))

```

- Após criar a medida, ele a adicionou ao cartão correspondente. Por fim, realizou a formatação geral do dashboard.

---

## Unidade 8: Power BI para Análise de Dados Financeiros

- **Qual a função da área de finanças de uma empresa?** Essa área é responsável por gerenciar os recursos financeiros da organização e garantir que esses recursos sejam utilizados de forma eficiente e eficaz para alcançar os objetivos da empresa. Algumas das principais funções incluem: planejamento financeiro, controle financeiro, gerenciamento de riscos, tomada de decisões financeiras e relacionamento com investidores.

### Principais KPIs de Finanças

- Alguns dos principais KPIs da área de finanças:

    - **Fluxo de caixa:** é uma medida do dinheiro que entra e sai da empresa em um determinado período de tempo. O fluxo de caixa positivo é um sinal de que a empresa está gerando receita suficiente para cobrir suas despesas;

    - **Margem de lucro:** é a porcentagem de lucro que a empresa ganha em cada venda. Ela pode ser calculada dividindo o lucro líquido pela receita total;

    - **Retorno sobre o investimento (ROI):** é uma medida do retorno que a empresa está obtendo de seus investimentos. O ROI pode ser calculado dividindo o lucro pelo investimento inicial;

    - **Endividamento:** é a medida da quantidade de dívida que a empresa tem em relação ao seu patrimônio líquido. Ele pode ser calculado dividindo a dívida total pelo patrimônio líquido;

    - **Faturamento:** é a receita total que a empresa gera em um determinado período de tempo;

    - **Custo de aquisição de clientes (CAC):** é a quantidade de dinheiro que a empresa gasta para adquirir cada novo cliente. Ele pode ser calculado dividindo o custo total de marketing e vendas pelo número de novos clientes;

    - **Prazo médio de pagamento (PMP):** é o tempo médio que a empresa leva para pagar seus fornecedores. Ele pode ser calculado dividindo o valor total das compras pelo valor total pago a fornecedores em um determinado período de tempo.

---

### Principais Despesas de uma Empresa

- Algumas das principais despesas comuns à maioria das empresas são:

    - **Custos de produção:** incluem os custos dos materiais, equipamentos, mão de obra e outros custos relacionados à produção de bens ou serviços;

    - **Despesas administrativas:** incluem os custos relacionados à administração da empresa, como aluguel, serviços públicos, telefone, internet, material de escritório, salários e benefícios dos funcionários administrativos, dentre outros;

    - **Despesas de venda e marketing:** incluem os custos relacionados à venda e promoção de produtos ou serviços, como publicidade, comissões de vendas, material promocional, eventos de marketing e outras despesas relacionadas;

    - **Despesas financeiras:** incluem os custos relacionados ao financiamento da empresa, como juros de empréstimos, taxas bancárias, despesas de cartão de crédito, entre outros;

    - **Impostos e taxas:** incluem os impostos, taxas e tributos que a empresa deve pagar, como imposto de renda, ICMS, ISS, contribuições previdenciárias e outras obrigações fiscais;

    - **Despesas com tecnologia:** incluem os custos relacionados à tecnologia da informação, como software, hardware, serviços em nuvem, licenças, manutenção, suporte técnico, entre outros;

    - **Despesas com pesquisa e desenvolvimento:** incluem os custos relacionados à pesquisa e desenvolvimento de novos produtos ou serviços, incluindo salários e benefícios de pesquisadores, equipamentos, materiais e outros custos relacionados.

---

### Principais Receitas de uma Empresa

- Algumas das principais fontes de receita comuns à maioria das empresas são:

    - **Vendas de produtos ou serviços:** a maioria das empresas obtém sua receita vendendo produtos ou serviços para seus clientes. A receita é gerada pelas vendas de produtos ou serviços, menos os custos associados à produção e vendas;

    - **Investimentos:** muitas empresas investem parte do faturamento em investimentos e ativos financeiros que rendem juros e, portanto, os investimentos se tornam fontes de receita;

    - **Publicidade:** empresas de mídia e plataformas de conteúdo podem gerar receita com publicidade, vendendo espaço publicitário para anunciantes;

    - **Licenciamento:** empresas que detêm propriedade intelectual podem gerar receita por meio de acordos de licenciamento, permitindo que outras empresas usem seus ativos em troca de uma taxa;

    - **Venda de ativos:** empresas podem gerar receita vendendo ativos, como propriedades, equipamentos ou outros recursos que não são mais necessários para suas operações;

    - **Franquias:** empresas podem gerar receita com a venda de franquias para empreendedores que desejam abrir uma nova unidade de negócios usando o modelo de negócias e a marca da empresa;

    - **Consultoria e serviços profissionais:** empresas de consultoria e serviços profissionais podem gerar receita por meio de taxas de consultoria e honorários de serviços prestados.

---

### Mini-Projeto 5: Dashboard de Análise Financeira