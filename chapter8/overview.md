# Unidade 8: Power BI para Análise de Dados Financeiros

- **Qual a função da área de finanças de uma empresa?** Essa área é responsável por gerenciar os recursos financeiros da organização e garantir que esses recursos sejam utilizados de forma eficiente e eficaz para alcançar os objetivos da empresa. Algumas das principais funções incluem: planejamento financeiro, controle financeiro, gerenciamento de riscos, tomada de decisões financeiras e relacionamento com investidores.

## Principais KPIs de Finanças

- Alguns dos principais KPIs da área de finanças:

    - **Fluxo de caixa:** é uma medida do dinheiro que entra e sai da empresa em um determinado período de tempo. O fluxo de caixa positivo é um sinal de que a empresa está gerando receita suficiente para cobrir suas despesas;

    - **Margem de lucro:** é a porcentagem de lucro que a empresa ganha em cada venda. Ela pode ser calculada dividindo o lucro líquido pela receita total;

    - **Retorno sobre o investimento (ROI):** é uma medida do retorno que a empresa está obtendo de seus investimentos. O ROI pode ser calculado dividindo o lucro pelo investimento inicial;

    - **Endividamento:** é a medida da quantidade de dívida que a empresa tem em relação ao seu patrimônio líquido. Ele pode ser calculado dividindo a dívida total pelo patrimônio líquido;

    - **Faturamento:** é a receita total que a empresa gera em um determinado período de tempo;

    - **Custo de aquisição de clientes (CAC):** é a quantidade de dinheiro que a empresa gasta para adquirir cada novo cliente. Ele pode ser calculado dividindo o custo total de marketing e vendas pelo número de novos clientes;

    - **Prazo médio de pagamento (PMP):** é o tempo médio que a empresa leva para pagar seus fornecedores. Ele pode ser calculado dividindo o valor total das compras pelo valor total pago a fornecedores em um determinado período de tempo.

---

## Principais Despesas de uma Empresa

- Algumas das principais despesas comuns à maioria das empresas são:

    - **Custos de produção:** incluem os custos dos materiais, equipamentos, mão de obra e outros custos relacionados à produção de bens ou serviços;

    - **Despesas administrativas:** incluem os custos relacionados à administração da empresa, como aluguel, serviços públicos, telefone, internet, material de escritório, salários e benefícios dos funcionários administrativos, dentre outros;

    - **Despesas de venda e marketing:** incluem os custos relacionados à venda e promoção de produtos ou serviços, como publicidade, comissões de vendas, material promocional, eventos de marketing e outras despesas relacionadas;

    - **Despesas financeiras:** incluem os custos relacionados ao financiamento da empresa, como juros de empréstimos, taxas bancárias, despesas de cartão de crédito, entre outros;

    - **Impostos e taxas:** incluem os impostos, taxas e tributos que a empresa deve pagar, como imposto de renda, ICMS, ISS, contribuições previdenciárias e outras obrigações fiscais;

    - **Despesas com tecnologia:** incluem os custos relacionados à tecnologia da informação, como software, hardware, serviços em nuvem, licenças, manutenção, suporte técnico, entre outros;

    - **Despesas com pesquisa e desenvolvimento:** incluem os custos relacionados à pesquisa e desenvolvimento de novos produtos ou serviços, incluindo salários e benefícios de pesquisadores, equipamentos, materiais e outros custos relacionados.

---

## Principais Receitas de uma Empresa

- Algumas das principais fontes de receita comuns à maioria das empresas são:

    - **Vendas de produtos ou serviços:** a maioria das empresas obtém sua receita vendendo produtos ou serviços para seus clientes. A receita é gerada pelas vendas de produtos ou serviços, menos os custos associados à produção e vendas;

    - **Investimentos:** muitas empresas investem parte do faturamento em investimentos e ativos financeiros que rendem juros e, portanto, os investimentos se tornam fontes de receita;

    - **Publicidade:** empresas de mídia e plataformas de conteúdo podem gerar receita com publicidade, vendendo espaço publicitário para anunciantes;

    - **Licenciamento:** empresas que detêm propriedade intelectual podem gerar receita por meio de acordos de licenciamento, permitindo que outras empresas usem seus ativos em troca de uma taxa;

    - **Venda de ativos:** empresas podem gerar receita vendendo ativos, como propriedades, equipamentos ou outros recursos que não são mais necessários para suas operações;

    - **Franquias:** empresas podem gerar receita com a venda de franquias para empreendedores que desejam abrir uma nova unidade de negócios usando o modelo de negócias e a marca da empresa;

    - **Consultoria e serviços profissionais:** empresas de consultoria e serviços profissionais podem gerar receita por meio de taxas de consultoria e honorários de serviços prestados.

---

## Mini-Projeto 5: Dashboard de Análise Financeira

- Primeiramente, a base foi conectada à ferramenta e analisada. Durante essa análise, foi possível observar que o título não havia sido reconhecido pelo Power BI, pois, por exemplo, a partir da terceira coluna utilizava-se uma data como variável. Para corrigir isso e deixar a data como uma única coluna, com outra coluna contendo os valores correspondentes, ele acessou **Transformar dados** → **Usar a primeira linha como cabeçalho**. Apenas com essa ação, os valores já foram isolados;

- Em seguida, como era necessário alterar os dados de linha para coluna, a opção **Transpor** foi aplicada para gerar a tabela transposta. Contudo, o problema ainda não estava totalmente resolvido. Ao clicar na etapa gerada, identificou-se uma linha de código no Editor Avançado. Ele apagou essa linha e adicionou o seguinte código:

