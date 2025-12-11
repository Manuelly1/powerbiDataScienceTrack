# Limpeza e Manipulação de Dados com Power BI

## Correção dos Exercícios da Unidade 11

- Antes de tudo, ele conectou a base e examinou os dados. Posteriormente, adicionou uma **tabela** ao dashboard e colocou o campo `Idade` (média), depois `Idade` (mediana) e mostrou que não tinha a opção de moda, uma das limitações do Power BI. Antes de iniciar a unidade, eu fiz várias medidas e aproveitei este momento para verificar se os dados batiam;

- Algumas das medidas DAX criadas:

```dax

    Moda_Altura = 
        VAR TabelaFrequencia =
            SUMMARIZE(
                'dados_pacientes',
                'dados_pacientes'[altura(cm)], 
                "Frequencia", COUNTROWS('dados_pacientes')
            )
        VAR FreqMax =
            MAXX(TabelaFrequencia, [Frequencia])
        VAR ValoresModa =
            FILTER(TabelaFrequencia, [Frequencia] = FreqMax)
        RETURN
            CONCATENATEX(ValoresModa, 'dados_pacientes'[altura(cm)], ", ") 

    Moda_Idade = 
        VAR TabelaFrequencia =
            SUMMARIZE(
                'dados_pacientes',
                'dados_pacientes'[idade(anos)],
                "Frequencia", COUNTROWS('dados_pacientes')
            )
        VAR FreqMax =
            MAXX(TabelaFrequencia, [Frequencia])
        VAR ValoresModa =
            FILTER(TabelaFrequencia, [Frequencia] = FreqMax)
        RETURN
            CONCATENATEX(ValoresModa, 'dados_pacientes'[idade(anos)], ", ")

    Moda_Peso = 
        VAR TabelaFrequencia =
            SUMMARIZE(
                'dados_pacientes',
                'dados_pacientes'[peso(kg)],
                "Frequencia", COUNTROWS('dados_pacientes')
            )
        VAR FreqMax =
            MAXX(TabelaFrequencia, [Frequencia])
        VAR ValoresModa =
            FILTER(TabelaFrequencia, [Frequencia] = FreqMax)
        RETURN
            CONCATENATEX(ValoresModa, 'dados_pacientes'[peso(kg)], ", ")

    Moda_Tipo_Sanguineo = 
        VAR TabelaFrequencia =
            SUMMARIZE(
                'dados_pacientes',
                'dados_pacientes'[tipo_sanguineo], 
                "Frequencia", COUNTROWS('dados_pacientes')
            )
        VAR FreqMax =
            MAXX(TabelaFrequencia, [Frequencia])
        VAR ValoresModa =
            FILTER(TabelaFrequencia, [Frequencia] = FreqMax)
        RETURN
            CONCATENATEX(ValoresModa, 'dados_pacientes'[tipo_sanguineo], ", ") 
        
    Moda_Estado_Civil = 
        VAR TabelaFrequencia =
            SUMMARIZE(
                'dados_pacientes',
                'dados_pacientes'[estado_civil],  
                "Frequencia", COUNTROWS('dados_pacientes')
            )
        VAR FreqMax =
            MAXX(TabelaFrequencia, [Frequencia])
        VAR ValoresModa =
            FILTER(TabelaFrequencia, [Frequencia] = FreqMax)
        RETURN
            CONCATENATEX(ValoresModa, 'dados_pacientes'[estado_civil], ", ") 

```

- Para as variáveis categóricas `tipo_sanguineo` e `estado_civil`, utilizamos o macete explicado pelo professor: cada variável deve ser colocada em uma **tabela** auxiliar duas vezes, sendo que uma delas recebe a coluna de contagem;

- Depois disso, criamos uma medida para calcular a moda e adicionamos essa medida em um **cartão** no relatório, permitindo visualizar o valor exato com precisão;

- Em seguida, o professor comentou sobre o segundo exercício, que pedia a **média**, **variância** e **desvio padrão** das variáveis `idade(anos)`, `altura(cm)` e `peso(kg)` dos pacientes. Além disso, também era necessário calcular o **coeficiente de variação** para as três variáveis;

- O professor adicionou algumas **tabelas** ao relatório e repetiu o mesmo procedimento utilizado anteriormente: ele puxou o campo `idade(anos)` três vezes e aplicou, em cada instância, a média, a variância e o desvio padrão;

- No meu caso, como eu já havia criado as **medidas DAX** (que irei adicionar abaixo), aproveitei esse momento para conferi-las e validar se os valores retornados estavam corretos.


```dax

    Variancia_Idade = VAR.P('dados_pacientes'[idade(anos)])

    DesvioPadrao_Idade = STDEV.P('dados_pacientes'[idade(anos)])

    CV_Idade = 
        DIVIDE(
            STDEV.P('dados_pacientes'[idade(anos)]),
            AVERAGE('dados_pacientes'[idade(anos)])
        )

```

- Após as etapas acima, os exercícios foram concluídos.

---

## O Que é Feito na Limpeza e Manipulação de Dados?

