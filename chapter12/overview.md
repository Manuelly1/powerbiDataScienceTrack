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

