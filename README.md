# TRABALHO 01:  Lanchonete BD
Trabalho desenvolvido durante a disciplina de BD1

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
Claudio Magno : claudiomagno_21@hotmail.com<br>
Diogo : dreedd020@gmail.com<br>
...<br>

### 2.INTRODUÇÃO E MOTIVAÇÃO<br>

> Diante dos desafios encontrados durante a pandemia a lanchonete BD uma startup no ramo é uma tentativa de seus donos para tentar seu negócio próprio buscando oportunidades de negócio. Com exemplos de diversos negócios semelhantes no mesmo ramo, o foco principal da lanchonete é a organização buscando sair na frente e se manter sempre firme tendo em vista que muitas lanchonetes tem uma queda brusca nas vendas logo após o "boom" inicial. Com um sistema de negócio simples mas eficiente, o objetivo é um sucesso a curto prazo e a expansão para franquias seguindo a mesma regra de negócio implementada em seu sistema de controle de modo a garantir a padronização e qualidade.
 

### 3.MINI-MUNDO<br>

Descrever o mini-mundo! (Não deve ser maior do que 30 linhas, se necessário resumir para justar) <br>
Entrevista com o usuário e identificação dos requisitos.(quando for o caso de sistemas com cliente  real)<br>
Descrição textual das regras de negócio definidas como um  subconjunto do mundo real 
cujos elementos são propriedades que desejamos incluir, processar, armazenar, 
gerenciar, atualizar, e que descrevem a proposta/solução a ser desenvolvida.

> O sistema tem como base gerenciar o funcionamento de uma lanchonete otimizando o rendimento do negócio como um todo.
O cliente, que possui o atributo nome, possui um telefone com os atributos tipo, telefone e código, sendo o tipo como C (cliente), e está ligado à entidade endereço, com os atributos código do cliente, rua, numero, bairro, cidade e unidade federativa do cliente. O cliente faz o pedido por meio de um funcionário, que possui o atributo nome_cliente, codigo do funcionario e possui um telefone com o tipo F (funcionário). O pedido é realizado e é registrado a data e um código do pedido. Com o cardapio, é fornecido a quantidade do pedido e o cardápio possui os atributos nome do produto, ingrediente do produto e o código.

### 4.PROTOTIPAÇÃO, PERGUNTAS A SEREM RESPONDIDAS E TABELA DE DADOS<br>
#### 4.1 RASCUNHOS BÁSICOS DA INTERFACE (MOCKUPS)<br>

![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/628d8f4c1e485196ed16fbfcc0fece07dea3d5e2/images/image.png?raw=true "Title")

![Arquivo PDF do Protótipo da lanchonete](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/263c3fec9ec8afb584d38f284496825f779e8bf2/arquivos/mockup.pdf)

#### 4.2 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
    a) O sistema proposto poderá fornecer quais tipos de relatórios e informaçes? 
    b) Crie uma lista com os 5 principais relatórios que poderão ser obtidos por meio do sistema proposto!
    
> A Empresa DevCom precisa inicialmente dos seguintes relatórios:
* Relatório que mostre o nome de cada supervisor(a) e a quantidade de empregados supervisionados.
* Relatório relativo aos os supervisores e supervisionados. O resultado deve conter o nome do supervisor e nome do supervisionado além da quantidade total de horas que cada supervisionado tem alocada aos projetos existentes na empresa.
* Relatorio que mostre para cada linha obtida o nome do departamento, o valor individual de cada salario existente no  departamento e a média geral de salarios dentre todos os empregados. Os resultados devem ser apresentados ordenados por departamento.
* Relatório que mostre as informações relacionadas a todos empregados de empresa (sem excluir ninguém). As linhas resultantes devem conter informações sobre: rg, nome, salario do empregado, data de início do salario atual, nomes dos projetos que participa, quantidade de horas e localização nos referidos projetos, numero e nome dos departamentos aos quais está alocado, informações do historico de salário como inicio, fim, e valores de salarios antigos que foram inclusos na referida tabela (caso possuam informações na mesma), além de todas informações relativas aos dependentes. 
>> ##### Observações: <br> a) perceba que este relatório pode conter linhas com alguns dados repetidos (mas não todos). <br>  b) para os empregados que não possuirem alguma destas informações o valor no registro deve aparecer sem informação/nulo. 
* Relatório que obtenha a frequencia absoluta e frequencia relativa da quantidade de cpfs únicos no relatório anterior. Apresente os resultados ordenados de forma decrescente pela frequencia relativa.

 
 
#### 4.3 TABELA DE DADOS DO SISTEMA:
    a) Esta tabela deve conter todos os atributos do sistema e um mínimo de 10 linhas/registros de dados.
    b) Esta tabela tem a intenção de simular um relatório com todos os dados que serão armazenados 
    
