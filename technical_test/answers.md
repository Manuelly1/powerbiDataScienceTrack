## Considere uma base de `vendas` contendo:

- Data; Cliente; Produto; Categoria; Quantidade e Valor Total.

### 1. Crie uma medida em DAX que calcule o faturamento total acumulado por data. 

```dax

    Faturamento Total Acumulado = CALCULATE(SUMX(Vendas, Vendas[Quantidade] * Vendas[Valor Total]), FILTER(ALL(Vendas[Data]), Vendas[Data] <= MAX(Vendas[Data])))

```

- **Explicação:**

    - `SUMX(Vendas, Vendas[Quantidade] * Vendas[Valor Total])` → essa parte calcula o faturamento linha por linha;

    - `SUMX` → é uma função iteradora: percorre cada linha da tabela `Vendas`;

    - `Vendas[Quantidade] * Vendas[Valor Total]` → calcula o faturamento de cada venda individual;

    - **Resultado:** soma do faturamento total (sem acumular ainda);

    - `CALCULATE(...)`→ serve para modificar o contexto do cálculo e aplicar filtros personalizados. Ele é o **responsável por transformar a soma simples em soma acumulada**;

    - `ALL(Vendas[Data])`→ remove qualquer filtro de data que o visual tenha aplicado. Isso é essencial para que o acumulado considere: todas as datas anteriores e não apenas a data atual da linha;

    - `MAX(Vendas[Data])`→ representa a data atual do contexto do visual. Se o gráfico estiver em: 10/03 → MAX(Data) = 10/03. Ou seja, define até onde o acumulado deve ir;

    - `FILTER(...)`→ essa parte cria a lógica do acumulado: “Considere todas as datas menores ou iguais à data atual da linha.”


### 2. Explique qual visual você utilizaria para comparar: Categoria × Faturamento e por quê.

- Para comparar `Categoria` × `Faturamento`, eu priorizaria o **gráfico de colunas**, pois ele permite visualizar com clareza a diferença de faturamento entre as categorias, facilitando a comparação direta. O gráfico de pizza poderia ser utilizado apenas se houvesse poucas categorias (no máximo 3 ou 4), já que com muitas categorias a leitura se torna confusa.
O cartão seria um bom complemento para apresentar o faturamento total geral, mas não seria o principal visual para análise comparativa entre categorias.
    
### 3. Proponha um pequeno dashboard para análise de vendas mensais contendo:

- Pelo menos 3 visuais;

- Indicadores principais (KPIs);

- Filtro(s) estrategicamente escolhidos;

- **Descreva:** objetivo do dashboard, tipo dos gráficos e métricas exibidas.

#### Objetivo do dashboard

- O dashboard tem como finalidade fornecer uma visão clara do desempenho das vendas mensais, permitindo analisar o faturamento, o desempenho dos produtos e o comportamento dos clientes, auxiliando na tomada de decisão estratégica;

#### KPIs principais

- Faturamento total do mês;

- Quantidade total de vendas;

- Ticket médio mensal;

- Número de clientes ativos;

- Esses indicadores seriam exibidos em **cartões** para facilitar a leitura rápida dos resultados principais.

#### Visuais propostos

- **Gráfico de colunas:** Produto × Faturamento;

    - Objetivo: comparar quais produtos geraram mais receita no mês;

    - Métrica: Soma do Valor Total.

- **Gráfico de barras ou colunas:** Categoria × Faturamento;

    Objetivo: analisar quais categorias têm maior impacto nas vendas;

    Caso o número de categorias seja pequeno (até 4), poderia ser usado gráfico de pizza, mas colunas oferecem melhor comparação visual.

- **Gráfico Top 5 Clientes por Faturamento**

    - Objetivo: identificar os clientes mais engajados, auxiliando em estratégias de fidelização e campanhas promocionais.

- **Filtros (segmentações de dados):**

    - Data (com hierarquia em Ano → Mês);

    - Categoria;

    - Cliente;

    - Esses filtros permitem análises dinâmicas e específicas por período e perfil de consumo.

### 4. Usando uma tabela Faturamento com as colunas: Data, Valor e Categoria, crie uma medida DAX que calcule o faturamento total apenas da categoria "Alimentos":

```dax

    Faturamento_Alimentos = CALCULATE(SUM(DadosFaturamento[Valor]), DadosFaturamento[Categoria] = "Alimentos")

```

### 5. Você tem duas tabelas: Clientes(id_cliente, nome) e Pedidos(id_pedido, id_cliente, total). Explique como configurar o relacionamento no Power BI e qual é o tipo de cardinalidade:

- A relação é criada a partir do campo em comum entre as tabelas, neste caso, o campo em comum é `id_cliente`. Em `Clientes`, `id_cliente` é chave primária, então possui valores únicos. Em `Pedidos`, pode aparecer várias vezes como chave estrangeira, uma vez que pode representar os vários pedidos feitos pelo mesmo cliente;

- Por isso, o Power BI cria uma relação de um-para-muitos (`1:*`), onde `Clientes` é o lado `1` e `Pedidos` é o lado `*`. A direção do filtro deve ser `Clientes → Pedidos`, para que ao selecionar um cliente, seus pedidos sejam filtrados corretamente.

