# Unidade 7: Power BI para Análise de Dados de Logística

- **Qual a função da área de logística?** Essa área tem a função de gerenciar o fluxo de produtos e informações desde o ponto de origem até o destino final, de forma eficiente e econômica. Isso inclui a coordenação de várias atividades, como o transporte, armazenamento, distribuição, embalagem, gerenciamento de estoque e o gerenciamento de cadeia de suprimentos;

- Ao gerenciar a cadeia de suprimentos de forma eficaz, a logística pode garantir que as mercadorias estejam disponíveis no momento certo, no lugar certo e nas condições adequadas, além de otimizar os recursos e minimizar os custos.

## Principais KPIs de Logística

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

## Mini-Projeto 4: Desconstruindo o Dashboard e Resolvendo Problemas de Análise na Área de Logística

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

