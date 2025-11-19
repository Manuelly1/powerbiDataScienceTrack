# Unidade 6: Power BI para Análise de Dados de RH

- **Qual a função da área de Recursos Humanos?** Gerenciar o capital humano da empresa, cuidando de todo o ciclo de vida do colaborador, desde o recrutamento e seleção até a demissão, além de administrar benefícios, folha de pagamento e garantir o cumprimento da legislação trabalhista, atuando como ponte entre os interesses da empresa e dos funcionários para promover um bom clima organizacional, engajamento e desenvolvimento profissional. 

## Principais KPIs na Área de RH

- São indicadores que ajudam a avaliar o sucesso da área:

    - **Taxa de rotatividade:** mede a frequência com que os funcionários estão deixando a empresa, o que pode indicar problemas com o ambiente de trabalho, remuneração ou oportunidades de desenvolvimento;

    - **Satisfação do funcionário:** mede o grau de satisfação dos funcionários com relação ao trabalho, remuneração, ambiente de trabalho e oportunidades de desenvolvimento;

    - **Tempo médio para preenchimento de vagas:** mede o tempo necessário para preencher uma vaga aberta, o que pode indicar a eficiência do processo de recrutamento e seleção;

    - **Custo de contratação por funcionário:** mede o custo total de contratar um novo funcionário, incluindo gastos com anúncios de vagas, entrevistas, testes e treinamento;

    - **Participação em treinamentos:** mede o número de funcionários que participam de programas de treinamento e desenvolvimento, o que pode indicar o interesse dos funcionários em melhorar suas habilidades e desenvolver suas carreiras;

    - **Avaliação de desempenho:** mede a avaliação do funcionário em um ciclo de trabalho, normalmente 6 ou 12 meses;

    - **Nível de absenteísmo:** mede a frequência com que os funcionários faltam ao trabalho, o que pode indicar problemas com o ambiente de trabalho ou saúde dos funcionários;

    - **Nível de engajamento:** escala que define quão engajados os funcionários estão, normalmente medida com base no nível de absenteísmo, pontualidade, avaliação de desempenho etc.

---

## Mini-Projeto 3: Análise de Dados de RH

- Antes de iniciar o projeto, o professor compartilhou o roteiro e pediu que cada aluno o realizasse de forma independente, sem auxílio. A seguir, descrevo os passos que segui durante o desenvolvimento (sem considerar a parte de formatação):

    - Primeiramente, realizei o **download da base de dados** e a **conectei ao Power BI**;

    - Em seguida, **examinei a base** e percebi que **não havia campos que necessitassem de limpeza ou transformação**, então segui direto para a criação do relatório;

    - Para a primeira questão: **"Qual o total de funcionários atualmente na empresa?"**, adicionei um **cartão** à tela e inseri o campo `Id_Funcionario` (contagem), obtendo automaticamente o total de funcionários;

    - Na segunda questão: **"Qual o tempo médio de experiência dos funcionários (em anos)?"**, adicionei outro **cartão** e utilizei o campo `Anos_Experiencia` (média);

    - Para a terceira questão: **"Qual o total e percentual de funcionários do gênero masculino e feminino?"**, criei algumas **medidas DAX**. Embora exista uma forma mais direta, optei por detalhar o processo criando medidas separadas para o total e o percentual de cada gênero. As medidas foram:

    ```dax

        Qtd_Masculino = CALCULATE(COUNTROWS(DatasetRH), DatasetRH[Genero] = "Masculino")
        Qtd_Feminino = CALCULATE(COUNTROWS(DatasetRH), DatasetRH[Genero] = "Feminino")
        Total_Funcionarios = COUNTROWS(DatasetRH)
        Pct_Masculino = DIVIDE([Qtd_Masculino], [Total_Funcionarios], 0) 
        Pct_Feminino = DIVIDE([Qtd_Feminino], [Total_Funcionarios], 0) 

    ```

    - Após criar as medidas, adicionei **cartões individuais** para exibir `Qtd_Masculino`, `Qtd_Feminino`, `Pct_Masculino` e `Pct_Feminino`;

    - Para a quarta questão: **"Qual a média salarial mensal?"**, criei outro **cartão** e utilizei o campo `Salario_Mensal` (média);

    - Na quinta questão: **"Qual o total de funcionários por função?"**, utilizei um **gráfico de barras empilhadas**, configurando `Funcao` no eixo Y e `Total_Funcionarios` no eixo X;

    - Na sexta questão: **"Qual o percentual de funcionários disponíveis para fazer hora extra?"**, antes de inserir o gráfico, acessei **Transformar Dados**, localizei a coluna `Disponivel_Hora_Extra` e substituí os valores **S → Sim** e **N → Não**, uma padronização que já deveria ter sido realizada no segundo passo, já que manter apenas “S” e “N” não é tão legível. Em seguida, adicionei um **gráfico de rosca**, utilizando:

        - **Legenda:** `Disponivel_Hora_Extra`;

        - **Valores:** `Total_Funcionarios`.

    - Na sétima questão: **"Qual o nível de envolvimento dos funcionários no trabalho considerando 4 categorias: Ruim, Baixo, Médio e Alto?"**, acessei a aba **Transformar Dados** e criei uma **coluna condicional** chamada `Categoria_Indice_Envolvimento`, definindo:

        - 1 → Ruim

        - 2 → Baixo 

        - 3 → Médio 

        - 4 → Alto  

    - Em seguida, voltei ao relatório e inseri um **gráfico de pizza**, utilizando `Categoria_Indice_Envolvimento` como legenda e `Id_Funcionario` (contagem) como valores;

    - Por último, na questão 8: **"Este item não deve estar no Dashboard, mas precisa ser calculado: Qual o total e o percentual de funcionários que devem receber promoção? Considere a coluna 'Anos Desde a Última Promoção' com a seguinte regra: se o funcionário tiver 5 anos ou mais desde a última promoção, deve ter a promoção considerada; caso contrário, a promoção não deve ser considerada agora."**, para respondê-la, criei uma **nova coluna** com a seguinte fórmula DAX:

    ```dax

        Promocao_Considerada = IF(DatasetRH[Anos_Desde_Ultima_Promocao] >= 5, "Sim", "Não")

    ```

    - Como o professor especificou que essa informação **não deveria ser exibida no dashboard**, optei por **manter a coluna apenas na base de dados**, de modo que possa ser utilizada em **análises futuras**.

