# SQL Analytics

## O que é SQL Analytics?

- É um termo que se refere à **análise de dados usando a linguagem SQL em conjunção com técnicas de análise de dados e ferramentas de visualização**;

- O **objetivo** é ajudar as organizações a tomar decisões informadas com base em insights extraídos de grandes volumes de dados armazenados em sistemas de gerenciamento de banco de dados relacionais e outras fontes de dados compatíveis com SQL;

- As principais características do SQL Analytics incluem:

    - **Análise de dados:** Através de consultas SQL é possível realizar análises descritivas, diagnósticas, preditivas e prescritivas para entender o passado e o presente dos dados e fazer previsões para o futuro;

    - **Agregação e transformação de dados:** A SQL permite agregar e transformar dados de várias tabelas e colunas, facilitando a geração de informações úteis e insights a partir dos dados brutos;

    - **Integração com ferramentas de BI e visualização:** As consultas SQL podem ser usadas em conjunto com ferramentas de BI e visualização de dados, como Tableau, Power BI e Looker (Google Data Studio), para criar painéis interativos e relatórios que ajudam a comunicar os insights de forma eficaz;

    - **Otimização de desempenho:** O SQL Analytics pode aproveitar técnicas avançadas de otimização de consulta, como indexação, particionamento e materialização, para melhorar o desempenho das consultas e a eficiência da análise de dados;

    - **Escalabilidade:** Com o advento de soluções de armazenamento e processamento de dados em larga escala, como Data Warehouses e bancos de dados baseados em nuvem, o SQL Analytics pode lidar com volumes crescentes de dados e fornecer insights em tempo real.

---

## Preparando o Banco de Dados para Estudar Linguagem SQL

- Antes de começar a pôr a mão na massa, o professor forneceu um banco de dados para ser utilizado durante a unidade (o mesmo da unidade anterior);

- Em seguida, como o banco de dados já estava disponível, fez-se necessário buscar uma ferramenta para realizar a conexão. Como visto no capítulo anterior, o Power BI permite essa conexão, porém o seu objetivo é que o analista extraia os dados e os leve para a ferramenta a fim de realizar análises. Ele não é ideal para a execução contínua de comandos SQL, ou seja, não funciona como uma IDE. Dessa forma, o professor optou por uma ferramenta gratuita: o **SQLite Studio**, já que o banco de dados utilizado é em SQLite. Para isso, foi feito o download da versão 3.4.4 e realizada a instalação;

- Posteriormente, dentro do SQLite Studio, foi feita a associação/conexão com o banco de dados. Para isso, há um ícone na parte superior que representa um banco de dados; ao passar o mouse sobre ele, aparece a mensagem **“Adicionar um banco de dados”**. Ao clicar, abre-se uma janela solicitando o tipo do banco (existem variações do SQLite, mas o utilizado foi o **SQLite 3**) e o arquivo do banco de dados (selecionando o caminho correspondente). Após isso, basta clicar em **Ok**;

- Ao dar dois cliques no banco de dados conectado, as tabelas são exibidas. Para executar a primeira consulta SQL, basta clicar com o botão direito sobre a tabela desejada (por exemplo, a tabela de clientes) e selecionar **Gerar consulta → SELECT**. Ao clicar no ícone de *play*, a consulta é executada.

---

## Comandos SQL 

- Antes de iniciar, o professor mostrou que para abrir uma nova janela no **SQLite Studio** basta ir em **Ferramentas → Abrir editor de SQL**;

- Para extrair tudo de uma tabela (`SELECT *`):

```sql

    SELECT *
    FROM TB_DSA_CLIENTES;

```

- Filtrar por coluna (`SELECT` + nome da coluna):

```sql

    SELECT ID_Cliente, Nome_Cliente, Cidade
    FROM TB_DSA_CLIENTES;

```

- Para limitar a quantidade de registros retornados (visualizar uma amostra da base - `LIMIT`):

```sql

    SELECT *
    FROM TB_DSA_CLIENTES
    LIMIT 10;

```

- Para saber, por exemplo, quantos segmentos distintos existem na tabela de clientes (`DISTINCT`):

```sql

    SELECT DISTINCT Segmento
    FROM TB_DSA_CLIENTES;

```

- Dessa forma, a consulta retorna apenas valores únicos da coluna `Segmento`;

- Para filtrar os dados em nível de registro (`WHERE`):

```sql

    SELECT *
    FROM TB_DSA_PEDIDOS
    WHERE Ano = 2014;

```

- Nesse caso, são retornados apenas os registros da tabela de pedidos referentes ao ano de 2014;

