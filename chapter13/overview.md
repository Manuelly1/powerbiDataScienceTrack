# Manipulação de Dados com Power Query M Language

## O que é a Power Query M Language?

- A linguagem M é uma linguagem de programação funcional e baseada em fórmulas, que é usada no Power Query (uma ferramenta de ETL presente no Power BI, Excel, dentre outros). Essa linguagem **permite que os usuários manipulem, transformem e preparem dados para análise e visualização**;

- Ela é projetada para ser fácil de aprender, especialmente para pessoas que têm experiência com o Excel. A sintaxe da linguagem é simples e concisa, o que permite realizar tarefas comuns de limpeza e transformação de dados de maneira rápida e eficiente;

- Algumas das principais características e funcionalidades da linguagem M incluem:

    - **Extração de dados:** A linguagem M permite extrair dados de várias fontes, como bancos de dados, arquivos de texto, APIs da Web etc;

    - **Transformação de dados:** Com ela, o analista pode realizar várias operações de transformação de dados, como filtrar, classificar, agrupar, mesclar, unir, dividir colunas etc;

    - **Funções personalizadas:** Essa linguagem permite que você crie funções personalizadas para atender às suas necessidades específicas de transformação de dados;

    - **Integração com o Power Query:** Ela é totalmente integrada ao Power Query Editor no Power BI, Excel e outras ferramentas da Microsoft, permitindo uma experiência de usuário simplificada.

---

## O que é Engenharia de Atributos (*Feature Engineering*)?

- É o **processo de criação, seleção e transformação de atributos** (variáveis/características) em um conjunto de dados. Essa técnica é usada para melhorar a performance dos modelos de aprendizado de máquina, além de tornar os dados mais informativos e relevantes para a análise;

- A engenharia de atributos envolve várias etapas e técnicas, incluindo:

    - **Seleção de atributos:** Identificar e selecionar os atributos mais importantes e relevantes para o problema em questão. Isso pode envolver a remoção de atributos com alta correlação, redundantes ou irrelevantes;

    - **Transformação de atributos:** Modificar ou transformar os atributos existentes para torná-los mais úteis para análise ou criação de modelos de Machine Learning. Isso pode incluir normalização, padronização, discretização, aplicação de funções logarítmicas ou exponenciais, entre outras;

    - **Criação de novos atributos:** Criar novos atributos a partir dos existentes, combinando-os ou aplicando funções matemáticas. Isso pode envolver a criação de atributos polinomiais, interações entre atributos, atributos derivados de funções matemáticas, entre outros;

    - **Tratamento de valores ausentes:** Lidar com valores ausentes (*missing values*) no conjunto de dados, substituindo-os por medidas estatísticas, como média, mediana ou moda, ou utilizando técnicas mais avançadas, como a interpolação ou a imputação por modelos de aprendizado de máquina;

    - **Codificação de variáveis categóricas:** Converter variáveis categóricas em representações numéricas que possam ser utilizadas pelos modelos de aprendizado de máquina. Isso pode incluir a aplicação de técnicas como one-hot encoding, ordinal encoding ou labelencoding.     

---

## Laboratório 5 - Engenharia de Atributos com Linguagem M no Power BI

- Primeiramente, o professor abriu a base e levantou o seguinte questionamento: *"As colunas presentes no arquivo são realmente ideais para o trabalho de análise que o analista precisa realizar com esses dados?"*, a resposta depende do problema de negócio, das perguntas que deverão ser respondidas, do tipo de análise que será feita e até mesmo se os dados serão utilizados ou não em modelos de Machine Learning. Conforme as necessidades do projeto, o analista deve realizar a **engenharia de atributos**, ou seja, criar novas colunas, modificar colunas existentes, dividir colunas, entre outras transformações.

---

### Análise Exploratória

- Assim que a base é carregada, já é perceptível um problema: na coluna `Idade` há registros contendo `"?"`, que representam valores ausentes, problema que também será tratado com a linguagem M;

- No Power Query, ao selecionar algumas das etapas aplicadas, aparece um código acima da tabela. Esse código é escrito na **linguagem M**. Todas as operações realizadas no Power Query geram automaticamente código M, que é o que o Power BI utiliza internamente para aplicar as transformações. Contudo, também é possível escrever/editar esse código manualmente. Como fazer isso? Existem duas formas: editar diretamente na caixa superior ou acessar **Exibição → Editor Avançado**;