### 6. Você tem dados de vendas mensais. Qual visual você usaria para comparar rapidamente a evolução das vendas ao longo do ano? Justifique.

- Eu utilizaria um **gráfico de linhas (ou de área)** porque esse tipo de visual é ideal para dados organizados ao longo de um período de tempo. Como as vendas são mensais, trata-se de uma série temporal, e gráficos de linha permitem identificar facilmente tendências, aumentos e quedas ao longo dos 12 meses. Além disso, esse tipo de visual mantém a continuidade entre os pontos, facilitando a análise da evolução das vendas durante o ano.

### 7. Com base em uma tabela `Vendas(qtd, preco)`, crie uma medida que calcule: Total de Vendas

```dax

    Total de Vendas = SUMX(Vendas, Vendas[qtd] * Vendas[preco])

```

### 8. Em um calendário já relacionado, crie uma medida que calcule: crescimento (%) mês a mês

```dax

    Crescimento Mês a Mês (%) =
        VAR TotalAtual = [Total de Vendas]
        VAR TotalMesAnterior = CALCULATE([Total de Vendas], DATEADD('Calendario'[Data], -1, MONTH))

        RETURN DIVIDE(TotalAtual - TotalMesAnterior, TotalMesAnterior)

```

### 9. Explique como relacionar: as tabelas `Vendas` e `Produtos`

- Cada produto possui um identificador único (ex: `Id_Produto`), portanto a tabela `Produtos` é o lado 1 da relação;

- Na tabela `Vendas`, o mesmo produto pode aparecer várias vezes, logo ela é o lado muitos ( * );

- A relação deve ser criada do campo Produtos[Id_Produto] → Vendas[Id_Produto].

### 10. Como poderia fazer para apresentar os 5 produtos mais vendidos?

- **Forma 1 – Pelo Power BI (mais simples):** selecionar o visual; ir em Filtros → Filtro por produto; escolher Top N e definir: Top 5 por: `Total de Vendas`;

- **Forma 2 – Medida DAX:**

```dax

    Top 5 Produtos = TOPN(5, SUMMARIZE(Produtos, Produtos[Nome], "Total", [Total de Vendas]), [Total], DESC)

```

- **Forma 3 – Visual já filtrado por ranking:** criar ranking:

```dax

    Ranking Produtos = RANKX(ALL(Produtos[Nome]), [Total de Vendas], DESC)

```

- E usar esse ranking para mostrar apenas até 5 produtos.

### 11. Na tabela `Vendas`, com: `Data` e `Valor`, crie uma medida que calcule faturamento acumulado no ano (YTD)

```dax

    Faturamento Acumulado no Ano = TOTALYTD(SUM(Vendas[Valor]), Vendas[Data])

```

- Neste caso, fez-se necessário usar funções de time intelligence, como TOTALYTD, e também somar os valores.

### 12. Na tabela `Pedidos`, calcule: número de clientes únicos que fizeram pedidos acima de 500 reais. A medida deve contar `id_cliente`, não linhas

```dax

    Número de Clientes que Fizeram Pedidos Acima de 500 =   
        CALCULATE(
            DISTINCTCOUNT(Pedidos[id_cliente]),
            Pedidos[valor] > 500
    )

```

### 13. Você recebe uma coluna de telefone com formatos misturados: `84 9999-1234`, `(84) 98765-4321` e `+55 84 98888-1212`. Explique como normalizar os números para o formato: `5584XXXXXXXX`. Use apenas recursos do Power Query (M Language), pode descrever os passos

- Para normalizar números de telefone com formatos misturados no Power Query, eu seguiria estes passos:

**1- Remover todos os caracteres não numéricos:**

    - Seleciono a coluna de telefone;

    - Uso Transformar → Extrair → Apenas Dígitos;

    - Isso garante que qualquer formato vire apenas números, exemplo:

        "84 9999-1234" → "8499991234";

        "(84) 98765-4321" → "84987654321";

        "+55 84 98888-1212" → "5584988881212".

**2- Garantir que o telefone contenha o código do país (55):**

    - Adiciono uma Coluna Personalizada com M:

    ```dax

        if Text.StartsWith([TelefoneLimpo], "55")
        then [TelefoneLimpo]
        else "55" & [TelefoneLimpo]
    
    ```

**3- Padronizar para 5584XXXXXXXX:**

    - Após garantir o 55, alguns números terão 10 dígitos após o DDD e outros 9;
    
    - Então adiciono outra coluna personalizada para colocar sempre o formato final:

    ```dax

        "55" &
        Text.Middle([TelefoneLimpo], Text.Length([TelefoneLimpo]) - 10, 2) &
        Text.End([TelefoneLimpo], 8)

    ```

- **De forma simplificada:** no Power Query, eu primeiro extraio apenas os dígitos da coluna; depois, adiciono uma coluna personalizada verificando se o número já começa com 55; se não começar, concateno "55". Por fim, uso as funções Text.Middle e Text.End para montar o formato final `5584XXXXXXXX`. Assim todos os telefones ficam padronizados independentemente do formato original.