- A limpeza e manipulação de dados são etapas cruciais no processo de análise e modelagem de dados. Essas atividades envolvem a organização, transformação e remoção de erros ou inconsistências nos dados para garantir que eles estejam prontos para serem utilizados em análises, visualizações ou aplicação de modelos de aprendizado de máquina. Algumas das principais tarefas incluem:

    - **Remoção de dados duplicados:** eliminar registros duplicados que podem distorcer a análise;

    - **Tratamento de valores ausentes:** substituir, remover ou estimar valores ausentes nos dados, usando métodos como média, mediana, interpolação ou outros algoritmos;

    - **Correção de erros de digitação e inconsistências:** identificar e corrigir erros de digitação, formatação e padronização dos dados;

    - **Conversação de tipos de dados:** transformar variáveis em tipos de dados apropriados, como numérico, categórico ou textual;

    - **Renomeação e reorganização de colunas:** ajustar os nomes das colunas para facilitar a compreensão e organizá-las de acordo com a necessidade da análise;

    - **Filtragem e seleção de dados:** extrair subconjuntos específicos de dados com base em critérios pré-determinados, como faixas de valores ou categorias;

    - **Discretização e binning:** converter variáveis contínuas em categorias ou agrupar dados em intervalos específicos para análise;

    - **Normalização e padronização:** ajustar a escala dos valores numéricos para facilitar a comparação e melhorar o desempenho de modelos de aprendizado de máquina;

    - **Transformação de variáveis:** criar novas variáveis a partir de outras existentes ou aplicar transformações matemáticas para simplificar análises ou melhorar a interpretação dos dados;

    - **Detecção e tratamento de outliers:** identificar e tratar valores extremos que podem afetar a análise ou a modelagem;

    - **Codificação de variáveis categóricas:** converter variáveis categóricas em formatos numéricos, como codificação one-hot ou ordinal, para serem utilizadas em modelos de aprendizado de máquina.

---

## Laboratório Prático 4 - Limpeza e Manipulação de Dados de Cadastro de Clientes no Power BI

### Análise Exploratória

- Primeiramente, o professor iniciou realizando uma **análise exploratória** da base e evidenciando alguns problemas, como valores ausentes, registros duplicados e outliers;

- A presença do termo `null` em campos como `Idade` e `Peso` indica que não há dados em determinados registros. Valores ausentes podem ocorrer por diversos motivos, como técnicas aplicadas pelo próprio analista, falhas no carregamento da base no sistema, entre outros;

- Posteriormente, para aprofundar a análise, o professor verificou a quantidade total de registros da base. Para isso, adicionou uma tabela com o campo `ID_Cliente` (contagem), que retornou 502 registros. Contudo, ele alertou sobre um possível problema: a presença de IDs duplicados, o que pode gerar inconsistências, já que um mesmo cliente poderia estar associado a mais de um ID. Assim, ele incluiu o campo `ID_Cliente` na mesma tabela, mas com contagem distinta, o que retornou apenas 496 IDs únicos, indicando que existem IDs duplicados;

- Além disso, o professor demonstrou um macete para identificar valores `null` e duplicados no Power Query. Para encontrar valores ausentes, basta selecionar a área que lista os valores da coluna, onde o `null` aparece logo no início, caso exista. Já para localizar duplicados, ele selecionou uma coluna, clicou no tipo de dado da coluna e utilizou a opção **Agrupar por**, que retorna a contagem de cada registro; se algum `ID_Cliente` aparecer mais de uma vez, é porque está duplicado;

- Em seguida, foi realizada a identificação de outliers. Para isso, o professor analisou um campo por vez, observando se existiam valores extremos. Ao selecionar o campo `Altura(cm)`, foi possível identificar valores como 20 cm e 278 cm, claramente atípicos. Esses valores impactam diversas operações estatísticas, como o cálculo da média. Para tratar esses outliers, cabe ao analista decidir (e justificar) se eles serão removidos, ajustados ou mantidos.

---

### Tratando Registros Duplicados

- Para isso, basta ir em **Transformar dados -> remover linhas -> remover duplicatas**. Em seguida, ao ir no relatório novamente, observa-se que atualizou para 496 IDs únicos.

---

### Tratando Valores Ausentes (*null*)

- O professor alertou que esse é um ponto mais complexo e que precisa ser corrigido rapidamente, pois impacta diretamente nas análises. A forma mais simples seria remover as linhas que possuem *null*, porém isso afetaria o resultado final, especialmente se a base contiver muitos valores ausentes;

- Uma alternativa é aplicar a **interpolação**, ou seja, preencher o valor nulo com algum outro valor. Antes disso, ele adicionou uma nova tabela ao dashboard para obter um resumo estatístico da coluna `Idade`. Colocou essa coluna cinco vezes no campo *Colunas* para, em cada uma delas, exibir: valor mínimo, média, desvio padrão, valor máximo e mediana. Com base nesses valores, o professor explicou que uma opção seria substituir o valor ausente pela média. Contudo, antes de usar a média, o ideal seria aplicar um teste estatístico para verificar a distribuição da variável `Idade`. Infelizmente, o Power BI não possui testes estatísticos de forma nativa, mas eles podem ser construídos via DAX, embora isso dê bastante trabalho, pois seria necessário consultar a documentação do teste e reproduzir toda a matemática. Usando Python ou R, isso seria bem mais simples;