![Exemplo de Tabela de dados da Empresa Devcom](https://github.com/discipbd1/trab01/blob/master/arquivos/TabelaEmpresaDevCom_sample.xlsx?raw=true "Tabela - Empresa Devcom")
    
    
### 5.MODELO CONCEITUAL<br>
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/conceitual%20v2.png "Modelo Conceitual")
    
    
        
    
#### 5.1 Validação do Modelo Conceitual
    [Grupo01]: [Nomes dos que participaram na avaliação]
    [Grupo02]: [Nomes dos que participaram na avaliação]

#### 5.2 Descrição dos dados 
    [objeto]: [descrição do objeto]
    
    EXEMPLO:
    CLIENTE: Tabela que armazena as informações relativas ao cliente<br>
    CPF: campo que armazena o número de Cadastro de Pessoa Física para cada cliente da empresa.<br>


### 6	MODELO LÓGICO<br>
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/logico%20v3.png "Modelo Lógico")

### 7	MODELO FÍSICO<br>
        create table FUNCIONARIO (cod_func int not null, nome_func varchar, tel_func varchar, primary key (cod_func));
        
        create table CLIENTE (cod_cliente int not null, nome_cliente varchar, primary key (cod_cliente));
        
        create table PEDIDO (cod_pedido int not null, data_pedido time, cod_cliente_pedido int, cod_func_pedido int , primary key (cod_pedido), foreign key(cod_cliente_pedido) references CLIENTE (cod_cliente), foreign key (cod_func_pedido) references FUNCIONARIO (cod_func)));
        
        create table TELEFONE (codigo int not null, telefone varchar, foreign key (codigo) references CLIENTE (cod_cliente));
        
        create table ENDERECO (cod_cliente int not null, rua_cliente varchar, num_casa_cliente int, bairro_cliente varchar, cidade_cliente varchar, uf_cliente varchar, foreign key (cod_cliente) references CLIENTE (cod_cliente));
        
        create table CARDAPIO (cod_prod int not null, nome_prod varchar, desc_prod varchar, valor_prod float, primary key (cod_prod));
        
        create table CARDAPIO_PEDIDO (cod_item int not null, cod_pedido int, quant_pedido int, foreign key (cod_item) references CARDAPIO (cod_prod), foreign key (cod_pedido) references PEDIDO (cod_pedido));
 
       
### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
        insert into cardapio values ((1,'X-Bacon', 'Pão, 2x carne, bacon, alface e salada.', 14.00), (2,'X-Tudo','Pão, carme, bacon, ovo, milho, alface e salada.', 15.00), (3,'X-Egg','Pão, carne, 2x ovo, bacon, alface e salada.', 14.00), (4,'X-Egg Bacon', 'Pão, 2x carne, 2x ovo, bacon, alface e salada.', 16.00), (5,'Misto', 'Pão, presuto e queijo.', 12.00));

        insert into cliente values ((1, 'Claudio'), (2, 'Isabelly'), (3, 'Gabriel'), (4, 'Julio'), (5, 'Augusto'));

        insert into endereco values ((1, 'Mossoró', 590, 'Barcelona', 'Serra', 'ES'),(3, 'Andorinhas', 12, 'Jacaraípe', 'Serra', 'ES'), (2, 'Cascardo', 175, 'Barcelona', 'Serra', 'ES'), (5, 'Alfredo Cunha', 154, 'Taquara', 'Serra', 'ES'), (4, 'Senhorio', 77, 'Barcelona', 'Serra', 'ES'));

        insert into telefone values ((1, '(27) 99645-1234'), (3, '(27) 94521-8524'), (2, '(27) 99998-8524'), (4, '(27) 999645-12345'), (5, '(27) 99698-4785'));

        insert into funcionario values ((1, 'Jorge', '(27) 99958-8954'), (2, 'Luiz', '(27) 99528-8966'), (3, 'Henrique', '(27) 99452-8524'), (4, 'Julia', '(27) 94521-5558'), (5, 'Isadora', '(27) 99784-7849'));

        insert into pedido values ((1, '2020-02-12 19:44:21', 2, 1), (2, '2020-02-12 19:55:01', 1, 3), (3, '2020-02-12 20:12:36', 3, 3),(4, '2020-02-12 20:33:55', 4, 5), (5, '2020-02-12 20:55:12', 5, 4));

        insert into cardapio_pedido values ((5, 1, 2), (4, 5, 1), (2, 3, 1), (3, 2, 3), (2, 4, 1));


### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
#### 9.1	CONSULTAS DAS TABELAS COM TODOS OS DADOS INSERIDOS (Todas) <br>

        select * from funcionario
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/01.png "Funcionario")
        
        select * from cliente
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/02.png "Cliente")
        
        select * from pedido
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/03.png "Pedido")

        select * from telefone
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/04.png "Telefone")

        select * from endereco
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/05.png "Endereço")

        select * from cardapio
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/06.png "Cardápio")

        select * from cardapio_pedido
     
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/07.png "Cardápio Pedido")