- Quando há mais de uma condição envolvida na filtragem, utilizam-se **operadores lógicos**:

```sql

    SELECT *
    FROM TB_DSA_VENDAS
    WHERE Quantidade_Vendida <=2 AND Valor_Venda > 900;

``` 

- Ou seja, a consulta retorna apenas os registros da tabela de vendas em que a quantidade vendida foi menor ou igual a 2 e o valor da venda foi superior a 900;

- Outro operador valioso para trabalhar com intervalos (`BETWEEN`):

```sql

    SELECT *
    FROM TB_DSA_VENDAS
    WHERE Valor_Venda BETWEEN 310 AND 320;

``` 

- Nesse caso, a consulta retorna os registros da tabela vendas em que o valor da venda esteja entre 310 e 320;

- Outro operador utilizado em conjunto com o `WHERE` para realizar a filtragem de registros textuais é o `LIKE`:

```sql

    SELECT *
    FROM TB_DSA_PRODUTOS
    WHERE Nome_Produto LIKE '%Clock%';

``` 

- Nesse caso, a consulta retorna, na tabela de produtos, apenas os registros cujo nome contém a palavra **Clock**, independentemente da posição do termo, o que é possibilitado pelo uso do caractere `%` no início e no fim da expressão;

- Outro operador útil para lidar com dados de texto (`IN`):

```sql

    SELECT *
    FROM TB_DSA_PRODUTOS
    WHERE Categoria IN ('Moveis', 'Tecnologia');

``` 

- Nesse outro exemplo, na tabela de produtos, a consulta retorna apenas os registros que pertencem às categorias **Móveis** e **Tecnologia**;

- Caso se deseje retornar todos os produtos que **não** pertencem a essas duas categorias, basta utilizar o `NOT IN`:

```sql

    SELECT *
    FROM TB_DSA_PRODUTOS
    WHERE Categoria NOT IN ('Moveis', 'Tecnologia');

``` 

- Para ordenar os dados, utiliza-se o comando `ORDER BY`:

```sql

    SELECT *
    FROM TB_DSA_PRODUTOS
    ORDER BY Nome_Produto;

``` 

- Funções de agregação (`MIN`, `MAX`, `AVG`, `COUNT`, `SUM`):

```sql

    SELECT MIN(Valor_Venda),
           MAX(Valor_Venda),
           AVG(Valor_Venda),
           SUM(Valor_Venda),
           COUNT(Valor_Venda)

    FROM TB_DSA_VENDAS;

``` 

- Dessa forma, a consulta retorna o menor valor de venda, o maior, a média, a soma total e a contagem de registros;

- Outro exemplo utilizando essas funções, mas agora por produto, e não mais de forma genérica. Para isso, ou seja, para realizar o agrupamento, utiliza-se o `GROUP BY`:

```sql

    SELECT MIN(Valor_Venda) AS valorMinimo,
           MAX(Valor_Venda) AS valorMaximo,
           AVG(Valor_Venda) AS valorMedio,
           SUM(Valor_Venda) AS valorTotal,
           COUNT(Valor_Venda) AS contagem

    FROM TB_DSA_VENDAS
    GROUP BY Produto;

``` 

- Assim, os resultados são agrupados por produto, retornando as métricas agregadas para cada um deles;

- Para arredondar os resultados para duas casas decimais e ordenando pela coluna `contagem`:

```sql

    SELECT ROUND(MIN(Valor_Venda), 2) AS valorMinimo,
           ROUND(MAX(Valor_Venda), 2) AS valorMaximo,
           ROUND(AVG(Valor_Venda), 2) AS valorMedio,
           ROUND(SUM(Valor_Venda), 2) AS valorTotal,
           COUNT(Valor_Venda) AS contagem

    FROM TB_DSA_VENDAS
    GROUP BY Produto
    ORDER BY contagem DESC;

``` 

- Para evitar exibir o código do produto, indica-se retornar o nome do produto. No entanto, essa informação encontra-se em outra tabela, o que torna necessária a realização de uma junção (`JOIN`):

```sql

    SELECT ROUND(MIN(t1.Valor_Venda), 2) AS valorMinimo,
           ROUND(MAX(t1.Valor_Venda), 2) AS valorMaximo,
           ROUND(AVG(t1.Valor_Venda), 2) AS valorMedio,
           ROUND(SUM(t1.Valor_Venda), 2) AS valorTotal,
           COUNT(t1.Valor_Venda) AS contagem,
           t2.Nome_Produto

    FROM TB_DSA_VENDAS AS t1

    JOIN TB_DSA_PRODUTO AS t2
        ON t1.Produto = t2.ID_Produto

    GROUP BY Produto
    ORDER BY contagem DESC;

``` 

