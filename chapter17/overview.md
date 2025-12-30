# Machine Learning e Power BI para Detecção de Outliers (Anomalias)

## O que é Detecção de Anomalias?

- É uma técnica de Machine Learning (ML) e Estatística que visa identificar padrões incomuns, inesperados ou anômalos nos dados. Esses padrões podem ser diferentes das observações normais de várias maneiras, como magnitude, frequência ou comportamento. A detecção de anomalias é importante porque as anomalias podem indicar problemas, erros, falhas, fraudes ou atividades maliciosas e, em muitos casos, é crucial identificar e analisar esses eventos anômalos para tomar decisões informadas e apropriadas;

- Existem várias abordagens para detectar anomalias em ML, algumas das quais incluem:

    - **Métodos Estatísticos:** Esses métodos baseiam-se na análise estatística dos dados, como testes de hipóteses, distribuições de probabilidade e medidas de dispersão (por exemplo, desvio padrão e intervalos interquartis). Observações que estão significativamente distantes da média ou fora dos intervalos esperados são consideradas anômalas;

    - **Aprendizado Supervisionado:** Nesta abordagem, um modelo de ML é treinado usando um conjunto de dados rotulado, que inclui exemplos de observações normais e anômalas. O modelo aprende a distinguir entre as duas classes e, em seguida, pode ser usado para classificar novas observações como normais ou anômalas;

    - **Aprendizado Não Supervisionado:** Neste caso, os algoritmos de ML são usados para analisar dados não rotulados e identificar padrões ou agrupamentos naturais neles. As anomalias são identificadas como pontos de dados que não se encaixam bem em nenhum desses agrupamentos ou que estão significativamente distantes de outros pontos de dados. Alguns exemplos incluem clustering e técnicas de redução de dimensionalidade;

    - **Aprendizado Semi-Supervisionado:** Esta abordagem combina elementos dos dois anteriores. Os algoritmos são treinados em um conjunto de dados parcialmente rotulado, que contém exemplos de observações normais e um pequeno número de exemplos anômalos. O modelo aprende a distinguir entre as classes e identificar novas anomalias com base nos padrões aprendidos;

    - **Métodos Baseados em Densidade:** Esses métodos identificam anomalias como pontos de dados que estão localizados em áreas de baixa densidade do espaço de recursos (atributos). Um exemplo desse tipo é o DBSCAN.

---

## Principais Áreas de Aplicação da Detecção de Anomalias

- A detecção de anomalias é uma técnica útil em várias áreas, uma vez que ajuda a identificar padrões incomuns ou comportamentos inesperados nos dados. Algumas das áreas mais comuns incluem:

    - **Finanças:** Detecção de fraudes em transações bancárias ou de cartão de crédito. Monitoramento do mercado financeiro para identificar atividades de insider trading ou manipulação de mercado;

    - **Cibersegurança:** Detecção de intrusões em redes, identificando padrões incomuns de tráfego ou comportamento do usuário. Monitoramento de logs de servidores e sistemas para identificar atividades maliciosas ou não autorizadas;

    - **Manutenção Preditiva:** Análise de dados de sensores em equipamentos industriais ou infraestrutura para identificar falhas iminentes ou desempenho degradado. Análise de anomalias em sinais de sensores IoT para identificar padrões incomuns;

    - **Saúde:** Identificação de eventos adversos ou erros médicos em registros de pacientes. Monitoramento de sinais vitais e dados de sensores de pacientes para identificar condições anômalas que possam indicar uma deterioração da saúde do paciente;

    - **Monitoramento Ambiental:** Análise de dados meteorológicos e climáticos para identificar eventos extremos ou mudanças significativas nas condições ambientais. Monitoramento da qualidade do ar e da água para identificar poluição ou contaminação;

    - **Marketing e Vendas:** Análise de padrões de comportamento do consumidor para identificar segmentos de clientes incomuns ou oportunidades de mercado não exploradas. Identificação de atividades fraudulentas em campanhas publicitárias, como cliques falsos ou impressões.