># Marco de Entrega 01: Do item 1 até o item 9.1<br>

#### 9.2	CONSULTAS DAS TABELAS COM FILTROS WHERE (Mínimo 4)<br>
#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E TABELAS OU CAMPOS RENOMEADOS (Mínimo 11)
    a) Criar 5 consultas que envolvam os operadores lógicos AND, OR e Not
    b) Criar no mínimo 3 consultas com operadores aritméticos 
    c) Criar no mínimo 3 consultas com operação de renomear nomes de campos ou tabelas

#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE E DATAS (Mínimo 12) <br>
    a) Criar outras 5 consultas que envolvam like ou ilike
    b) Criar uma consulta para cada tipo de função data apresentada.

#### 9.5	INSTRUÇÕES APLICANDO ATUALIZAÇÃO E EXCLUSÃO DE DADOS (Mínimo 6)<br>
    a) Criar minimo 3 de exclusão
    b) Criar minimo 3 de atualização

#### 9.6	CONSULTAS COM INNER JOIN E ORDER BY (Mínimo 6)<br>
    a) Uma junção que envolva todas as tabelas possuindo no mínimo 2 registros no resultado
    b) Outras junções que o grupo considere como sendo as de principal importância para o trabalho

#### 9.7	CONSULTAS COM GROUP BY E FUNÇÕES DE AGRUPAMENTO (Mínimo 6)<br>
    a) Criar minimo 2 envolvendo algum tipo de junção

#### 9.8	CONSULTAS COM LEFT, RIGHT E FULL JOIN (Mínimo 4)<br>
    a) Criar minimo 1 de cada tipo

#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Mínimo 6)<br>
        a) Uma junção que envolva Self Join (caso não ocorra na base justificar e substituir por uma view)
        b) Outras junções com views que o grupo considere como sendo de relevante importância para o trabalho

#### 9.10	SUBCONSULTAS (Mínimo 4)<br>
     a) Criar minimo 1 envolvendo GROUP BY
     b) Criar minimo 1 envolvendo algum tipo de junção

># Marco de Entrega 02: Do item 9.2 até o ítem 9.10<br>

### 10 RELATÓRIOS E GRÁFICOS

#### a) análises e resultados provenientes do banco de dados desenvolvido (usar modelo disponível)
#### b) link com exemplo de relatórios será disponiblizado pelo professor no AVA
#### OBS: Esta é uma atividade de grande relevância no contexto do trabalho. Mantenha o foco nos 5 principais relatórios/resultados visando obter o melhor resultado possível.

    

### 11	AJUSTES DA DOCUMENTAÇÃO, CRIAÇÃO DOS SLIDES E VÍDEO PARA APRESENTAÇAO FINAL <br>

#### a) Modelo (pecha kucha)<br>
#### b) Tempo de apresentação 6:40 

># Marco de Entrega 03: Itens 10 e 11<br>
<br>
<br>
<br> 



### 12 FORMATACAO NO GIT:<br> 
https://help.github.com/articles/basic-writing-and-formatting-syntax/
<comentario no git>
    
##### About Formatting
    https://help.github.com/articles/about-writing-and-formatting-on-github/
    
##### Basic Formatting in Git
    
    https://help.github.com/articles/basic-writing-and-formatting-syntax/#referencing-issues-and-pull-requests
    
    
##### Working with advanced formatting
    https://help.github.com/articles/working-with-advanced-formatting/
#### Mastering Markdown
    https://guides.github.com/features/mastering-markdown/

    
### OBSERVAÇÕES IMPORTANTES

#### Todos os arquivos que fazem parte do projeto (Imagens, pdfs, arquivos fonte, etc..), devem estar presentes no GIT. Os arquivos do projeto vigente não devem ser armazenados em quaisquer outras plataformas.
1. <strong>Caso existam arquivos com conteúdos sigilosos<strong>, comunicar o professor que definirá em conjunto com o grupo a melhor forma de armazenamento do arquivo.

#### Todos os grupos deverão fazer Fork deste repositório e dar permissões administrativas ao usuário do git "profmoisesomena", para acompanhamento do trabalho.

#### Os usuários criados no GIT devem possuir o nome de identificação do aluno (não serão aceitos nomes como Eu123, meuprojeto, pro456, etc). Em caso de dúvida comunicar o professor.


Link para BrModelo:<br>
http://www.sis4.com/brModelo/download.html
<br>


Link para curso de GIT<br>
![https://www.youtube.com/curso_git](https://www.youtube.com/playlist?list=PLo7sFyCeiGUdIyEmHdfbuD2eR4XPDqnN2?raw=true "Title")


