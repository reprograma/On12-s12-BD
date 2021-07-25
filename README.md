<h1 align="center">
    <br>
    <p align="center">Semana 12 - Introdução ao Banco de Dados<p>
</h1>

## O que é um banco de dados?

Antigamente organizávamos nossos dados em papel e arquivos físicos, e com o tempo ficava bem difícil administrar essas informações. Além da dificuldade para lidar com essas informações, existia também um enorme risco de perdermos essa folha de papel que tinha nosso dado ou mesmo cair em mãos erradas. Hoje com um banco de dados conseguimos armazenar essas informações digitalmente, de forma segura, e recuperar muito mais facilmente os dados que precisamos, além de permitir que mais de uma pessoa acesse a mesma informação ao mesmo tempo, o que seria impossível com uma única folha de papel.

Em termos gerais, podemos definir banco de dados como uma coleção organizada onde se pode armazenar dados, de forma estruturada podendo ser consultada por um programa ou pessoa permitindo extrair informações. Ficou um pouco confuso? Não se preocupe, vamos entender melhor o que é e como funciona ao longo desse curso! Ao final essa definição ficará muito mais clara.

![banco_de_dados](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTW8kxwgWPiXr77gcQiAxMqBTLKkuJlFK8PfRRWHsUjyeJ0NvLeGAjQHKemgrFZCJYHRZ0&usqp=CAU)

## Clínica Jansen's Anatomy

