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

- Primeiramente, o professor começou fazendo uma **análise exploratória** da base e evidenciando alguns problemas, como valores ausentes, registros duplicados e outliers;

- A presença do termo `null` em campos como `Idade` e `Peso` indica que não há dados em alguns daqueles registros. Valor ausente pode ser ocasionado por inúmeros fatores, como técnicas aplicadas pelo próprio analista, algum problema no carregamento da base no sistema... 

- Posteriormente, para auxiliar ainda mais nessa análise, o professor buscou verificar a quantidade de registros da base, para isso adicionou uma tabela com o campo `ID_Cliente` (contagem), que retornou 502 registros. Porém, o professor alertou para outro possível problema: a presença de IDs duplicados, o que provocaria uma série de problemas, uma vez que um mesmo cliente poderia estar associado a mais de um ID etc. Portanto, ele adicionou o campo `ID_Cliente` na mesma tabela com a contagem distinta, que retornou apenas 496 IDs únicos, o que nos leva a crer que tem ID duplicado. 