- O professor não utilizou o `JOIN` no exemplo apresentado em aula, optando por realizar a junção por meio das cláusulas `FROM` e `WHERE`. Exemplo:

```sql

    SELECT 
        ROUND(MIN(t1.Valor_Venda), 2) AS valorMinimo,
        ROUND(MAX(t1.Valor_Venda), 2) AS valorMaximo,
        ROUND(AVG(t1.Valor_Venda), 2) AS valorMedio,
        ROUND(SUM(t1.Valor_Venda), 2) AS valorTotal,
        COUNT(t1.Valor_Venda) AS contagem,
        t2.Nome_Produto

    FROM TB_DSA_VENDAS AS t1,
        TB_DSA_PRODUTOS AS t2

    WHERE t1.Produto = t2.ID_Produto

    GROUP BY t1.Produto, t2.Nome_Produto
    ORDER BY contagem DESC;

```

- Aplicando uma nova instrução: `INSERT`, utilizada para inserir novos dados no banco de dados:

```sql
    INSERT INTO TB_DSA_CLIENTES (
        ID_Cliente,
        Nome_Cliente,
        Cidade,
        Estado,
        Pais,
        Regiao,
        Mercado,
        Segmento
    )

    VALUES (
        'ID_Cliente',
        'Nome_Cliente',
        'Cidade',
        'Estado',
        'Pais',
        'Regiao',
        'Mercado',
        'Segmento'
    );


```

- Nesse caso, na tabela de clientes, especificamente nas colunas listadas acima, estão sendo inseridos os valores informados na cláusula `VALUES`;

- Para atualizar um ou mais registros, utiliza-se a instrução `UPDATE`:

```sql

UPDATE TB_DSA_CLIENTES
    SET ID_Cliente = 'ID_Cliente',
       Nome_Cliente = 'Nome_Cliente',
       Cidade = 'Cidade',
       Estado = 'Estado',
       Pais = 'Pais',
       Regiao = 'Regiao',
       Mercado = 'Mercado',
       Segmento = 'Segmento'
    WHERE ID_Cliente = 'ID_Cliente' AND 
       Nome_Cliente = 'Nome_Cliente' AND 
       Cidade = 'Cidade' AND 
       Estado = 'Estado' AND 
       Pais = 'Pais' AND 
       Regiao = 'Regiao' AND 
       Mercado = 'Mercado' AND 
       Segmento = 'Segmento';

```

- A cláusula `SET` é utilizada para definir os novos valores que serão atribuídos às colunas. No exemplo acima, deseja-se que a coluna `ID_Cliente` receba um novo valor, e assim sucessivamente;

- Para atualizar apenas uma coluna específica de um registro:

```sql

UPDATE TB_DSA_CLIENTES
    SET Nome_Cliente = 'Nome_Cliente'
    WHERE ID_Cliente = '1000';

```

- Nesse exemplo, a consulta localiza o cliente com o ID informado e atualiza o valor da coluna `Nome_Cliente` correspondente;

- Para excluir um registro do banco de dados, utiliza-se a instrução `DELETE`:

```sql

    DELETE FROM TB_DSA_CLIENTES
        WHERE ID_Cliente = '1000';

```

- Nesse caso, o registro da tabela de clientes que possui o ID igual a 1000 será removido do banco de dados.

---

## SQL Analytics no Power BI

- O professor demonstrou como utilizar SQL diretamente no Power BI. Para isso, aplicou uma das consultas já discutidas anteriormente. Antes da execução, acessou o caminho **Obter dados → ODBC → Conectar → `db_dsa` → Opções avançadas**, onde adicionou o script SQL abaixo:

```sql

    SELECT 
        ROUND(MIN(t1.Valor_Venda), 2) AS valorMinimo,
        ROUND(MAX(t1.Valor_Venda), 2) AS valorMaximo,
        ROUND(AVG(t1.Valor_Venda), 2) AS valorMedio,
        ROUND(SUM(t1.Valor_Venda), 2) AS valorTotal,
        COUNT(t1.Valor_Venda) AS contagem,
        t2.Nome_Produto,
        t3.Ano

    FROM TB_DSA_VENDAS AS t1,
        TB_DSA_PRODUTOS AS t2,
        TB_DSA_PEDIDOS AS t3

    WHERE t1.Produto = t2.ID_Produto

    GROUP BY t1.Produto, t2.Nome_Produto
    ORDER BY contagem DESC;


```

-  Em seguida, carregou os dados. 