---

### Pontos Compartilhados pelo Professor na Unidade 6

- O professor criou uma **tabela de medidas** para organizar melhor o projeto (uma prática muito utilizada no mercado de trabalho, pois facilita a localização e manutenção das medidas no relatório). Nessa tabela, foram adicionadas as seguintes medidas: `TotalMasculino`, `TotalFeminino`, `% Masculino`, `% Feminino`, `TotalFunc`, `SalarioMedio`, `TotalFuncPromover`, `TotalFuncNaoPromover`, `% Promover` e `% Nao Promover`;

- Para criar essa tabela, ele acessou: **Inserir dados** → **Carregar**;

- Depois, para inserir as medidas, ele selecionou a tabela criada e clicou em **Nova medida**;

- Foram adicionadas as seguintes medidas à tabela:

    ```dax

        TotalFunc = COUNTROWS(DatasetRH)
        TotalFeminino = CALCULATE([TotalFunc], DatasetRH[Genero] = "Feminino")
        TotalMasculino = CALCULATE([TotalFunc], DatasetRH[Genero] = "Masculino")
        % Feminino = DIVIDE([TotalFeminino], [TotalFunc], 0)
        % Masculino = DIVIDE([TotalMasculino], [TotalFunc], 0)
        SalarioMedio = AVERAGE(DatasetRH[Salario_Mensal])
        TotalFuncPromover = CALCULATE([TotalFunc], DatasetRH[StatusPromo] = "Considerar Promoção")
        TotalFuncNaoPromover = CALCULATE([TotalFunc], DatasetRH[StatusPromo] = "Não Considerar Promoção")
        % Promover = DIVIDE([TotalFuncPromover], [TotalFunc], 0)
        % Nao Promover = DIVIDE([TotalFuncNaoPromover], [TotalFunc], 0)

    ```

- A criação da tabela deixou as funções DAX muito mais organizadas e fáceis de compreender. Para seguir o fluxo do professor, criei uma nova página no relatório dedicada exclusivamente às medidas que ele desenvolveu;

- Após isso, o professor criou uma **coluna condicional** (a qual também incluí na base). Em vez de criar uma medida para indicar quem deveria ser promovido, ele gerou a coluna `StatusPromo`, baseada em `Anos_Desde_Ultima_Promocao`:  

    - Se o valor for **maior ou igual a 5**, então: **"Considerar Promoção"**;  

    - Caso contrário: **"Não Considerar Promoção"**.  

- Essa coluna serviu de base para as medidas `TotalFuncPromover` e `TotalFuncNaoPromover`;

- Ele reforçou que criou mais medidas do que o necessário para o relatório atual, pois isso facilita análises futuras para o RH, evitando retrabalhos desnecessários;

- Posteriormente, inseriu os gráficos solicitados no relatório utilizando essas medidas. Também criou uma nova coluna categorizando `Indice_Envolvimento_Trabalho`, assim como eu havia feito;

- Para formatar as medidas percentuais, ele ensinou um macete: acesse a **Exibição de modelo**, selecione a medida (ex: `% Masculino`), role até as propriedades e altere o **Formato** para **Porcentagem**;

- Na parte estética, ele adicionou caixas sobre cada visual para destacar os elementos e ajustou a transparência para melhorar a apresentação.