- Para evitar esse esforço extra, o mais indicado é não usar a média, e sim a **mediana**. Porém, ao analisar o cliente com `id = 3`, um dos que possui valor *null*, observa-se que o peso dele é de apenas 44 kg, o que levanta a dúvida: "Será que realmente teria 40 anos?". O professor ressaltou que essa é exatamente a questão: ou você remove o registro inteiro ou o preenche com algum valor aproximado. Uma alternativa mais avançada seria criar um modelo de aprendizado de máquina capaz de aprender o padrão da variável `Idade` e prever um valor provável;

- Tanto para `Idade` quanto para `Peso`, que também apresentava valores ausentes, foi aplicada a mediana. Para fazer isso no **Power Query**, basta selecionar a coluna `Idade`, clicar com o botão direito em **Substituir Valores** e definir `null -> 40`. O mesmo procedimento foi aplicado para a coluna `Peso`.

---

### Visualizando e Tratando Outliers

- Antes de começar, o professor adicionou uma nova tabela e repetiu o mesmo processo realizado anteriormente com os campos `Idade` e `Peso`, porém agora para a variável `Altura`. Em seguida, foi feita uma interpretação inicial: o valor mínimo encontrado foi 146 cm (comum), enquanto o valor máximo foi 278 cm (incomum). Isso justificou uma pesquisa para verificar se esse valor poderia ser real. Ao pesquisar, constatou-se que a maior altura já registrada em um ser humano foi de 271 cm. Logo, o valor de 278 cm presente na base é um outlier (anomalia);

- Diante disso, é necessário tomar uma decisão (e todas elas envolvem riscos). Uma possibilidade é não fazer nada, mas isso afetaria a média e outras análises. Outra alternativa é remover os registros que possuem esse valor extremo, adicionando uma observação ao relatório, como: “Foram removidos X registros, pois não foi possível validar se a altura era real (pode ter sido erro de medição ou digitação)”. Também existe a alternativa de substituir os outliers pela mediana;

- Antes de qualquer ação, o professor destacou a importância de **visualizar** o outlier em um gráfico. O gráfico mais indicado seria o **boxplot**, pois mostra média, mediana, mínimo, máximo e quartis. Entretanto, o Power BI ainda não possui boxplot nativo. Ele existe apenas como visual R na galeria de gráficos, usando o pacote *ggplot2*. Como a ferramenta não oferece esse recurso prontamente, o professor criou uma série de medidas para auxiliar na visualização dos outliers por meio de gráficos. Foram criadas medidas de mediana, quartis e IQR (intervalo interquartil):

```dax

    MedianaAltura = MEDIAN(customers[Altura]) 
    Q1Altura = PERCENTILE.INC(customers[Altura], 0.25) 
    Q3Altura = PERCENTILE.INC(customers[Altura], 0.75) 
    IQRAltura = [Q3Altura] - [Q1Altura] 
    LimiteInferiorAltura = [Q1Altura] - 1.5 * [IQRAltura]   // Valores abaixo disso são outliers
    LimiteSuperiorAltura = [Q3Altura] + 1.5 * [IQRAltura]   // Valores acima disso são outliers

```

- Em seguida, em uma nova página, juntamente com a tabela de resumo da variável `Altura`, adicionou-se um **gráfico de dispersão**, definindo o `ID_Cliente` (sem resumir) no eixo X e `Altura` (sem resumir) no eixo Y. Assim, já é possível visualizar alguns pontos distantes do centro, ou seja, os outliers. Depois, foram adicionadas **linhas de referência** com as medidas calculadas anteriormente para documentar e justificar a decisão de substituição dos outliers pela mediana. Para isso, basta ir até o **terceiro ícone** (a lupa, referente à aba de Análise), selecionar Linha constante no eixo Y → Adicionar linha → clicar no fx e escolher a medida da mediana (repetindo o processo para as outras medidas). Dessa forma, ao relatar a decisão, basta comentar que essa é uma forma amplamente aceita na estatística para identificação de outliers: **qualquer valor acima do limite superior ou abaixo do limite inferior é considerado outlier**;

- Após visualizar, **foi possível identificar três pontos fora dos limites:** um deles era o de 204 cm. Nesse caso, cabe ao analista decidir se considera esse valor incomum ou não. No projeto, optou-se por manter esse registro, pois alturas nessa faixa são comuns em atletas. Portanto, apenas os outros dois valores (270 cm e 278 cm) foram substituídos. No Power Query, em `Altura` → Substituir Valores, substituiu-se 270 por 172 (mediana) e 278 por 172. Ao aplicar essas alterações, o gráfico foi atualizado automaticamente e os pontos deixaram de aparecer.

