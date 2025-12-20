# Machine Learning e Power BI para Segmentação de Clientes

## O que é Machine Learning (Aprendizado de Máquina)?

- É uma área da Inteligência Artificial que se concentra no desenvolvimento de algoritmos e técnicas que permitem que os computadores aprendam a executar tarefas sem serem explicitamente programados para isso. O **objetivo** é desenvolver modelos que possam *identificar padrões, fazer previsões e tomar decisões com base nos dados fornecidos*;

- O aprendizado de máquina pode ser dividido em 3 categorias:

    - **Aprendizado supervisionado:** Neste tipo de aprendizado, o algoritmo é treinado com um conjunto de dados rotulados, ou seja, com entradas e saídas conhecidas. O algoritmo utiliza esses dados para aprender a mapear as entradas nas saídas corretas. Exemplos comuns incluem classificação de imagens e previsão de preços;

    - **Aprendizado não supervisionado:** Aqui, o algoritmo é treinado com um conjunto de dados não rotulados, e seu objetivo é encontrar padrões e estruturas subjacentes nos dados. Exemplos comuns incluem agrupamento e redução de dimensionalidade;

    - **Aprendizado por reforço:** Neste tipo de aprendizado, o algoritmo, chamado de agente, aprende a tomar decisões com base em recompensas e punições. O agente interage com um ambiente e ajusta suas ações para maximizar as recompensas a longo prazo. Exemplos comuns incluem jogos e robótica.

- A verdade é que *Machine Learning* tem uma ampla gama de aplicações, desde a análise de dados e previsão até a automação e desenvolvimento de sistemas de recomendação. É uma área em rápido crescimento e desempenha um papel crucial no desenvolvimento de tecnologias avançadas. Além disso, é uma das atividades principais em projetos de Data Science. O foco desta unidade é o **aprendizado não supervisionado**.

---

## O que é Segmentação de Clientes?

- É o processo de **dividir a base de clientes de uma empresa em grupos distintos** com base em *características comuns, necessidades, comportamentos ou preferências*;

- O **objetivo** é entender melhor as necessidades e desejos de diferentes grupos de clientes e, assim, adaptar as estratégias de marketing, comunicação e vendas para atender a essas necessidades de maneira mais eficaz e personalizada;   

- A segmentação pode ser feita com base em diversos critérios, como:

    - **Demográficos:** Idade, sexo, estado civil, renda, ocupação, nível de educação e tamanho da família;

    - **Geográficos:** Localização, clima, densidade populacional e fronteiras políticas ou culturais;

    - **Psicográficos:** Estilo de vida, personalidade, valores, atitudes e interesses;

    - **Comportamentais:** Padrões de compra, frequência de uso, lealdade à marca, preferências e atitudes em relação a produtos e serviços.

- **A segmentação pode beneficiar as empresas de várias maneiras, incluindo:**

    - Compreender melhor as necessidades e expectativas de diferentes grupos de clientes;

    - Desenvolver campanhas de marketing e comunicação mais eficazes e personalizadas;

    - Identificar oportunidades de mercado e nichos ainda não explorados;

    - Melhorar a satisfação e retenção de clientes, oferecendo produtos e serviços mais adequados às suas necessidades;

    - Otimizar a alocação de recursos, concentrando-se nos segmentos de clientes mais lucrativos ou com maior potencial de crescimento.

- As empresas podem utilizar técnicas de análise de dados e aprendizado de máquina para segmentar sua base de clientes de forma mais precisa e sofisticada, identificando padrões e relações complexas entre diferentes variáveis e comportamentos.

---

## Laboratório 7 - Machine Learning com Python e Power BI no Jupyter Notebook

- O Power BI não é uma ferramenta voltada para projetos de aprendizado de máquina; por isso, é necessário utilizar outra ferramenta. Neste caso, a escolhida foi o **Jupyter Notebook**;

- Assim como nas unidades anteriores, o professor inicialmente examinou a base de dados para visualizar os campos, a quantidade de registros (500) e o conteúdo dos dados. A partir dessa análise, foi possível observar que, para realizar a segregação solicitada neste laboratório, seria necessário desenvolver um algoritmo capaz de dividir a base com precisão em três grupos distintos;

