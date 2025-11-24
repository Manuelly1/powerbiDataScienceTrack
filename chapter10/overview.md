# Unidade 10: Power BI para Análise de Dados do Mercado de Ações

- **O que é o mercado de ações?** É um sistema no qual as empresas vendem frações de sua propriedade (chamadas ações) para investidores, que por sua vez se tornam proprietários parciais da empresa. Quando as empresas têm lucro, os acionistas também recebem uma parte desses lucros na forma de **dividendos**;

- Além disso, o valor das ações pode subir ou descer com base em vários fatores, como desempenho financeiro da empresa, mudanças na economia ou na indústria em que a empresa opera, bem como decisões políticas e regulatórias;

- Os **investidores** compram e vendem ações no mercado de ações, geralmente usando uma corretora ou plataforma de negociação online para fazer as transações. Esse mercado é comumente visto como um indicador da saúde econômica geral de um país.

---

## Interpretando Dados do Mercado de Ações

- Nesta unidade vamos  trabalhar  com  dados  reais  extraídos  do  portal  da  **Nasdaq**.  A NASDAQ  (National  Association  of  Securities  Dealers  Automated  Quotations)  é  uma  bolsa  de valores eletrônica americana, fundada em 1971. É a segunda maior bolsa de valores do mundo em termos de capitalização de mercado, atrás apenas da Bolsa de Valores de Nova York (NYSE);

- A NASDAQ é conhecida por ser a bolsa de valores onde são negociadas principalmente as ações de empresas de tecnologia e inovação, como Apple, Microsoft, Amazon, Facebook, IBM e Alphabet (a holding da Google);

- É uma bolsa de valores eletrônica, o que significa que as negociações são realizadas através de sistemas de computador e redes de telecomunicações. A NASDAQ é pioneira no uso de tecnologia para a realização de negociações, como a utilização de telas de computador para exibir cotações em tempo real e a implementação do sistema de negociação eletrônico;

- Os  dados  da  NASDAQ  incluem  várias  colunas,  cada  uma  fornecendo  informações específicas sobre o preço e o volume de negociação das ações negociadas no mercado. Aqui está uma descrição do que cada uma dessas colunas significa:

    - **Coluna  `Date`:**  Esta  coluna  fornece  a  data  em  que  a  ação  foi  negociada  na NASDAQ;
    
    - **Coluna  `Close/Last`  (Fechamento/Último  Preço):**  Esta  coluna  fornece  o  preço  de fechamento  da  ação  na  NASDAQ  no  final  do  dia  de  negociação.  O  preço  de fechamento é o último preço pelo qual a ação foi negociada naquele dia;
    
    - **Coluna `Volume`:** Esta coluna indica o número total de ações negociadas durante o dia. Isso pode incluir várias transações feitas por um ou mais investidores;
    
    - **Coluna `Open` (Preço de Abertura):** Esta coluna indica o preço de abertura da ação na NASDAQ no início do dia de negociação. O preço de abertura é o primeiro preço pelo qual a ação foi negociada naquele dia;
    
    - **Coluna `High` (Preço Máximo) e `Low` (Preço Mínimo):** Estas colunas indicam o preço máximo e mínimo que a ação foi negociada naquele dia. O preço máximo é o preço mais alto pelo qual a ação foi negociada durante o dia, enquanto o preço mínimo é o preço mais baixo pelo qual a ação foi negociada.

---

## Mini-Projeto 6 - Dashboard Analítico do Mercado de Ações com Narrativa Inteligente

- Após baixar a base de dados e conectá-la à ferramenta, realizei a formatação da coluna `Data` para que a hierarquia de datas fosse exibida corretamente. Para isso, acessei **Transformar dados** e utilizei a opção **Alterar tipo com base na localidade**, pois o formato original da data estava incompatível;

- O professor, antes de tudo, buscou demonstrar como **extrair dados reais para compor o nosso portfólio de projetos**. Inicialmente, ele acessou o site da NASDAQ → *Market Activity* → *Stocks* → digitou o nome de uma empresa → *Historical Quotes* → selecionou o período desejado e realizou o download dos dados;

