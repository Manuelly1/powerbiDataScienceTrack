# Unidade 4: Power BI para Análise de Dados de Marketing

- **O que é marketing?** A unidade começa esclarecendo esse conceito, definido como o processo de **planejar e executar a concepção, o preço, a promoção e a distribuição de ideias, bens e serviços** com o objetivo de criar **trocas que satisfaçam tanto os objetivos individuais quanto os organizacionais**. O marketing é responsável por **atrair e manter clientes**, envolvendo atividades como **pesquisa de mercado**, **análise de concorrência**, **definição de estratégias** e **planejamento de campanhas publicitárias**.

## Principais KPIs de Marketing

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

## Mini-Projeto 1: Análise de Campanhas de Marketing

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

### Visão Cliente

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

### Visão Comportamento

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

    TotalGasto = SUMX(DadosMarketing, DadosMarketing[Gasto com Alimentos] + DadosMarketing[Gasto com Brinquedos] + DadosMarketing[Gasto com Eletronicos] + DadosMarketing[Gasto com Moveis] + DadosMarketing[Gasto com Utilidades] + DadosMarketing[Gasto com Vestuario])

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

### Visão da Performance das Campanhas

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

### Visão dos Padrões de Compra por Ponto de Venda

- Para esta visão, foram utilizados dois gráficos. O primeiro é o **gráfico de colunas agrupadas e linha**, que requer pelo menos três campos: eixo X, eixo Y da coluna e eixo Y da linha.  

- Nele, foram aplicados os seguintes campos: `País` no eixo X; no eixo Y da coluna, os campos relacionados aos gastos, como `Gasto com Alimentação`, `Gasto com Brinquedos`, entre outros, que são os valores exibidos no gráfico. Já no eixo Y da linha, foi adicionado o campo `ID` (contagem);

- **O que foi possível concluir com esse gráfico?**  

    - Ao observar a Espanha, nota-se que o maior gasto total é com eletrônicos. A linha indica que o país possui um total de **302 clientes**. Desse total, os clientes gastaram **94.282** com eletrônicos e **11.962** com utilidades, por exemplo. A mesma análise pode ser estendida aos demais países.

- O outro gráfico utilizado foi o **gráfico de linhas**, no qual o eixo Y recebeu o campo `TotalGasto`, a legenda foi composta pelo campo `País` e o eixo X representou o `Ano` proveniente do campo `Data Cadastro`;

- **O que foi possível analisar com esse?**  

    - Esse gráfico permitiu observar a **evolução do total gasto ao longo do tempo**, com cada linha representando um país;

    - Verifica-se que o comportamento entre os países é bastante semelhante: houve um **crescimento acentuado em 2020**, seguido por uma **queda em 2021** e uma **retomada do crescimento em 2022**. Algo que se deve, por exemplo, a pandemia que ocorreu nesse período.
