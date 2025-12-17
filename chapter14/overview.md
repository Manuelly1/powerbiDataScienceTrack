# Power BI e Bancos de Dados

## O que são SGBDs?

- **Sistemas Gerenciadores de Bancos de Dados (SGBDs)** são softwares responsáveis por gerenciar e administrar bancos de dados. Eles fornecem um conjunto de ferramentas e funcionalidades para criar, manter, manipular, proteger e otimizar o acesso aos dados armazenados. *São eles que facilitam a interação entre os usuários e os bancos de dados*, permitindo que eles executam operações como inserção, atualização, exclusão e consulta de dados;

- Eles podem ser classificados em diferentes categorias, dependendo do modelo de banco de dados que eles suportam, como:

    - **SGBDs Relacionais:** gerenciam bancos de dados relacionais, onde *os dados são organizados em tabelas e as relações entre eles são estabelecidas por meio de chaves primárias e estrangeiras*. Eles utilizam a linguagem **SQL** como uma linguagem padrão para realizar consultas e manipular dados. Exemplos: MySQL, PostgreSQL, Oracle e SQL Server;

    - **SGBDs NoSQL:** gerenciam bancos de dados não relacionais que *não utilizam o modelo tabular clássico. Eles são projetados para serem escaláveis e distribuídos*, e podem ser categorizados em diferentes tipos, como bancos de dados de documentos (MongoDB, Couchbase), bancos de dados de colunas (Cassandra, HBase), bancos de dados de grafos (Neo4j, OrientDB) e bancos de dados de chave-valor (Redis).

- Além desse gerenciamento, os SGBDs também são responsáveis por aspectos como controle de transações, consistência de dados, integridade referencial, segurança e gerenciamento de acesso, e otimização de consultas.

---

## O que são Bancos de Dados?

- São sistemas organizados para **armazenar, gerenciar e recuperar informações de maneira eficiente e estruturada**. Eles permitem o armazenamento de grandes quantidades de dados, facilitando a busca, análise e manipulação dos dados;

- Existem diferentes tipos, como:

    - **Bancos de Dados Relacionais:** baseados no modelo relacional, onde os dados são organizados em tabelas, e as relações entre eles são estabelecidas por meio de chaves primárias e estrangeiras;

    - **Bancos de Dados NoSQL:** são bancos de dados não relacionais que não utilizam o modelo tabular clássico. Eles são projetados para serem escaláveis e distribuídos, e podem ser categorizados em diferentes tipos (como mencionado no tópico anterior).

---

## Laboratório 6 - Trabalhando com Power BI e BDs para Extração e Análise de Dados

### Bancos de Dados Suportados pelo Power BI

- No Power BI, é possível obter dados de diversos bancos de dados, como **MySQL**, **PostgreSQL**, **Sybase**, **Teradata**, **SAP HANA**, **MariaDB**, **Oracle**, entre outros. Ao selecionar, por exemplo, o **MySQL**, aparece a seguinte mensagem: *“Antes de ser usado, este conector exige que um ou mais componentes adicionais sejam instalados”*;

- Embora o Power BI ofereça suporte nativo a vários bancos de dados, em muitos casos é necessário instalar um **conector/driver** que permita a comunicação entre a ferramenta e o sistema de banco de dados. Ao clicar em **“Saiba mais”**, o usuário é direcionado para a página oficial do MySQL, especificamente para o local onde se encontra o driver de conexão. Após realizar o download do arquivo, é necessário fechar e reabrir o Power BI para que a conexão possa ser estabelecida;

- Cada banco de dados possui um tipo específico de conector e um procedimento próprio de instalação. O **Oracle**, por exemplo, apresenta um fluxo de configuração diferente do MySQL, exigindo outros componentes para que a conexão com o Power BI seja realizada corretamente.

---

### Bancos de Dados Usados no Laboratório

- O professor explicou que existem mais opções de bancos de dados do que aquelas apresentadas diretamente na lista de **“Bancos de dados”** do Power BI. É possível realizar uma conexão direta por meio do **ODBC**, que funciona como um padrão de conexão universal, permitindo a integração com praticamente qualquer banco de dados;

- No menu **Obter dados → ODBC → Conectar**, o professor informou que utilizaria o **SQLite** como banco de dados para o laboratório.

---

### O que é o ODBC?

- **Open Database Connectivity é uma interface de programação de aplicativos (API)** padrão que permite que aplicativos se conectem a sistemas gerenciadores de bancos de dados (SGBDs) de diferentes fornecedores, independentemente do sistema operacional, linguagem de programação ou modelo de banco de dados;

- O ODBC foi desenvolvido pela Microsoft no início dos anos 1990 e é amplamente utilizado para fornecer acesso a uma variedade de bancos de dados, como Oracle, SQL Server, MySQL, PostgreSQL, entre outros;

