# Unidade 5: Power BI para Análise de Dados Comerciais

- A **área comercial** de uma empresa é responsável por garantir a venda de produtos ou serviços da empresa e por conseguir novos clientes;

- Sendo assim, é o departamento responsável por estabelecer as **estratégias de vendas**, **realizar negociações**, **fechar contratos** e **acompanhar o desempenho das vendas**.

## Principais KPIs da Área Comercial

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

## Mini-Projeto 2: Dashboard Comercial - Performance de Vendas

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

### Relatório: Narrativa Inteligente

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

### Relatório: Principais Influenciadores de Vendas

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

### Relatório: Total de Venda por Categoria e Ponto de Venda (Gráfico de Faixas)

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

### Relatório: Performance dos Vendedores por Região

- Para este relatório, foi utilizado um **mapa com filtros**. Semelhante ao relatório anterior, o professor optou por demonstrá-lo em apenas uma página, pois essa é a forma mais indicada de apresentar esses elementos, garantindo uma visualização mais limpa, objetiva e legível;

- Foram aplicados os seguintes campos: 

    - `Estado` em **localização**;
    
    - `Vendedor` em **legenda**;
    
    - `Valor Venda` em **tamanho da bolha** (posteriormente ajustado para `Total Valor Venda`).

- Além disso, foi adicionado um filtro em `Total Valor Venda` maior que **30.000**, com o objetivo de destacar apenas os estados que apresentaram volumes de vendas mais elevados.

---

### Criando Menu/Índice para os Relatórios

- O professor recomendou a criação de um **índice (menu de navegação)** para facilitar o acesso entre as páginas dos relatórios, aproveitando a paginação de forma organizada e evitando a poluição visual da dashboard;

- Para criar o índice: **Inserir → Botões → Navigator → Navigator de Página**;

- A navegação entre as páginas ocorre utilizando **Ctrl + Clique**;

- Após inserir o menu, basta realizar as **formatações desejadas**, ajustando cores, tamanhos e posições conforme o estilo do relatório.

