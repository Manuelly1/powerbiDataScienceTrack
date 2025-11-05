# Curso: Microsoft Power BI para Business Intelligence e Ciência de Dados

## Conceitos Importantes de Dados

- **Data Warehouse:** é um banco de dados central que reúne e organiza grandes volumes de dados históricos vindos de várias fontes da empresa (sistemas de vendas, RH, marketing etc), com o objetivo de facilitar análises e tomadas de decisão;

- **Data Mart:** é como um “mini data warehouse”, voltado para um departamento específico (por exemplo, um data mart de vendas ou de finanças). Ele contém apenas os dados relevantes para aquela área;

- **ETL (Extract, Transform, Load):** é o processo de extração, transformação e carga dos dados, ou seja, buscar os dados das fontes, limpá-los e padronizá-los, e armazená-los no data warehouse;

- **OLAP (Online Analytical Processing):** são ferramentas e técnicas para análise multidimensional dos dados, permitindo explorar informações de diferentes ângulos (por exemplo, vendas por região, tempo e produto);

- **Data Lake:** é um repositório que guarda dados brutos e não estruturados (textos, imagens, logs etc), geralmente usado antes de um processamento mais analítico;

- **BI (Business Intelligence):** é o conjunto de ferramentas e práticas que transforma os dados do data warehouse em relatórios, dashboards e insights para o negócio.

---

## Unidade 2: Laboratório Prático I

- A base de dados `dataset.csv` foi disponibilizada e, após ser conectada e carregada na ferramenta, submeteu-se à aplicação de diferentes métricas analíticas;

### Aula - Cartão de Métricas

- O professor iniciou respondendo à primeira pergunta do roteiro: **“Qual o valor total vendido?”**, que corresponde a uma métrica numérica. Em outras palavras: “Considerando todas as vendas, qual foi o total vendido?”;

- No Power BI, ele inseriu um cartão visual e adicionou o campo `Total_Vendas`, que já continha o somatório dos valores. Dessa forma, foi possível responder já a primeira questão;

- **Observação:** Se o campo `Total_Vendas` não existisse pronto no `dataset`, seria preciso criar essa métrica manualmente dentro do Power BI usando DAX (Data Analysis Expressions);

    - **Seria algo assim:**

    - Iria em uma `Nova Medida` e em seguida adicionaria uma fórmula DAX parecida com esta:

        `Total_Vendas = SUMX(dataset, dataset[Quantidade] * dataset[Preco_Unitario] * (1 - dataset[Desconto]))`

    - Se o valor de cada item já estiver em uma coluna (por exemplo, `Valor_Venda`):

        `Total_Vendas = SUM(dataset[Valor_Venda])`
        
    - O correto é utilizar o `preço × quantidade`, aplicando o `desconto` apenas quando necessário. Como neste caso ele é considerado, foi incluído na fórmula apresentada acima.

---

### Aula - Gráfico de Pizza

- O professor iniciou respondendo à segunda pergunta do roteiro: **“Quantas vendas foram realizadas por categoria de produto?”**. Ele escolheu o **gráfico de pizza**, pois, primeiramente, selecionou esse tipo de visual e, em seguida, adicionou o campo `Categoria` em `Legenda`. Depois, inseriu `ID_Pedido` em `Valores`, e o Power BI retornou automaticamente a contagem de `ID_Pedido` por `Categoria`, ou seja, já resolveu o problema, uma vez que fez a contagem do número de registros para cada `Categoria`;

- **Observação:** Segundo o professor, como a base possui poucas categorias, o gráfico de pizza é uma boa opção para representar esse cenário.Caso houvesse mais de três categorias, o uso desse tipo de gráfico já não seria recomendado;

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

--

## Unidade 3: Modelagem, Relacionamentos e DAX

- 