- A principal **vantagem** do ODBC é que ele permite que os desenvolvedores escrevam aplicativos que podem se conectar a diferentes SGBDs sem a necessidade de modificar o código-fonte do aplicativo para cada banco de dados específico. Isso é possível porque o ODBC abstrai as diferenças entre os SGBDs e oferece uma interface comum para executar consultas e manipular dados;

- Ele funciona usando **drivers** específicos para cada SGBD. Esses drivers são responsáveis por traduzir as chamadas de API do ODBC para comandos específicos do SGBD. Portanto, para que um aplicativo se conecte a um determinado banco de dados, é necessário instalar e configurar o driver ODBC apropriado para esse banco de dados.

---

### Instalando Driver ODBC para Conexão com o Power BI

- Após sair da ferramenta, acessou-se o menu principal do computador e digitou-se **“ODBC”**, selecionando a opção **“Fontes de dados ODBC”**. Nessa janela, foi possível visualizar o **DSN de usuário**, o **DSN de sistema**, o **DSN de arquivo**, além das abas de **Drivers**, **Rastreamento**, entre outras opções;

- Em seguida, verificou-se a necessidade de criar uma nova conexão (*data source*) para permitir a conexão com o **SQLite**. Para isso, utilizou-se a opção **“Adicionar”**, analisando-se a lista de drivers disponíveis. Constatou-se, então, a ausência de um driver específico para o SQLite, o que tornou necessária a instalação de um **driver ODBC** adequado;

- Diante desse cenário, o professor encerrou a janela de fontes de dados e apresentou um arquivo executável disponibilizado ao final do capítulo, denominado **`DevartODBCSQLite.exe`**, utilizado para a instalação do driver. O arquivo foi obtido por meio do portal **Devart**, que disponibiliza drivers de conexão para diversas plataformas, destacando-se que o driver não era gratuito e possuía um período de avaliação de **30 dias**.

---

### Configurando Driver ODBC para Conexão com o Power BI

- Posteriormente, no Power BI, por meio da opção **Obter dados**, realizou-se a busca por **ODBC** e efetuou-se a conexão. Em **DSN (Nome da Fonte de Dados)**, verificaram-se as fontes disponíveis, comparando-as com as conexões existentes em **“Fontes de dados ODBC”** no computador. Identificou-se que, embora houvesse três conexões configuradas, o Power BI reconheceu apenas **dBase Files**;

- Dessa forma, foi necessária a criação de uma nova fonte de dados. Para isso, retornou-se à opção **“Fontes de dados ODBC”** e iniciou-se a configuração manual. Ao selecionar **“Adicionar”**, identificou-se o driver **“Devart ODBC Driver for SQLite”**, que foi escolhido para prosseguir com a configuração, clicando-se em **“Concluir”**;

- Na etapa seguinte, foi aberta uma janela para definição do **nome da fonte de dados**, definido livremente como **`db_dsa`**, da **descrição** e do **banco de dados**, correspondente ao arquivo do SQLite. O arquivo foi localizado por meio da opção representada pelos três pontos (**...**). Após a execução do comando **“Test Connection”**, o sistema confirmou o sucesso da conexão;

- Com a conexão ODBC configurada, a fonte **`db_dsa`** passou a ser exibida no Power BI, na opção **Obter dados**. Ao selecioná-la e confirmar a ação, o sistema solicitou **usuário** e **senha**;

- Como o banco de dados SQLite não possuía autenticação configurada, o professor utilizou a opção **Padrão ou Personalizada** e prosseguiu com a conexão. Nesse momento, o Power BI estabeleceu a comunicação via ODBC com o arquivo do SQLite, exibindo a pasta **`main`**;

- Por fim, as tabelas disponíveis foram selecionadas e os dados carregados para a ferramenta.

---

### Extraindo os Dados do Banco de Dados e Verificando o Modelo no Power BI

- Inicialmente, como o banco de dados envolvia mais de uma tabela, recomendou-se acessar a área de **Modelo** para verificar os relacionamentos existentes entre as tabelas, uma vez que esses relacionamentos nem sempre são criados automaticamente. Essa situação geralmente ocorre quando há inconsistências nos dados, como **registros duplicados** ou **ausência de nomes nas colunas**;

- Após essa verificação, o laboratório foi concluído.

---

### Usando SQL para Extração de Dados de Bancos de Dados com Power BI

- Na última aula da unidade, o professor apresentou o uso da linguagem **SQL** para a extração de dados no Power BI, evitando a necessidade de carregar integralmente todas as informações do banco de dados. O procedimento foi realizado por meio do caminho **Obter dados → ODBC → Conectar → `db_dsa` → Opções avançadas**, onde foi inserida a instrução SQL;

- O script utilizado foi:

```sql

    SELECT id_cliente, cidade, estado, pais
    FROM TB_DSA_CLIENTES;

```

- Após a confirmação da operação ao clicar em **“Ok”**, os dados foram carregados, e o Power BI gerou uma tabela contendo apenas as colunas especificadas na consulta.