```dax

    = Table.UnpivotOtherColumns(#"Tipo Alterado1", {"Tipo", "Componente"}, "Data", "Valor")

```

- **O que esse código faz?** Ele pega a tabela após a etapa **"Tipo Alterado1"** (responsável por definir a primeira linha como cabeçalho), aplica o **unpivot** mantendo as colunas `Tipo` e `Componente`, e converte todas as demais colunas em duas novas colunas: `Data` e `Valor`. Assim, tem-se 4 colunas na tabela: `Componente`, `Data`, `Tipo` e `Valor`. Depois disso, ele aplicou as alterações;

- Posteriormente, constatou-se que a coluna `Data` não estava sendo reconhecida como tipo *date*, sendo tratada como *string*. Devido à forma como a transformação anterior foi realizada, a coluna `Data` não exibiu a hierarquia completa (Ano, Trimestre, Mês, Dia), o que compromete a flexibilidade das análises. Para solucionar isso, foi necessário ajustar o tipo de dados da coluna. Assim, retornou-se à etapa **Transformar dados** → selecionou-se o ícone de tipo na coluna `Data` e alterou-se para **Data**. Após essa mudança, a hierarquia passou a ser exibida corretamente;

- Com os dados devidamente formatados, iniciou-se a criação da **tabela: MedidasIndicadores**, onde foram incluídos os indicadores sugeridos no roteiro. As seguintes medidas foram adicionadas:

```dax

    TotalReceitas = CALCULATE(SUM(DadosFinanceiros[Valor]), DadosFinanceiros[Tipo] = "Receitas") 
    TotalDespesas = CALCULATE(SUM(DadosFinanceiros[Valor]), DadosFinanceiros[Tipo] = "Despesas") 
    Lucro = [TotalReceitas] - [TotalDespesas] 
    MargemLucro = DIVIDE([Lucro], [TotalReceitas], 0) 

```

- Em seguida, foi inserido um **cartão** exibindo a medida `TotalReceitas`, atendendo à primeira questão do roteiro. O mesmo procedimento foi aplicado para `TotalDespesas` e `MargemLucro`. A medida `Lucro` foi criada exclusivamente para ser utilizada no cálculo da margem;

- Para responder à quarta questão: **"Total de Receitas por Componente"**, ao analisar a tabela, observou-se que existem várias categorias e que elas dependem do tipo (Receitas/Despesas). Ao filtrar apenas o tipo `Receitas`, verificou-se que há somente seis componentes. Com base nisso, foi selecionado um gráfico de **barras horizontais**, utilizando `Componente` no eixo Y e `TotalReceitas` no eixo X;

- O próximo indicador: **"Total de Despesas por Componente em relação à média de Despesas"** foi construído da seguinte forma: selecionou-se um **gráfico de área**, adicionando `Componente` ao eixo Y e `TotalDespesas` ao eixo X. Como o enunciado solicita a exibição de uma linha de média, utilizou-se o ícone ao lado de **Formatar visual**, identificado por uma lupa (**Adicionar mais análises ao seu visual**). Em seguida, escolheu-se **Linha média** → **Adicionar linha**, e foi habilitado o rótulo de dados, permitindo visualizar a média das despesas diretamente no gráfico;

- Para a tarefa seguinte: **"Total de Receitas e Despesas por Componente e por Ano, com a hierarquia Tipo/Componente"** é necessário apresentar também a hierarquia categórica Tipo → Componente, visto que cada tipo (Receitas/Despesas) possui seus respectivos componentes. Nesse caso, o visual mais adequado é uma **matriz**;

- Para as **linhas**, foram adicionados `Tipo` e `Componente`, criando a hierarquia de navegação. Em **valores**, utilizou-se `Valor` (soma), que já representa o total de receitas e despesas, evitando a criação desnecessária de uma nova medida. Por fim, em **colunas**, foi incluído o campo `Ano`;

- O professor reforçou um ponto importante: **para representar hierarquias, o ideal é utilizar matriz, não tabela**;

- A última exigência do roteiro: **"a empresa precisa identificar os segmentos onde Receitas e Despesas são maiores e menores, a fim de traçar seu plano estratégico"** foi implementada da seguinte forma: inicialmente, o professor esclareceu o que o enunciado realmente solicitava. A palavra *segmentos* refere-se a agrupamentos, ou seja, é necessário categorizar os dados com base em características comuns. Além disso, o enunciado destaca *maiores e menores*, o que indica uma análise comparativa. Tudo isso deve ser observado considerando os dois tipos (`Receitas` e `Despesas`), envolvendo as colunas `Tipo` e `Componente`;

- Em um primeiro momento, foi selecionado o elemento **Segmentação de dados**, porém esse recurso apenas cria filtros e não realiza a segmentação analítica solicitada. Por isso, ele foi removido do dashboard;

- Em seguida, o professor explicou que há um elemento visual no Power BI que realiza esse tipo de análise automaticamente: **Principais Influenciadores**. Assim, adicionou-se `Valor` em **Analisar** e `Tipo` e `Componente` em **Explicar por**. Na formatação, foi desativada a seção relacionada aos *principais influenciadores*, mantendo apenas a exibição dos *principais segmentos*. Com isso, o Power BI passou a retornar os agrupamentos automaticamente, indicando onde estão as maiores e menores receitas e despesas.