- Contudo, existe uma alternativa mais simples: a aplicação de técnicas de *Machine Learning*, que disponibilizam algoritmos prontos capazes de analisar os dados, identificar similaridades e realizar o agrupamento automaticamente, muitas vezes com apenas uma linha de código. Dessa forma, evita-se a necessidade de criar diversas regras manuais para realizar a segregação dos perfis.

---

### Como o Power BI Pode Ser Usado em Projetos de Machine Learning?

- Após a finalização do trabalho de modelagem, o conjunto de dados devidamente limpo e modelado pode ser importado para o Power BI. A partir disso, é possível criar relatórios e gráficos com base nos resultados obtidos durante a etapa de modelagem em Machine Learning, permitindo a análise e a visualização dos padrões identificados.

---

### Iniciando o Jupyter Notebook

- Para este projeto, o professor definiu que seria utilizada exclusivamente essa ferramenta tanto para a execução de códigos em linguagem Python, por meio do interpretador Anaconda Python, quanto para a elaboração dos relatórios no Power BI ao final do trabalho de modelagem. Para isso, foi necessário realizar previamente a instalação do **Anaconda**, uma distribuição gratuita de Python e R voltada para ciência de dados, aprendizado de máquina e IA. Essa distribuição facilita o gerenciamento de ambientes e pacotes, além de incluir, de forma nativa, ferramentas como o **Jupyter Notebook** e bibliotecas essenciais (por exemplo, NumPy e Pandas), tornando mais simples a configuração do ambiente de análise de dados em um único local;

- Após a instalação, foi aberto o **Prompt de Comando (CMD)** em modo administrador. Em seguida, dentro da pasta onde se encontra a base de dados, copiou-se o caminho do diretório e executou-se o comando `cd` seguido do respectivo caminho. Já no diretório correto, digitou-se o comando `jupyter notebook`, o que resultou na abertura da ferramenta no navegador. Por fim, no ambiente do Jupyter, bastou clicar no arquivo `Lab7.ipynb` para iniciar as atividades.

---

### Definição do Problema de Negócio

- No ambiente do **Jupyter Notebook**, o professor apresentou alguns comandos importantes, como **Kernel → Restart Kernel and Clear Outputs** e **Kernel → Restart Kernel and Run All Cells**, além de reforçar a importância de sempre clicar no ícone de salvamento, a fim de evitar a perda de alterações realizadas no notebook;

- Todo projeto de **Data Science** e **Machine Learning** tem início com a **definição do problema de negócio**. Neste caso, o problema proposto foi: *“Considerando dados históricos de clientes que realizaram compras em nossa empresa, realizar o agrupamento (segmentação) dos clientes por similaridade de características em três grupos e enviar o relatório para a equipe de Marketing”*. A partir dessa definição, o analista consegue determinar quais dados serão utilizados, como será realizado o pré-processamento, qual algoritmo de Machine Learning será aplicado e de que forma os resultados serão entregues. Assim, cada problema de negócio dá origem a um projeto específico;

- Sempre que são utilizadas técnicas de **Machine Learning**, faz-se necessário o uso de **dados históricos**. Caso a empresa não possua esses dados, não há matéria-prima suficiente para a aplicação das técnicas nesse momento. Nessa situação, o analista deve iniciar a coleta de dados e, após um período adequado (por exemplo, três ou quatro meses), retomar o projeto para aplicar os modelos de aprendizado de máquina;

- No contexto apresentado, **agrupamento** é sinônimo de **segmentação**, com o objetivo inicial de formar três grupos de clientes. Entretanto, surge um questionamento relevante: *será que três grupos são suficientes para representar adequadamente os padrões presentes nos dados históricos?*. Essa é uma reflexão que cabe ao analista, uma vez que a solicitação do negócio nem sempre corresponde à solução ideal do ponto de vista analítico. Por fim, é necessário encaminhar o relatório à equipe de Marketing. Embora a ferramenta não tenha sido explicitamente definida, cabe ao analista verificar se a empresa possui licença de algum software disponível. Neste projeto, optou-se pelo uso do **Power BI**.

---

### Carregando os Dados

- 