- Durante essa etapa de análise, ao observar a coluna `ID_Cliente`, nota-se que o tipo atribuído foi **texto**, pois a coluna contém uma combinação de letras e números. Já a coluna `Idade` também foi classificada como **texto**, devido à presença do caractere `"?"`. Esse comportamento causa estranhamento, pois o esperado é que `Idade` seja do tipo numérico.

---

### Verificando a Qualidade dos Dados

- Para evitar depender de ferramentas externas, é possível verificar a qualidade dos dados diretamente no Power Query acessando **Exibição → Qualidade da coluna**. Assim, o Power BI automaticamente avalia cada coluna e exibe um resumo sobre sua qualidade. Porém, apesar de essa verificação oferecer uma visão inicial, cabe ao analista analisar cuidadosamente os resultados. Neste exemplo, a coluna `Idade` aparece com **100% de dados válidos**, embora saibamos que isso não corresponde à realidade;

- Esse erro ocorre porque o Power BI classificou a coluna `Idade` como **texto**, devido à presença do caractere `"?"`. Como texto, o valor `"?"` não é considerado inválido, por isso o relatório aponta 100% de validade. Entretanto, se o analista tentar executar operações numéricas nessa coluna, elas falharão. Isso evidencia a importância de sempre verificar o tipo de dados atribuído a cada coluna;

- Em resumo, mesmo que o relatório de qualidade indique que uma coluna está 100% válida, o analista deve revisar manualmente e garantir que o tipo de dado esteja coerente com o tipo de análise que será realizada.

---

### Verificando a Distribuição dos Dados

- Assim como na verificação da qualidade, é possível analisar a distribuição dos dados diretamente no Power Query. Para isso, basta acessar **Exibição → Distribuição de colunas**. O Power BI exibirá um gráfico que representa a frequência dos valores em cada variável;

- Enquanto a visualização de **qualidade** ajuda o analista a identificar possíveis problemas na base (como valores inválidos ou ausentes), a visualização de **distribuição** mostra a organização geral dos dados, permitindo avaliar, por exemplo, se a variável apresenta distribuição assimétrica, se há concentração de valores em determinadas faixas ou se existem muitos valores únicos;

- O tipo de gráfico exibido depende do tipo de dado da coluna (numérica ou categórica). Essa visualização também ajuda a identificar valores exclusivos, valores distintos e padrões na distribuição, contribuindo para uma melhor compreensão da variável antes da etapa de transformação ou modelagem.

---

### Limpeza de Dados com Linguagem M

- Esta etapa foi realizada no Power Query, especificamente em **Exibição → Editor avançado**. O Editor Avançado exibe todo o bloco de código M correspondente às etapas já aplicadas pela ferramenta até aquele momento;

- O código inicia com o bloco `let`, que pode ser interpretado como “deixe isso acontecer”. Dentro dele são declaradas todas as etapas de transformação. Já o bloco `in` indica qual foi a última etapa executada — ou seja, o passo final que será retornado. No momento em que o código foi aberto, apenas três etapas haviam sido aplicadas automaticamente pelo Power BI: `Fonte` (carregamento do arquivo), `Cabeçalhos Promovidos` e `Tipo Alterado`. O script estava assim:

```m

    let
        Fonte = Csv.Document(File.Contents("C:\Users\Manuelly\Desktop\curso-data-science\cap13\customers_dataset\customers.csv"), 
            [Delimiter=",", Columns=10, Encoding=65001, QuoteStyle=QuoteStyle.None]),
        #"Cabeçalhos Promovidos" = Table.PromoteHeaders(Fonte, [PromoteAllScalars=true]),
        #"Tipo Alterado" = Table.TransformColumnTypes(#"Cabeçalhos Promovidos",
            {{"ID_Cliente", type text}, {"Idade", type text}, {"Peso", Int64.Type}, {"Altura", Int64.Type},
            {"Estado Civil", type text}, {"Estado", type text}, {"Limite de Credito", Int64.Type},
            {"Valor Desconto", Int64.Type}, {"Valor Compra", Int64.Type}, {"Tipo de Cliente", type text}})
    in
        #"Tipo Alterado"


```

- Em seguida, iniciou-se o processo de inclusão das operações personalizadas (inseridas dentro do mesmo bloco let). A primeira operação foi substituir o valor `"?"` da coluna `Idade`, utilizando a função `Table.ReplaceValue`. O caractere foi substituído pelo valor 45 (apenas um valor provisório para fins didáticos, pois na prática seria utilizado a média ou mediana da coluna). O script atual ficou assim:

```m

    let
        Fonte = Csv.Document(File.Contents("C:\Users\Manuelly\Desktop\curso-data-science\cap13\customers_dataset\customers.csv"),[Delimiter=",", Columns=10, Encoding=65001, QuoteStyle=QuoteStyle.None]),
        #"Cabeçalhos Promovidos" = Table.PromoteHeaders(Fonte, [PromoteAllScalars=true]),
        #"Tipo Alterado" = Table.TransformColumnTypes(#"Cabeçalhos Promovidos",{{"ID_Cliente", type text}, {"Idade", type text}, {"Peso", Int64.Type}, {"Altura", Int64.Type}, {"Estado Civil", type text}, {"Estado", type text}, {"Limite de Credito", Int64.Type}, {"Valor Desconto", Int64.Type}, {"Valor Compra", Int64.Type}, {"Tipo de Cliente", type text}}),

        // substituindo valor
        #"Valor Substituido"= Table.ReplaceValue(#"Tipo Alterado", "?", "45", Replacer.ReplaceText, {"Idade"})
    in
        #"Valor Substituido"

```

- Posteriormente, o professor aplicou e salvou o processo. Agora, a operação **`Valor Substituído`** aparece na lista de *Etapas Aplicadas*, indicando que a transformação foi registrada e passa a fazer parte do fluxo de limpeza da base.

---

### Removendo Colunas com Linguagem M

- A coluna `Estado Civil` não é mais necessária para a análise, portanto, pode ser removida sem afetar o resultado final. Para isso, adiciona-se uma nova etapa ao código M utilizando a função `Table.RemoveColumns`. O bloco de código fica da seguinte forma:

```m

    let
        Fonte = Csv.Document(File.Contents("C:\Users\Manuelly\Desktop\curso-data-science\cap13\customers_dataset\customers.csv"),[Delimiter=",", Columns=10, Encoding=65001, QuoteStyle=QuoteStyle.None]),
        #"Cabeçalhos Promovidos" = Table.PromoteHeaders(Fonte, [PromoteAllScalars=true]),
        #"Tipo Alterado" = Table.TransformColumnTypes(#"Cabeçalhos Promovidos",{{"ID_Cliente", type text}, {"Idade", type text}, {"Peso", Int64.Type}, {"Altura", Int64.Type}, {"Estado Civil", type text}, {"Estado", type text}, {"Limite de Credito", Int64.Type}, {"Valor Desconto", Int64.Type}, {"Valor Compra", Int64.Type}, {"Tipo de Cliente", type text}}),

        // substituindo valor
        #"Valor Substituido"= Table.ReplaceValue(#"Tipo Alterado", "?", "45", Replacer.ReplaceText, {"Idade"}),

        // removendo coluna
        #"Coluna Removida" = Table.RemoveColumns(#"Valor Substituido", {"Estado Civil"})

    in
        #"Coluna Removida"

```
---

### Adicionando Novas Colunas com Linguagem M

- Na base existem duas colunas: **`Valor Desconto`** e **`Valor Compra`**. Surge então a dúvida: *“A coluna `Valor Compra` já representa o valor final com o desconto aplicado, ou corresponde ao valor antes do desconto?”*. Para responder isso, é necessário consultar a **área de negócios da empresa**. Se ninguém souber informar, **não utilize os dados**, pois qualquer cálculo feito poderá gerar análises incorretas;

- Supondo que a área de negócios informou que **`Valor Compra` é o valor antes do desconto**, ou seja, o valor bruto, então precisamos criar uma nova coluna chamada **`Valor Final`**, na qual o desconto será aplicado;

- O código M para criar essa nova coluna poderia ser assim:

```m

    let
        Fonte = Csv.Document(File.Contents("C:\Users\Manuelly\Desktop\curso-data-science\cap13\customers_dataset\customers.csv"),[Delimiter=",", Columns=10, Encoding=65001, QuoteStyle=QuoteStyle.None]),
        #"Cabeçalhos Promovidos" = Table.PromoteHeaders(Fonte, [PromoteAllScalars=true]),
        #"Tipo Alterado" = Table.TransformColumnTypes(#"Cabeçalhos Promovidos",{{"ID_Cliente", type text}, {"Idade", type text}, {"Peso", Int64.Type}, {"Altura", Int64.Type}, {"Estado Civil", type text}, {"Estado", type text}, {"Limite de Credito", Int64.Type}, {"Valor Desconto", Int64.Type}, {"Valor Compra", Int64.Type}, {"Tipo de Cliente", type text}}),

        // substituindo valor
        #"Valor Substituido"= Table.ReplaceValue(#"Tipo Alterado", "?", "45", Replacer.ReplaceText, {"Idade"}),

        // removendo coluna
        #"Coluna Removida" = Table.RemoveColumns(#"Valor Substituido", {"Estado Civil"}),

        // adicionando coluna
        #"Coluna Adicionada" = Table.AddColumn(#"Coluna Removida", "Valor Final", each [Valor Compra] - [Valor Desconto])

    in
        #"Coluna Adicionada"

```

