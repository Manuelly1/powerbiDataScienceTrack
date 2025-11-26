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