- Como o objetivo deste dashboard não era trabalhar em tempo real, foi utilizada a base (`stock_market/market.xlsx`) disponível no repositório. Após realizar as formatações necessárias, partiu-se para a primeira questão do roteiro: **"Qual o total de volume negociado de ações ao longo do tempo para as 5 empresas que estão sendo analisadas?"**.;

    > O professor destacou que, ao se mencionar a expressão **“ao longo do tempo”**, o analista deve automaticamente associá-la à construção de uma linha do tempo. Assim, foi escolhido o **gráfico de área**, por ser mais indicado para representar totais, em comparação ao gráfico de linhas. Foram adicionados `Data` no eixo X e `Volume` no eixo Y. Porém, observou-se que as colunas não estavam sendo reconhecidas como numéricas após a formatação da data. Para corrigir isso, foi necessário ajustar o tipo de dado de cada coluna pelo ícone correspondente, da mesma forma que foi feito com a coluna de data.

- Para o próximo item: **"Qual o valor médio de abertura (Open), mais alto (High), mais baixo (Low) e de fechamento (Close) das ações de todas as empresas para todos os meses do período de dados analisado (1 ano em nosso exemplo)? Mostre no formato de tabela"**, foi inserida uma **tabela**;

    > O professor pontuou que o roteiro solicita o valor médio por mês, porém a base contém dados dos anos de 2022 e 2023. Caso fosse exibido apenas o mês isoladamente, o usuário não conseguiria identificar a qual ano ele se refere. Portanto, mesmo que a questão mencione somente o mês, neste contexto é mais adequado incluir também o ano. Dessa forma, nas colunas da tabela foram adicionados `Data` (Ano e Mês), seguidos dos campos `Open`, `High`, `Low`, `Close` e `Volume`, todos configurados para exibir a média. Por fim, foi adicionada uma segmentação de dados para permitir o filtro por empresa.

- A terceira questão: **"Qual a variação da média do valor de fechamento (Close) das ações de todas as empresas ao longo do tempo, mês a mês?"** foi desenvolvida da seguinte forma: inicialmente, foi selecionado o **gráfico de área empilhado** e adicionado o campo `Data` (considerando apenas o mês) no eixo X e `Close` (média) no eixo Y. Além disso, como a análise deveria ser feita por empresa, o campo `Empresa` foi incluído na legenda. Dessa forma, o gráfico passou a exibir a média do valor de fechamento das ações de cada empresa mês a mês;

- Contudo, o objetivo era visualizar a **variação da média**, e não apenas o valor médio em si. Portanto, foi necessário realizar um cálculo adicional. Para isso, utilizou-se o recurso de **Time Intelligence** (Inteligência de Dados Temporais), que é aplicado quando se trabalha com medidas que variam ao longo do tempo. Nesse caso, o valor de fechamento (Close) representa uma série temporal, pois é um dado que se modifica continuamente ao longo dos períodos;

- Para criar essa variação, o professor acessou a parte superior do Power BI → **Medida rápida** → Cálculo → **Inteligência de dados temporais** → *Alteração de mês a mês*. Em seguida, configurou os parâmetros da seguinte forma:

    - Valor base: `Close` (média);
    
    - Data: `Data`;
    
    - Número de períodos: 1 (para analisar a variação de um mês para o outro).

- Após a criação da medida, o campo `Close` foi removido do eixo Y e substituído pela nova medida gerada, permitindo assim visualizar corretamente a variação da média do valor de fechamento das ações ao longo do tempo, mês a mês;

- Para auxiliar o usuário na interpretação das informações, foi adicionado o elemento **Narrativa**, responsável por gerar uma narrativa inteligente, ou seja, um resumo automático que descreve e contextualiza os principais insights obtidos a partir dos gráficos presentes no dashboard;

- Por último, foi incluída outra **segmentação de dados**, desta vez referente ao **mês**, permitindo ao usuário filtrar as informações exibidas e analisar o comportamento das ações de forma mais específica ao longo do tempo.