![clinica_medica_greys_anatomy](https://uploads.jovemnerd.com.br/wp-content/uploads/2018/10/greys-anatomy-1210x540.png)

### Problema

A clínica Jansen's Health é um pouco "cringe", então costuma agendar as consultas e dados do paciente no papel e caneta. Com o passar do tempo e com a clínica crescendo está ficando insustentável manter o que temos hoje. Toda vez que precisamos de qualquer informação do paciente ou mesmo das consultas do médico demoramos muito para achar o que precisamos. Além disso, temos dados super importantes em anotações, como prontuário e todo um histórico de pacientes. Se perdermos uma folha ou alguma dessas cair em mãos erradas, podemos perder algo muito importante e sensível. Com todo esse cenário caótico, a clínica pediu nossa ajuda para organizar esses dados para melhorar o dia a dia deles e dos pacientes.

![homer_desesperado](https://medicinamardelplata.files.wordpress.com/2018/05/homer.png)


### Como resolver isso?

Para ajudá-los a organizar os dados da clínica, precisamos antes entender a informação que eles têm para ser organizada. Essas informações são compostas de dados de consulta, dados do paciente atendido e médico que atendeu.

O que temos desses dados?

* **Dados de Pacientes**: *Nome, Plano de Saúde, Carteirinha, Endereço, Telefone*
* **Dados de Médicos**: *Nome, Documento profissional (ex: CRM), Especialidade, Telefone*
* **Dados de Consultas**: *Médico, Paciente, Data Hora, Prescrições (remédios receitados), Exames (exames prescritos), Prontuário (anotações da consulta)*

Pronto, anotamos as informações utilizadas no dia a dia da clínica e agora? Como a gente vai organizar isso? Podemos organizar nossos dados de forma relacional e de forma não relacional. Mas o que é cada uma dessas duas formas diferentes???!

![bob_esponja_pensativo](https://64.media.tumblr.com/tumblr_m2a0k4mEF71rsmfs0o1_250.gifv)

---

### Banco de dados relacionais (SQL)

No banco de dados relacional nossas informações ficam em tabelas e se relacionam. Os bancos de dados relacionais são conhecidos como banco de dados SQL. Essa sigla SQL siginifica “Structured Query Language” que traduzindo para o português significa: “Linguagem de Consulta Estruturada”.
Com o SQL, você pode executar vários comandos para criar, alterar, gerenciar, consultar, dentre outras informações no seu banco de dados. Costumamos dizer que bancos SQL seguem uma modelagem relacional, pois estes se baseiam no fato de que todos seus dados sejam guardados em tabelas.

Para entendermos melhor o que seria um banco de dados relacional, vamos montar um esboço do nosso banco de dados relacional da nossa clínica? Primeiro vamos desenhar um modelo para nosso banco:

![bd_relacional](https://i.imgur.com/8l5vVxf.png?1)

Vamos simular esse banco em uma tabela? https://docs.google.com/spreadsheets/d/1G0tPKeKvCHS1_Q0-w6GAWa4G_xKwdcwN73c9dOxL0V4/edit#gid=1916395408

Um exemplo de um comando SQL para trazer todas as informações da minha tabela de Pacientes seria:

```
SELECT * FROM PACIENTES
```
Esse comando acima significa: *selecionar tudo de Pacientes*. Feito isso serão retornadas todas as linhas da tabela Pacientes.

### Banco de dados não relacionais (noSQL)

No banco de dados não relacional não utilizamos o *SQL* e também não temos esse esquema de tabelas e linhas. Se não temos tabelas como isso fica armazenado então? Temos alguns modelos de bancos noSQL e vamos falar um pouco deles agora para entender melhor como os dados ficariam armazenados:

![bd_nao_relacional](https://i.imgur.com/fHnOR4O.png)

#### Banco de dados de Documentos (noSQL)
    
Esse banco de dados foi projetado para armazenar e consultar dados como documentos do tipo JSON. Os bancos de dados de documentos facilitam para que os desenvolvedores armazenem e consultem dados usando o mesmo formato de modelo de documento que usam no código da aplicação. **Um exemplo de banco de dados de documentos é o famoso MongoDB!**

As consultas médicas do Jansen's Anatomy em um banco noSQL (não relacional) de Documentos ficariam assim nesse formato:
    
```
    {
        "_id": "a24e470f-08c0-4c03-8312-18575a41d247",
        "dataHora": ISODate("2021-07-12T10:00:00Z"),
        "medico" : { 
            "nome": "Sarah Freitas", 
            "documentoProfissional": "CRM-SP 1234",
            "especialidade": "Clínica Médica",
            "telefone": "(11) 1212-12112"
        },
        "paciente": {
            "nome": "Rita da Silva",
            "telefone": "(11) 8888-8888"
        },
        "prescricoes": "Tomar remédio x para dor 2 vezes ao dia por 5 dias.",
        "exames": "Ressonancia Magnetica e Raio X",
        "prontuario": "Paciente se queixa de dor nas costas"
    },
    {
        "_id": "72a84cf4-c21d-4ed1-9cff-ab23260182d7",
        "dataHora": ISODate("2021-07-12T11:00:00Z"),
        "medico" : { 
            "nome": "Sarah Freitas", 
            "documentoProfissional": "CRM-SP 1234",
            "especialidade": "Clínica Médica",
            "telefone": "(11) 1212-12112"
        },
        "paciente": {
            "nome": "Daniel Borges",
            "planoSaude": "Bradesco",
            "carteirinha": "98765432",
            "endereco": "Avenida dos Papagaios número 131 apto 55A",
            "telefone": "(11) 7777-7777"
        },
        "prescricoes": "Remédio para dor de estômago",
        "exames": "Endoscopia",
        "prontuario": "Paciente se queixa de dor e queimação no estômago"
    },
    // E todo o restante dos dados em diante
```
#### Banco de dados de Grafos (noSQL)

Os bancos de dados grafo utilizam nós para armazenar entidades de dados e bordas para armazenar os relacionamentos entre as entidades. Uma borda tem sempre um nó inicial, um nó final, um tipo e um direcionamento, o que possibilita a descrição dos relacionamentos entre pais e filhos, das ações, das propriedades e assim por diante. A quantidade e os tipos de relacionamentos que um nó pode ter são ilimitados. **Um exemplo de banco de dados de Grafos é o Arangodb.**

O gráfico a seguir é um exemplo de gráfico de rede social. Considerando as pessoas (nós) e seus relacionamentos (bordas), é possível descobrir quem são os “amigos dos amigos” de uma pessoa específica:

![bd_nao_relacional](https://d1.awsstatic.com/diagrams/foaf-graph.e5e42865e0ee97a2972f9014d28f525ef68a981b.png)

#### Banco de dados de Chave-Valor (noSQL)

É um tipo de banco de dados não relacional que usa um método de chave-valor simples para armazenar dados. Um banco de dados de chave-valor armazena dados como um conjunto de pares de chave-valor em que uma chave funciona como um identificador exclusivo. Os dados dentro de bancos de chave-valor são formados por duas partes: uma string, que representa a chave, e os dados em si, que são o valor. A chave é usada como um índice, permitindo que o usuário faça a requisição dos dados relacionados a ela. **Um exemplo de banco de dados de Chave-Valor é o Redis.**

#### Banco de dados Colunar (noSQL)

Enquanto um banco de dados relacional é otimizado para armazenar linhas de dados, um banco de dados colunar é otimizado para recuperação rápida de colunas de dados, normalmente em aplicativos analíticos. O armazenamento orientado a colunas para tabelas do banco de dados é um fator importante para a performance de consulta analítica, pois ele reduz expressivamente os requisitos gerais de E/S de disco e diminui a quantidade de dados que você precisa carregar do disco. **Um exemplo de banco de dados colunar é o Cassandra.**
    
### Banco de Dados Relacional (SQL) x Banco de Dados Não Relacional (noSQL)

Agora que sabemos o que é um banco relacional (SQL) e um banco de dados não relacional (noSQL), podemos falar um pouquinho das diferenças de cada um desses:
    
![sql_nosql](https://miro.medium.com/max/1400/0*LR8ZkHpzwTAZjBtI.png)

* **Vantagens do banco de dados não relacional (NoSQL):** A vantagem número um é a escalabilidade e a flexibilidade da estruturação, que além de tornar a escalabilidade mais fácil, facilita a inserção e acesso aos dados.

* **Vantagens do banco de dados relacional (SQL):** Enquanto que no modelo não relacional (noSQL), onde a consistencia de dados pode ser considerada fraca, no modelo relacional há uma forte consistencia de dados, um dos preços para isso é a estrutura menos flexivel.

A diferença essencial entre as duas teconologia é que uma é baseada em esquema (Relacional) e a outra não (Não relacional). Para trabalhar com um banco SQL (Relacional) a primeira coisa que voce precisa fazer é projetar a estrutura do banco, isto é, voce não consegue inserir um dado se não tiver previamente definido os "esquemas" das tabelas, enquanto que em um banco de dados NoSQL (Não relacional) isso não é necessário.

#### Qual banco de dados utilizar? SQL ou NoSQL?

Depende! Tudo vai depender do seu projeto, então sempre bom analisar o que precisará ser feito para decidir qual banco de dados é melhor para usar. Por exemplo, às vezes fazer consultas em diversas tabelas para conseguir retornar a informação que precisa, quando a base é exageradamente grande, pode exigir muito do seu banco de dados relacional. Pode ser que nesse caso faça sentido utilizar um não relacional (noSQL). Sempre vale uma análise pois cada caso é sempre um caso.

O NoSQL tem muitas vantagens para ser utilizado. Mas não é por isso que devemos utilizá-lo em todas as situações. Em muitos sistemas, você pode (e até deve) usar o modelo relacional. O NoSQL é mais indicado para aqueles sistemas que tenham necessidades maiores de armazenamento e desempenho. O NoSQL não veio para substituir o SQL, mas sim para oferecer mais uma alternativa de um banco de dados mais flexível no suporte de dados. Sendo assim, você pode usar ambas as soluções para diferentes casos.

## SGBD (Sistema de Gerenciamento de Banco de Dados)

Os Sistemas de Gerenciamento de Banco de Dados são softwares utilizados para gerir as estruturas de armazenamento dos dados, permitem realizar manipulações, bem como controlar as permissões de utilização dos bancos de dados. Aqui nesse curso iremos focar no MongoDB para trabalhar com nossos dados!

![sgdb](https://i.imgur.com/kJokS8A.png?1)

## O que é o MongoDB?

MongoDB é um banco de dados não relacional (noSQL) orientado a documentos no formato JSON. Ele é opensource e possui alta performance e flexibilidade. Ao contrário de um banco de dados relacional (SQL), ele não possui como restrição a necessidade de ter as tabelas e colunas criadas previamente, permitindo que um ***documento*** represente toda a informação necessária, com todos os dados que você queira, no formato de um JSON. Esses documentos são agrupados em ***collections***, que em conjunto, forma um database (banco de dados).

![mongo_db](https://i.imgur.com/ciBulIx.png)

## Instalação do MongoDB

Aqui vamos focar na instalação do MongoDB no Windows, mas caso seja necessário a instalação no Linux ou MacOS, basta seguir os links abaixo:

 * Linux: https://docs.mongodb.com/manual/administration/install-on-linux/
 * MacOS: https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/ (É importante lembrar de criar a pasta `data/db` dentro do diretório `/Users/nomeUsuario`)

ps: Caso seu **MacOS** seja de uma versão mais antiga (ex: Sierra), deve-se rodar esses comandos no terminal para instalar:

```
$ brew tap mongodb/brew
$ brew install mongodb-community@4.2
```
E então utilizar os comandos abaixo para iniciar e parar o servidor, respectivamente:

```
$ brew services start mongodb-community@4.2
$ brew services stop mongodb-community@4.2
```
Em versões mais atuais do mac, podemos subir o servidor utilizando o comando: `mongod --dbpath=/Users/nomeUsuario/data/db`.

### Windows

Para instalar o MongoDB no Windows, deve-se acessar o link: https://www.mongodb.com/try/download/community , selecionar corretamente as comboboxes, conforme a imagem abaixo, e em seguinda, pressionar o botão de *Download*.

![install_mongo_db_windows_1](https://i.imgur.com/AtnO0SK.png)

Feito isso, deve-se seguir os passos a seguir:

![install_mongo_db_windows_2](https://i.imgur.com/pUJxDO1.png)

![install_mongo_db_windows_3](https://i.imgur.com/renmHqg.png)

Devemos acessar o painel de controle para adicionar variáveis de ambiente. Para isso devemos clicar em *editar as variáveis de ambiente do sistema* e em seguida na janela que for aberta, clicar em *Variáveis de Ambiente...*

![install_mongo_db_windows_4](https://i.imgur.com/HvBt8LJ.png)

![install_mongo_db_windows_5](https://i.imgur.com/H6914Th.png)

Ao clicar em *Variáveis de Ambiente*, irá abrir uma janela onde deverá ser adicionado o caminho da pasta bin de onde está instalado o seu mongoDB. Exemplo, adicionar o caminho *C:\Program Files\MongoDB\Server\5.0\bin*

### Inicializando o servidor

Para iniciar o servidor, abra o terminal e navegue, por meio dele, até a pasta *C:\Program Files\MongoDB\Server\5.0\bin*. Para isso, digite no terminal `cd C:\Program Files\MongoDB\Server\5.0\bin` e pressione "enter". Com isso você estará na pasta desejada, e deverá então digitar `mongod` e pressionar enter. Feito isso, o servidor deverá ficar de pé.

![init_mongo](https://i.imgur.com/ykXe9XT.png)

### Utilizando o mongodb

Com o servidor rodando em um terminal, deixamos esse terminal aberto e abrimos um novo para trabalharmos com o banco de dados. No novo terminal que abrimos, sem fechar o que está rodando o servidor, devemos navegar até a pasta bin do mongo, como fizemos para subir o servidor, digitando `cd C:\Program Files\MongoDB\Server\5.0\bin`:

![using_mongo_directory](https://i.imgur.com/krZvjCF.png)

Já dentro da pasta bin no terminal, digitar **mongo** e pressionar enter:
 
![using_mongo](https://i.imgur.com/sB0Zstt.png)

Feito isso, já poderemos começar a trabalhar com o mongo!

#### Databases

Para começar, vamos visualizar as bases de dados (databases) existentes, utilizando o comando `show dbs`:

![mongo_databases](https://i.imgur.com/Jhagope.png)

Vamos criar um novo database para trabalharmos? Para isso utilize o comando `use reprograma`. Esse comando irá selecionar um database ou criar, caso esse não exista. Com nosso database criado podemos agora trabalhar em cima dele e criar nossas collections!

#### Collections

Antes de criar collections no nosso novo database `reprograma`, vamos recordar do nosso de documento que fizemos para consultas da Clínica Jansen's Anatomy?

```
    {
        "_id": "a24e470f-08c0-4c03-8312-18575a41d247",
        "dataHora": ISODate("2021-07-12T10:00:00Z"),
        "medico" : { 
            "nome": "Sarah Freitas", 
            "documentoProfissional": "CRM-SP 1234",
            "especialidade": "Clínica Médica",
            "telefone": "(11) 1212-12112"
        },
        "paciente": {
            "nome": "Rita da Silva",
            "telefone": "(11) 8888-8888"
        },
        "prescricoes": "Tomar remédio x para dor 2 vezes ao dia por 5 dias.",
        "exames": "Ressonancia Magnetica e Raio X",
        "prontuario": "Paciente se queixa de dor nas costas"
    },
    {
        "_id": "72a84cf4-c21d-4ed1-9cff-ab23260182d7",
        "dataHora": ISODate("2021-07-12T11:00:00Z"),
        "medico" : { 
            "nome": "Sarah Freitas", 
            "documentoProfissional": "CRM-SP 1234",
            "especialidade": "Clínica Médica",
            "telefone": "(11) 1212-12112"
        },
        "paciente": {
            "nome": "Daniel Borges",
            "planoSaude": "Bradesco",
            "carteirinha": "98765432",
            "endereco": "Avenida dos Papagaios número 131 apto 55A",
            "telefone": "(11) 7777-7777"
        },
        "prescricoes": "Remédio para dor de estômago",
        "exames": "Endoscopia",
        "prontuario": "Paciente se queixa de dor e queimação no estômago"
    },
    // E todo o restante dos dados em diante
```

* Como podemos armazenar essas informações no nosso banco de dados mongo? Para isso vamos criar uma **collection** chamada *Consultas* para armazenar essas informações. Para criar nossa coleção de consultas (collection), utilizaremos o comando `db.createCollection('Consultas')`.
* Para visualizar todas as collections criadas no nosso database podemos utilizar o comando `show collections`.
* Caso não queiramos mais nossa collection Consultas, podemos utilizar o comando `db.Consultas.drop()` para deletá-la.

## Robo 3T

Poderíamos continuar inserindo novas consultas na nossa nova Collection Consultas pelo terminal, como fizemos anteriormente, porém podemos melhorar nossa experiência utilizando um programa com interface gráfica bem mais simples de utilizar para continuarmos nossas atividades. Vamos então instalar o Robo 3T para facilitar nosso uso do mongo? Para isso acesse o link https://robomongo.org/ e efetue o download e instalação do mesmo.

![mongo_robo_3t_0](https://pbs.twimg.com/profile_images/674614010587795456/sCsiuBmt_400x400.png)

Com o mesmo já instalado podemos nos conectar no nosso banco de dados que está rodando ali naquele terminal que deixamos aberto. Para isso clicamos nos dois computadores do menu:

![mongo_robo_3t_1](https://i.imgur.com/79WfKcj.png)

Em seguida, clicamos em `create` e ajustamos o nome da conexão para um nome personalizado. Feito isso salvamos nossa conexão e em seguida clicamos em conectar:

![mongo_robo_3t_2](https://i.imgur.com/DzVPLdI.png)
![mongo_robo_3t_3](https://i.imgur.com/ENIMzgN.png)


Podemos ver que quando nos conectamos no nosso banco de dados pelo Robo 3T podemos ver listado o database `reprograma` e nossa collection `Consultas` que criamos anteriormente pelo terminal:

![mongo_robo_3t_4](https://i.imgur.com/U9FYFzn.png)

## Inserindo documentos na Collection

Agora que já estamos utilizando o Robo 3T, vamos continuar criando nossas consultas na collection `Consultas`? Vamos dar dois cliques na collection `Consultas` no Robo 3T. Feito isso ele já vai abrir o comando `db.getCollection('Consultas').find({})` para visualizar tudo o que contém nessa collection:

![mongo_robo_3t_4](https://i.imgur.com/yZAKMIz.png)

Podemos ver que não foi retornada nenhuma linha, pois essa collection `Consultas` está vazia, sem nenhuma consulta ainda registrada. Vamos inserir algumas consultas novas? Para isso podemos clicar com o botão direito na nossa collection `Consultas` e clicar em `Insert Document`:

![mongo_robo_3t_insert](https://i.imgur.com/pyz9GTt.png)

Com isso ele vai abrir uma janela para passarmos o json que queremos inserir na nossa collection `Consultas`. Podemos passar o seguinte json:

```
{
    "medico" : { 
            "nome": "Sarah Freitas", 
            "documentoProfissional": "CRM-SP 1234",
            "especialidade": "Clínica Médica",
            "telefone": "(11) 1212-12112"
    },
    "paciente": {
            "nome": "Rita da Silva",
            "telefone": "(11) 8888-8888"
    },
    "prescricoes": "Tomar remédio x para dor 2 vezes ao dia por 5 dias.",
    "exames": "Ressonancia Magnetica e Raio X",
    "prontuario": "Paciente se queixa de dor nas costas",
    "dataHora": ISODate("2021-07-12T10:00Z")
}
```

Ao salvar nosso json, podemos rodar o comando `db.getCollection('Consultas').find({})` no Robo 3T e o mesmo irá listar o documento que criamos:

![mongo_robo_3t_insert_result](https://i.imgur.com/8WGBjVc.png)

Caso queiramos inserir uma nova consulta via terminal, sem utilizar o Robo 3T, podemos utilizar o comando abaixo no terminal (que está conectado no mongo):

```
db.Consultas.insert({
    "medico" : { 
        "nome": "Sarah Freitas", 
        "documentoProfissional": "CRM-SP 1234",
        "especialidade": "Clínica Médica",
        "telefone": "(11) 1212-12112"
    },
    "paciente": {
        "nome": "Daniel Borges",
        "planoSaude" : "Bradesco",
        "carteirinha": "98765432",
        "endereco": "Avenida dos Papagaios número 131 apto 55A",
        "telefone": "(11) 7777-7777"
    },
    "prescricoes": "Remédio para dor de estômago",
    "exames": "Endoscopia",
    "prontuario": "Paciente se queixa de dor e queimação no estômago",
    "dataHora": ISODate("2021-07-12T11:00Z")   
});
```

Se formos no Robo 3T e rodamos a consulta `db.getCollection('Consultas').find({})` veremos que teremos agora dois registros (documentos) na nossa collection `Consultas`:

![mongo_robo_3t_insert_result_2](https://i.imgur.com/ABexvL3.png)

Que tal exercitarmos e inserirmos mais consultas na nossa collection `Consultas`? Podemos tentar inserir três essas consultas abaixo:

```
{
    "medico": {
        "nome": "Lucas Pereira",
        "documentoProfissional": "CRM-SP 5599",
        "especialidade": "Pediatria",
        "telefone": "(11) 4321-12343"
    },
    "paciente": {
        "nome": "Maria da Costa",
        "planoSaude": "Amil",
        "carteirinha": "123456789",
        "endereco": "Rua dos Bobos número 0",
        "telefone": "(11) 9999-9999"
    },
    "prescricoes": "Xarope",
    "prontuario": "Paciente se queixa de dor de garganta",
    "dataHora": ISODate("2021-07-12T10:00Z")
}
```

```
    {
        "medico": {
            "nome": "Lucas Pereira",
            "documentoProfissional": "CRM-SP 5599",
            "especialidade": "Pediatria",
            "telefone": "(11) 4321-12343"
        },
        "paciente": {
            "nome": "Maria da Costa",
            "planoSaude": "Amil",
            "carteirinha": "123456789",
            "endereco": "Rua dos Bobos número 0",
            "telefone": "(11) 9999-9999"
        },
        "prontuario": "Consulta de retorno, paciente apresentou melhora",
        "dataHora": ISODate("2021-07-19T11:00Z")
    }
```

```
    {
        "medico": {
            "nome": "Sarah Freitas",
            "documentoProfissional": "CRM-SP 1234",
            "especialidade": "Clínica Médica",
            "telefone": "(11) 1212-12112"
        },
        "paciente": {
            "nome": "Rita da Silva",
            "telefone": "(11) 8888-8888"
        },
        "prescricoes": "10 sessões de fisioterapia",
        "prontuario": "Consulta de retorno, paciente apresentou inflamacao na musculatura",
        "dataHora": ISODate("2021-07-20T09:00Z")
    }
```

Feito isso teremos ao total 5 documentos na nossa collection `Consultas`! Com esses documentos podemos fazer algumas operações que veremos a seguir.

## Consultas no MongoDB

Agora que temos a nossa base de dados populada, podemos efetuar algumas consultas que poderemos necessitar em algumas situações:

### Igualdade

* Como saber em quais consultas o médico receitou `Xarope`? Podemos consultar de duas maneiras:

1) Quando queremos retornar todos os documentos que contém apenas o texto exato `Xarope` na prescrição (caso esteja escrito `20ml de Xarope antes de dormir` não será retornado nessa consulta): `db.getCollection('Consultas').find({prescricoes: 'Xarope'})`
2) Quando queremos retornar todos os documentos que contém o texto `Xarope` na prescrição (caso esteja escrito `20ml de Xarope antes de dormir` nessa consulta irá retornar, além de retornar também caso esteja escrito apenas `Xarope`): `db.getCollection('Consultas').find({prescricoes: /.*Xarope.*/})`

### Menor que

* Como saber quais consultas ocorreram antes das 11h do dia 12/07/2021? `db.getCollection('Consultas').find({dataHora: {$lt: ISODate('2021-07-12 11:00:00.000Z') }})`. Nesse caso serão retornados 2 documentos de consultas no dia 12/07/2021 às 10h.

### Menor ou igual

* Como saber quais consultas ocorreram até das 11h (inclusive 11h) do dia 12/07/2021? `db.getCollection('Consultas').find({dataHora: {$lte: ISODate('2021-07-12 11:00:00.000Z') }})`. Nesse caso serão retornados 2 documentos de consultas no dia 12/07/2021 às 10h e 1 com consulta às 11h nesse dia.

### Maior que

* Como saber quais consultas ocorreram depois das 11h do dia 12/07/2021? `db.getCollection('Consultas').find({dataHora: {$gt: ISODate('2021-07-12 11:00:00.000Z') }})`. Nesse caso serão retornados 2 documentos de consultas, um com consulta no dia 19/07/2021 às 11h e um com consulta no dia 20/07/2021 às 9h.

### Maior ou igual

* Como saber quais consultas ocorreram depois das 11h (inclusive o das 11h) do dia 12/07/2021? `db.getCollection('Consultas').find({dataHora: {$gte: ISODate('2021-07-12 11:00:00.000Z') }})`. Nesse caso serão retornados 3 documentos de consultas, um com consulta no dia 12/07/2021 às 11h, um com consulta no dia 19/07/2021 às 11h, um com consulta no dia 20/07/2021 às 9h.

### Diferente

* Quero ver todas as consultas que ocorreram sem ser a consulta das 11h do dia 12/07/2021: `db.getCollection('Consultas').find({dataHora: {$ne: ISODate('2021-07-12 11:00:00.000Z') }})`. Nesse caso serão retornados 4 documentos, que são todos menos a consulta do dia 12/07/2021 às 11h.

### AND

* Quero ver todas as consultas com pacientes que tenham a palavra `da` no nome **E** que também tenham endereço na `Rua dos Bobos`: `db.getCollection('Consultas').find({"paciente.nome": /.*da.*/, "paciente.endereco": /.*Rua dos Bobos.*/})` .  Nesse caso serão retornados 2 documentos que possuem o paciente com essas informações.

### OR

* Quero ver todas as consultas com pacientes que tenham a palavra `da` no nome e **OU** que também tenham endereço na `Rua dos Bobos`: `db.getCollection('Consultas').find({$or:[{"paciente.nome": /.*da.*/},{"paciente.endereco": /.*Rua dos Bobos.*/}]})` .  Nesse caso serão retornados 3 documentos que possuem o paciente com essas informações.

## Atualizando um documento

Quero incluir o valor da consulta da paciente Rita da Silva. Como posso fazer isso? No Robo 3T posso clicar com o direito e escolher a opção `Update Documents`. Feito isso ele irá exibir um json já com um template para você utilizar para alterar o documento:

![mongo_robo_3t_update](https://i.imgur.com/3XaoLxi.png)

Na primeiro json que aparece na imagem `{ "key" : "value" }` (onde tem o comentário `//query`) corresponde ao filtro que vamos fazer para a alteração que iremos setar onde tem o comentário `//update`. Em outras palavras, você diz que você quer alterar tal coisa onde tem o `//update` quando o documento tiver `{ "key" : "value" }` (onde tem o comentário `//query`). Por exemplo, vamos incluir o valor da consulta nas consultas da paciente Rita da Silva:

```
db.getCollection('Consultas').update(
    { "paciente.nome" : "Rita da Silva" },
    { $set:
        { 
            "valor": 100 
        }
    }
);
```

Poderíamos incluir a parte de `\\options` da imagem se quiséssemos:

* Utilizando o `multi`, passando valor `true` alteraríamos todos os documentos com a query `{ "key" : "value" }` que especificamos. Caso informemos valor `false` alteraríamos apenas um documento com essa query `{ "key" : "value" }`. O valor padrão caso não informemos o multi é `false`.
* Utilizando o `upsert`, podemos informar o valor `true` caso queiramos inserir um novo documento caso não exista nenhum documento que satisfaça a query `{ "key" : "value" }`. O valor padrão caso não informemos o upsert é `false`.


## Excluindo um documento

Para excluir um documento pelo Robo 3T basta clicar em cima dele com o botão direito e escolher a opção `Delete Document` ou usar o comando `db.Consultas.remove({selecao})`, onde `selecao` é a condição que você quer passar para a deleção. Exemplo: quero deletar todas as consultas que possui valor da consulta 100: `db.Consultas.remove({"preco" : 100})`. Caso queiramos deletar apenas um único registro nessa condição podemos fazer essa remoção dessa forma: `db.Consultas.remove({"preco" : 100},{justOne: true})`

## Projeção do documento

Caso eu queira buscar todos os documentos, porém a única informação que quero que retorne seja a `dataHora` da consulta, como fazer? Podemos utilizar a seguinte seleção: `db.getCollection('Consultas').find({},{"dataHora" : 1, "_id" : 0})` . Nesse caso utilizamos o número `1` para informar que queremos que esse atributo velha no resultado, porém utilizamos o número `0` informando que não queremos que apareça no resultado da busca. Então na nossa listagem somente virá retornando o atributo `dataHora` das consultas.

## Limitando resultado de consultas

Caso eu queira retornar, por exemplo, no máximo 2 consultas na minha busca eu posso utilizar o limit: `db.getCollection('Consultas').find({}).limit(2)`

## Pulando resultado de consultas

Caso eu queira retornar as consultas mas remover alguns registros da lista (ex: 3 registros), não os mostrandos: `db.getCollection('Consultas').find().skip(3)`

## Ordenando resultado de consultas

Caso queiramos ordenar o resultado das consultas por algum atributo, por exemplo, pelo nome do médico, podemos fazer a seguinte busca: `db.getCollection('Consultas').find().sort({"medico.nome": 1})`

Esse número `1` indica que estamos ordenando do primeiro para o último, no caso do nome, da letra A -> Z do alfabeto. Caso fosse interessante ordenar ao contrário, da letra Z -> A, colocaríamos `-1` no lugar.

* Caso queiramos o resultado das consultas pelo nome do médico (A -> Z) e ordenar da última consulta para a primeira, considerando o atributo `dataHora`: 
`db.getCollection('Consultas').find({}).sort({"medico.nome": 1, "dataHora": -1})`

# Resumo de comandos básicos Mongo

![mongo_commands](https://64.media.tumblr.com/b379181a50957ac510be65e15fbe4c35/e87827f64c42008c-d8/s540x810/67cc66809ef7a594602ab2608795bf7955db470d.gifv)

1. Base de Dados
    * Exibir existentes - `show dbs`
    * Selecionar para uso (e criar, caso não exista) - `use nome-do-database`
    * Excluir base selecionada - `db.dropDatabase()`
2. Coleção
    * Criar coleção de documentos - `db.createCollection('nome-da-collection')` (Mongo é case sensitive)
    * Exibir todas as coleções - `show collections`
    * Apagar coleção de documentos - `db.nomedacollection.drop()`
3. Documentos
    * Inserir - `db.nomedacollection.insert(documento)`
    * Consultar -  `db.nomedacollection.find({selecao})`
        * Igualdade - `{<key>:<value>}`
        * Menor que - `{<key>:{$lt:<value>}}`
        * Menor ou igual - `{<key>:{$lte:<value>}}`
        * Maior que - `{<key>:{$gt:<value>}}`
        * Maior ou igual - `{<key>:{$gte:<value>}}`
        * Diferente - `{<key>:{$ne:<value>}}`
        * AND - `{<key>:<value>, <key>:<value>}`
        * OR - `$or:[{<key>:<value>},{<key>:<value>}]`
    * Atualizar - `db.nomedacollection.update({selecao}, {$set:{campos-atualizados}})`
    * Excluir - `db.nomedacollection.remove({selecao})` (Considerar exclusão de seleção, apenas um e todos)
    * Projetar - `db.nomedacollection.find({selecao},{<key>:1})`
    * Limitar - `db.nomedacollection.find().limit(numero)`
    * "Pular" - `db.nomedacollection.find().skip(numero)`
    * Ordernar -  `db.nomedacollection.find().sort({<key>:1})` (Considerar crescente e decrescente, e combinações)

---

# Links Extras:

- Apresentação utilizada na aula: https://docs.google.com/presentation/d/1Aj-rh80A1Tb72gtmxpZ-AchGCC_441hCEL0eZ7Ui4I8/edit?usp=sharing

- [https://kenzie.com.br/blog/banco-de-dados/](https://kenzie.com.br/blog/banco-de-dados/)
- [https://rockcontent.com/br/blog/banco-de-dados/](https://rockcontent.com/br/blog/banco-de-dados/)
- [https://medium.com/xp-inc/comparando-os-termos-utilizados-no-nosql-com-sql-e862788e2374](https://medium.com/xp-inc/comparando-os-termos-utilizados-no-nosql-com-sql-e862788e2374)
- [https://medium.com/@albsilva/o-fantastico-mundo-do-nosql-2e72c5640e69](https://medium.com/@albsilva/o-fantastico-mundo-do-nosql-2e72c5640e69)
- [https://gabriel-faraday.medium.com/o-que-%C3%A9-nosql-9d7fd54792d4](https://gabriel-faraday.medium.com/o-que-%C3%A9-nosql-9d7fd54792d4)
- [https://medium.com/qaninja/principais-diferen%C3%A7as-de-um-banco-de-dados-tradicional-e-o-mongodb-4fc1117453f8](https://medium.com/qaninja/principais-diferen%C3%A7as-de-um-banco-de-dados-tradicional-e-o-mongodb-4fc1117453f8)
- [https://www.fiveacts.com.br/sgbd/](https://www.fiveacts.com.br/sgbd/)

---

## Acabamos, e agora? Vamos exercitar!

![exercise](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcQzkx9NbIzjUfe7io1-mvfkRybTZGH-C0RL0A&usqp=CAU)

Agora que já sabemos o que é um banco de dados, já sabemos como instalar um e já conhecemos os comandos para utilizá-lo, podemos e devemos exercitar! O que podemos criar de novo? O que podemos atualizar? O que podemos buscar de informação nesse banco de dados?

Espero que tenha gostado da atividade e o segredo é praticar!!! Quanto mais exercícios fizer, melhor :) Abs e até mais!

---

## Para Casa

![exercise](https://media1.popsugar-assets.com/files/thumbor/XGbRY5FyWX99jE-AVcO0vx7A008/fit-in/1024x1024/filters:format_auto-!!-:strip_icc-!!-/2017/04/26/922/n/1922283/a08d3bf8b558b4c9_giphy_4_/i/When-Your-BFF-Tells-You-First-Name-Guy-She-Going-Date-You-Spring-CIA-Mode.gif)

Você deve criar um banco de dados novo (database) e uma coleção com um nome pertinente, de acordo com os dados e tema que você escolher. Os seguintes comandos devem ser feitos e entregues:

* Inserção de documentos
* Atualização de documentos
* Exclusão de documentos
* Consulta com projeção
* Consulta utilizando combinação entre os seletores
* Consulta paginada e ordenada (utilizar *skip*, *limit* e *sort*)
