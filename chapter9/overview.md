# Unidade 9: Power BI para Análise de Dados Contábeis

- **O que são ciências contábeis?** São um campo de estudo que envolve o registro, classificação e análise de transações financeiras de uma empresa ou organização. Essas transações incluem compras, vendas, pagamentos, recebimentos, investimentos, entre outros. Os profissionais dessa área usam técnicas e ferramentas específicas para registrar e organizar informações financeiras, como balanços, demonstrativos de resultados, fluxo de caixa e relatórios contábeis.

---

## Os Principais Relatórios em Ciências Contábeis

- Os principais relatórios são:

    - **Balanço patrimonial (BP):** é um relatório que apresenta a posição financeira da empresa em um determinado momento. Ele mostra os ativos (bens e direitos) e passivos (obrigações) da empresa, bem como o patrimônio líquido;

    - **Demonstração de resultado do exercício (DRE):** é um relatório que apresenta o resultado das operações da empresa durante um período de tempo. Ele mostra as receitas, despesas e lucro líquido (ou prejuízo) da empresa;

    - **Demonstração do fluxo de caixa (DFC):** é um relatório que apresenta o fluxo de caixa da empresa durante um período de tempo. Ele mostra as entradas e saídas de caixa da empresa e o saldo de caixa no final do período;

    - **Demonstrativo de lucros ou prejuízos acumulados (DLPA):** esse importante relatório contábil indica as mudanças e aplicações do patrimônio líquido de uma empresa durante o período considerado, permitindo identificar a origem do recurso e averiguar sua gestão. Na prática, o DLPA deriva dos resultados obtidos no DRE e no balanço patrimonial, é obrigatório às sociedades limitadas, evidencia lucros e prejuízos e ajuda a avaliar se o investimento é adequado e rentável;

    - **Relatório de análise de desempenho:** é um relatório que apresenta uma análise detalhada dos resultados financeiros da empresa, comparando com períodos anteriores e com outras empresas do mesmo setor;

    - **Notas explicativas:** são informações adicionais que acompanham os relatórios financeiros e fornecem detalhes sobre as políticas contábeis da empresa, suas operações e outras informações relevantes. Essas notas ajudam a interpretar os relatórios financeiros e a entender melhor a situação financeira da empresa.

---

## O que é um Balanço Patrimonial?

- É um relatório financeiro que apresenta a posição financeira de uma empresa em um determinado momento, geralmente no final do ano fiscal ou em um intervalo de tempo específico;

- Ele apresenta a situação dos ativos, passivos e patrimônio líquido da empresa;
    
    - Os **ativos** são bens e direitos que a empresa possui, como dinheiro em caixa, contas a receber, estoques, imóveis, veículos, entre outros;
    
    - Os **passivos** são as obrigações, como empréstimos, contas a pagar, impostos, entre outros;
    
    - O **patrimônio líquido** representa os recursos próprios da empresa, ou seja, a diferença entre ativos e passivos.

- O BP é dividido em 2 partes principais: uma que apresenta os ativos, e outra que apresenta os passivos e o patrimônio líquido. O **objetivo** é mostrar que a soma dos ativos é igual à soma dos passivos mais o patrimônio líquido, ou seja, que o PL representa a diferença entre os recursos que a empresa possui e as suas obrigações.

---

## Laboratório Prático 3: Balanço Patrimonial com Visual de Matrix no Power BI

- Após carregar a base, foi selecionado o visual **Matrix** (que utiliza hierarquia, diferente da Tabela). Em **Linhas**, foram adicionados: `Tipo`, `Conta Nível 1`, `Conta Nível 2`, `Conta Nível 3` e `Conta Nível 4`. Em **Valores**, foram incluídos: `Ano_2019`, `Ano_2020`, `Ano_2021`, `Ano_2022` e `Ano_2023`. Em seguida, foi clicado com o botão direito no primeiro elemento da hierarquia e escolhida a opção **Expandir → Todos**;

- Depois disso, foram realizados ajustes de formatação para melhorar a legibilidade da matrix, incluindo aumento do tamanho da fonte, mudanças no layout e renomeação das colunas (por exemplo, de `Ano_2019` para `2019`);

- Na sequência, o professor demonstrou a navegação pela hierarquia usando o botão direito. Ele também explicou os botões localizados na parte superior do visual: a seta apontando para cima realiza o **drill up**, retornando ao nível superior da hierarquia; o ícone com duas setas para baixo navega para o próximo nível; e o ícone com a seta bifurcada expande todos os campos para o nível imediatamente inferior;

- Já a seta apontando para baixo habilita o **drill down**, permitindo descer na hierarquia a partir de um elemento específico. Ao clicar nela, o Power BI permite explorar somente a parte selecionada, exibindo seus detalhes enquanto mantém a estrutura hierárquica;

- Posteriormente, o professor mostrou como **alterar o layout de nível** acessando: **Formatar visual → Predefinições de layout → Recuo**. Nessa opção, é possível ajustar o espaçamento da hierarquia para evidenciar a diferença entre os níveis. O valor padrão é 10, mas o professor aumentou para 30;

- Além disso, o professor deu uma dica: caso o usuário queira visualizar apenas os totais ao longo dos anos, pode acessar **Formatar visual → Predefinições de layout → Valores → Opções** e ativar a opção de **alternar valores para linhas**. Porém, é importante destacar que isso altera a proposta do Balanço Patrimonial, pois passa a exibir apenas os totais;

- Em seguida, para melhorar a apresentação do Balanço Patrimonial, o professor mostrou como adicionar um **gráfico de barras dentro das células** da matriz. Para isso, selecionou a matriz e acessou: **Formatar visual → Elementos da célula**. Nessa área aparecem as séries (as colunas), e cada série pode ter sua formatação personalizada, como cor de fundo e outros estilos;

- O professor ativou a opção **Barra de dados**, pois ela facilita a interpretação visual: valores positivos podem ser exibidos em verde e valores negativos em vermelho, ajudando a audiência a identificar rapidamente os resultados. A largura das barras é proporcional aos valores, mas isso também pode ser ajustado manualmente. Vale lembrar que o Power BI exibe barras **apenas em células com valores**, não em subtotais;

- Por último, ele deixou como desafio cada um explorar outras métricas e relatórios para aplicar no dashboard.