---

### Dividindo Coluna com Linguagem M

- A coluna `ID_Cliente`, por exemplo, foi preenchida com letras e números, o que leva a crer que esse campo possui duas informações em uma única coluna. O professor alerta que **isso deve ser investigado junto à área de negócios da empresa** para confirmar se realmente representam dois códigos distintos e/ou se existe alguma documentação oficial que descreva essa estrutura. **Exemplo:** os 4 primeiros caracteres podem indicar um código e os 4 últimos o próprio ID. É importante sempre validar antes de executar qualquer transformação, nada de suposições;

- Considerando que essa coluna realmente precisa ser dividida, serão criadas duas novas colunas: uma contendo os 4 primeiros caracteres e outra contendo os 4 últimos. O script fica assim:

```m

    let
        Fonte = Csv.Document(File.Contents("C:\Users\Manuelly\Desktop\curso-data-science\cap13\customers_dataset\customers.csv"),[Delimiter=",", Columns=10, Encoding=65001, QuoteStyle=QuoteStyle.None]),
        #"Cabeçalhos Promovidos" = Table.PromoteHeaders(Fonte, [PromoteAllScalars=true]),
        #"Tipo Alterado" = Table.TransformColumnTypes(#"Cabeçalhos Promovidos",{{"ID_Cliente", type text}, {"Idade", type text}, {"Peso", Int64.Type}, {"Altura", Int64.Type}, {"Estado Civil", type text}, {"Estado", type text}, {"Limite de Credito", Int64.Type}, {"Valor Desconto", Int64.Type}, {"Valor Compra", Int64.Type}, {"Tipo de Cliente", type text}}),

        // substituindo valor
        #"Valor Substituido"= Table.ReplaceValue(#"Tipo Alterado", "?", "45", Replacer.ReplaceText, {"Idade"}),

        // removendo coluna
        #"Coluna Removida" = Table.RemoveColumns(#"Valor Substituido", {"Estado Civil"}),

        // adicionando coluna
        #"Coluna Adicionada" = Table.AddColumn(#"Coluna Removida", "Valor Final", each [Valor Compra] - [Valor Desconto]),

        // dividindo coluna
        #"Dividir Coluna pela Posicao" = Table.SplitColumn(#"Coluna Adicionada", "ID_Cliente", Splitter.SplitTextByPositions({0,4}, false), {"ID_Cliente.1", "ID_Cliente.2"}),
        #"Coluna Dividida" = Table.TransformColumnTypes(#"Dividir Coluna pela Posicao", {{"ID_Cliente.1", type text}, {"ID_Cliente.2", Int64.Type}})

    in
        #"Coluna Dividida"

```

---

### Ajustando Nome de Coluna com Linguagem M

- Na seção anterior foram criadas as colunas `ID_Cliente.1` e `ID_Cliente.2`, porém esses nomes não são claros para o analista nem para outras pessoas que possam consultar o relatório. Por isso, é recomendável renomeá-las para algo mais descritivo e fácil de entender;

- O script fica assim:

```m

    let
        Fonte = Csv.Document(File.Contents("C:\Users\Manuelly\Desktop\curso-data-science\cap13\customers_dataset\customers.csv"),[Delimiter=",", Columns=10, Encoding=65001, QuoteStyle=QuoteStyle.None]),
        #"Cabeçalhos Promovidos" = Table.PromoteHeaders(Fonte, [PromoteAllScalars=true]),
        #"Tipo Alterado" = Table.TransformColumnTypes(#"Cabeçalhos Promovidos",{{"ID_Cliente", type text}, {"Idade", type text}, {"Peso", Int64.Type}, {"Altura", Int64.Type}, {"Estado Civil", type text}, {"Estado", type text}, {"Limite de Credito", Int64.Type}, {"Valor Desconto", Int64.Type}, {"Valor Compra", Int64.Type}, {"Tipo de Cliente", type text}}),

        // substituindo valor
        #"Valor Substituido"= Table.ReplaceValue(#"Tipo Alterado", "?", "45", Replacer.ReplaceText, {"Idade"}),

        // removendo coluna
        #"Coluna Removida" = Table.RemoveColumns(#"Valor Substituido", {"Estado Civil"}),

        // adicionando coluna
        #"Coluna Adicionada" = Table.AddColumn(#"Coluna Removida", "Valor Final", each [Valor Compra] - [Valor Desconto]),

        // dividindo coluna
        #"Dividir Coluna pela Posicao" = Table.SplitColumn(#"Coluna Adicionada", "ID_Cliente", Splitter.SplitTextByPositions({0,4}, false), {"ID_Cliente.1", "ID_Cliente.2"}),
        #"Coluna Dividida" = Table.TransformColumnTypes(#"Dividir Coluna pela Posicao", {{"ID_Cliente.1", type text}, {"ID_Cliente.2", Int64.Type}}),

        // ajustando nome de coluna
        #"Colunas Renomeadas" = Table.RenameColumns(#"Coluna Dividida", {{"ID_Cliente.1", "Codigo"}, {"ID_Cliente.2", "ID"}})

    in
        #"Colunas Renomeadas"

```

---

### Coluna Condicional com Linguagem M

- Suponha que a área de negócios solicitou um novo relatório para identificar a proporção de clientes que recebem **desconto especial**. Ao analisar os dados, percebe-se que não existe uma coluna indicando esse desconto. Entretanto, a área esclarece a regra de negócio:  

    - Cliente **bronze** → recebe 5% de desconto;

    - Cliente **prata** → recebe 10%;

    - Cliente **ouro** → recebe 15%;

    - Cliente **diamante** → recebe 20%.

- Dessa forma, cabe ao analista criar uma nova coluna com base nessas condições, usando a Linguagem M, por exemplo. O script completo:

```m

    let
        Fonte = Csv.Document(File.Contents("C:\Users\Manuelly\Desktop\curso-data-science\cap13\customers_dataset\customers.csv"),[Delimiter=",", Columns=10, Encoding=65001, QuoteStyle=QuoteStyle.None]),
        #"Cabeçalhos Promovidos" = Table.PromoteHeaders(Fonte, [PromoteAllScalars=true]),
        #"Tipo Alterado" = Table.TransformColumnTypes(#"Cabeçalhos Promovidos",{{"ID_Cliente", type text}, {"Idade", type text}, {"Peso", Int64.Type}, {"Altura", Int64.Type}, {"Estado Civil", type text}, {"Estado", type text}, {"Limite de Credito", Int64.Type}, {"Valor Desconto", Int64.Type}, {"Valor Compra", Int64.Type}, {"Tipo de Cliente", type text}}),

        // substituindo valor
        #"Valor Substituido"= Table.ReplaceValue(#"Tipo Alterado", "?", "45", Replacer.ReplaceText, {"Idade"}),

        // removendo coluna
        #"Coluna Removida" = Table.RemoveColumns(#"Valor Substituido", {"Estado Civil"}),

        // adicionando coluna
        #"Coluna Adicionada" = Table.AddColumn(#"Coluna Removida", "Valor Final", each [Valor Compra] - [Valor Desconto]),

        // dividindo coluna
        #"Dividir Coluna pela Posicao" = Table.SplitColumn(#"Coluna Adicionada", "ID_Cliente", Splitter.SplitTextByPositions({0,4}, false), {"ID_Cliente.1", "ID_Cliente.2"}),
        #"Coluna Dividida" = Table.TransformColumnTypes(#"Dividir Coluna pela Posicao", {{"ID_Cliente.1", type text}, {"ID_Cliente.2", Int64.Type}}),

        // ajustando nome de coluna
        #"Colunas Renomeadas" = Table.RenameColumns(#"Coluna Dividida", {{"ID_Cliente.1", "Codigo"}, {"ID_Cliente.2", "ID"}}),

        // coluna condicional
        #"Coluna Condicional Adicionada" = Table.AddColumn(#"Colunas Renomeadas", "% Desconto Especial", each if [Tipo de Cliente] = "Bronze" then 5 else if [Tipo de Cliente] = "Prata" then 10 else if [Tipo de Cliente] = "Ouro" then 15 else if [Tipo de Cliente] = "Diamante" then 20 else 0)

    in
        #"Coluna Condicional Adicionada"

```

---

### Ajustando a Escala dos Dados com Transformação Logarítmica com Linguagem M


