# TRABALHO 01:  Lanchonete BD
Trabalho desenvolvido durante a disciplina de BD1

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
Claudio Magno : claudiomagno_21@hotmail.com<br>
Diogo Tomas : dreedd020@gmail.com<br>

### 2.INTRODUÇÃO E MOTIVAÇÃO<br>

> Diante dos desafios encontrados durante a pandemia, a lanchonete BD, uma startup no ramo, é uma tentativa de seus donos para tentar seu negócio próprio, buscando oportunidades de negócio. Com exemplos de diversos negócios semelhantes no mesmo ramo, o foco principal da lanchonete é a organização buscando sair na frente e se manter sempre firme, tendo em vista que muitas lanchonetes tem uma queda brusca nas vendas logo após o "boom" inicial. Com um sistema de negócio simples, mas eficiente, o objetivo é um sucesso a curto prazo e a expansão para franquias, seguindo a mesma regra de negócio implementada em seu sistema de controle, de modo a garantir a padronização e qualidade.
 

### 3.MINI-MUNDO<br>

> O sistema tem como base gerenciar o funcionamento de uma lanchonete otimizando o seu rendimento e a organização do negócio.
O cliente, possui um código que servirá para sua identificação, nome, um ou mais telefones e endereço detalhado comportando desde estado até o número da casa. Nesse sistema também é armazedo os dados do funcionário que possui um telefone para contato e o nome, além do código de identificação. O cardápio é armazendao possuindo nome, descrição, valor e um código de identificação para cada produto. Por fim, essas 3 entidades (cliente, funcionário e cardápio) se relacionam onde o cliente ao escolher um pedido do cardápio o repassa para o funcionário onde se armazenam a data/hora do pedido e é gerado um novo código para o controle do mesmo.

### 4.PROTOTIPAÇÃO, PERGUNTAS A SEREM RESPONDIDAS E TABELA DE DADOS<br>
#### 4.1 RASCUNHOS BÁSICOS DA INTERFACE (MOCKUPS)<br>

![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/628d8f4c1e485196ed16fbfcc0fece07dea3d5e2/images/image.png?raw=true "Title")

![Arquivo PDF do Protótipo da lanchonete](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/263c3fec9ec8afb584d38f284496825f779e8bf2/arquivos/mockup.pdf)

#### 4.2 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
* Relatório que apresente as informações de cada empregado que trabalha ou trabalhou na empresa, esse relatório deve conter: nome e telefone.
* Relatório que mostre todas as transações de cada período e seu faturamento, esse relatório deve conter: descrição da transação, valor e data.
* Relatório que mostre uma lista de prioridade dos produtos vendidos, apresentando quais produtos têm o maior retorno e quais têm o menor, esse relatório deve conter: nome do produto, valor, quantidade vendida em cada período.
* Relatório que mostre a variedade de clientes no estabelecimento, clientes novos e clientes frequentes, esse relatório deve conter: código do cliente, as vendas ligadas à esse código e as datas.
* Relatório que mostre as regiões com maior número de clientes cadastrados, contendo os resultados ordenados de forma decrescente pela quantidade de cada região, esse relatório deve conter: código do cliente, bairro, cidade e estado.
 
#### 4.3 TABELA DE DADOS DO SISTEMA:
![Tabela de dados da LanchoneteBD](https://github.com/ClaudioMBJr/Lanchonete-BD/raw/master/arquivos/TabelaLanchoneteBD.xlsx?raw=true "Tabela - LanchoneteBD")
    
    
### 5.MODELO CONCEITUAL<br>
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/conceitual%20v2.png "Modelo Conceitual")
    
    
        
    
#### 5.1 Validação do Modelo Conceitual
    Grupo DuCiclo: Gabrielle Azevedo e Renato Marques
    Foi avaliado que o Fornece poderia ser retirado e o Pedido ser conectado nos itens pedidos, formando o cardápio.
#### 5.2 Descrição dos dados 
    FUNCIONARIO: Tabela que armazena informações relativas ao funcionário da lanchonete
    cod_func: Campo que armazena o código específico do funcionário
    nome_func: Campo que armazena o nome do funcionário
    tel_func: Campo que armazena o telefone do funcionário
    
    PEDIDO: Tabela que armazena informações relativas ao pedido
    cod_pedido: Campo que armazena o código específico do pedido
    data_pedido: Campo que armazena a data do pedido
    
    CARDAPIO: Tabela que armazena informações relativas ao cardápio
    cod_prod: Campo que armazena o código do produto
    nome_prod: Campo que armazena o nome do produto
    desc_prod: Campo que armazena a descrição do produto
    valor_prod: Campo que armazena o valor do produto
    
    TELEFONE: Tabela que armazena informações relativas ao telefone
    cod_tel: Campo que armazena o código específico do telefone
    telefone: Campo que armazena o número do telefone
    
    CLIENTE: Tabela que armazena informações relativas ao cliente
    cod_cliente: Campo que armazena o código específico do cliente
    nome_cliente: Campo que armazena o nome do cliente
    
    ENDERECO: Tabela que armazena informações relativas ao endereço do cliente
    rua_cliente: Campo que armazena o nome da rua do cliente
    num_casa_cliente: Campo que armazena o número da casa do cliente
    bairro_cliente: Campo que armazena o nome do bairro do cliente
    cidade_cliente: Campo que armazena o nome da cidade do cliente
    uf_cliente: Campo que armazena o nome do estado do cliente


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

        select * from endereco where bairro_cliente = 'Barcelona';
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.2/1.bmp)

        select * from cardapio where valor_prod > 14;
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.2/2.bmp)

        select nome_func from funcionario where tel_func = '(27) 99452-8524';
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.2/3.bmp)

        select nome_cliente from cliente where cod_cliente = 3;
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.2/4.bmp)

#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E TABELAS OU CAMPOS RENOMEADOS (Mínimo 11)

 a) Consultas que envolvam os operadores lógicos AND, OR e Not
    
        select cod_pedido from pedido where (cod_cliente_pedido = 1 and cod_func_pedido = 3);
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.3/1.bmp)  

        select cod_cliente from endereco where (rua_cliente = 'Andorinhas' or rua_cliente = 'Cascardo');
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.3/2.bmp)
        
        select rua_cliente from endereco where bairro_cliente not in ('Barcelona');
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.3/3.bmp)
  
        select nome_prod from cardapio where (valor_prod <=15 and valor_prod >12);
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.3/4.bmp)

        select cod_pedido from cardapio_pedido where quant_pedido > 1;
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.3/5.bmp)

b) Consultas com operadores aritméticos 

        select cod_prod, nome_prod, desc_prod, valor_prod, (valor_prod + 2.9) as valor_prod from cardapio where nome_prod = 'Misto';
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.3/6.bmp)

        select cod_prod, nome_prod, desc_prod, valor_prod, (valor_prod * 1.2) as novo_valor_prod from cardapio where valor_prod < 15;
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.3/7.bmp)

        select cod_prod, nome_prod, desc_prod, valor_prod, (valor_prod * 0.9) as novo_valor_prod from cardapio where valor_prod > 14;
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.3/8.bmp)

c) Consultas com operação de renomear nomes de campos ou tabelas

        select cod_cliente as cod, rua_cliente as rua, num_casa_cliente as num_casa, bairro_cliente as bairro, cidade_cliente as cidade, uf_cliente as uf from endereco;
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.3/9.bmp)

        select cod_prod, nome_prod, desc_prod as ingredientes_prod, valor_prod as preco_prod from cardapio;
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.3/10.bmp)

        select cod_pedido, data_pedido as hora_pedido, cod_cliente_pedido as cod_cliente, cod_func_pedido as cod_func from pedido where cod_func_pedido = 3;
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.3/11.bmp)

#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE E DATAS (Mínimo 12) <br>
    a) Criar outras 5 consultas que envolvam like ou ilike
    b) Criar uma consulta para cada tipo de função data apresentada.

#### 9.5	INSTRUÇÕES APLICANDO ATUALIZAÇÃO E EXCLUSÃO DE DADOS (Mínimo 6)<br>

        delete from cardapio_pedido where quant_pedido > 2
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/delete%201.png)
       
        delete from endereco where bairro_cliente = 'Barcelona'
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/delete%202.png)
        
        delete from telefone where codigo = 4
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/delete%203.png)        

        update cliente set nome_cliente = 'Claudio Magno' where nome_cliente = 'Claudio'
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/update%201.png)    

        update cardapio set valor_prod = 15 where nome_prod = 'X-Egg Bacon'
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/update%202.png)  
        
        update endereco set num_casa_cliente = 123 where rua_casa_cliente = 12
        
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/update%203.png)  

#### 9.6	CONSULTAS COM INNER JOIN E ORDER BY (Mínimo 6)<br>

        select cliente.nome_cliente as nome, telefone.telefone as celular, endereco.bairro_cliente as bairro, pedido.data_pedido as data, cardapio_pedido.quant_pedido as quantidade, cardapio.nome_prod as pedido, funcionario.nome_func as atendente from cliente inner join telefone on (cliente.cod_cliente = telefone.codigo) inner join endereco on (cliente.cod_cliente = endereco.cod_cliente) inner join pedido on (cliente.cod_cliente = pedido.cod_cliente_pedido) inner join cardapio_pedido on (pedido.cod_pedido = cardapio_pedido.cod_pedido) inner join cardapio on (cardapio_pedido.cod_item = cardapio.cod_prod) inner join funcionario on (pedido.cod_func_pedido = funcionario.cod_func) order by data
    
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.6/9.6%201.png)
    
         select cliente.nome_cliente as nome, endereco.rua_cliente as rua, endereco.num_casa_cliente as numero_da_casa, endereco.bairro_cliente as bairro from cliente inner join endereco on (cliente.cod_cliente = endereco.cod_cliente)
    
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.6/9.6%202.png)
    
         select cliente.nome_cliente as nome, telefone.telefone as celular from cliente inner join telefone on (cliente.cod_cliente = telefone.codigo)
    
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.6/9.6%203.png)
    
         select pedido.data_pedido as pedidos_atrasados, cliente.nome_cliente, cardapio_pedido.quant_pedido from cliente inner join pedido on (cliente.cod_cliente = pedido.cod_cliente_pedido) inner join cardapio_pedido on (pedido.cod_pedido = cardapio_pedido.cod_pedido) order by pedidos_atrasados desc
    
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.6/9.6%204.png)
    
         select funcionario.nome_func as funcionario, cliente.nome_cliente as cliente_atendido from funcionario inner join pedido on (funcionario.cod_func = pedido.cod_func_pedido) inner join cliente on (pedido.cod_cliente_pedido = cliente.cod_cliente)
    
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.6/9.6%205.png)
    
         select cardapio.nome_prod as pedido, cardapio_pedido.quant_pedido as quantidade from cardapio inner join cardapio_pedido on (cardapio.cod_prod = cardapio_pedido.cod_item) order by quantidade
    
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.6/9.6%206.png)

#### 9.7	CONSULTAS COM GROUP BY E FUNÇÕES DE AGRUPAMENTO (Mínimo 6)<br>

    select cliente.nome_cliente as nome, count(pedido.cod_cliente_pedido) from cliente inner join pedido on (cliente.cod_cliente = pedido.cod_cliente_pedido) group by nome
    
    
    
    select funcionario.nome_func as funcionario, count(pedido.cod_func_pedido) from funcionario inner join pedido on (funcionario.cod_func = pedido.cod_func_pedido) group by funcionario
    
    
    
    select cardapio_pedido.cod_item as codigo_lanche, sum(cardapio_pedido.quant_pedido) as quantidade_total from cardapio_pedido group by codigo_lanche
    
    
    select telefone.telefone as telefone, telefone.codigo from telefone group by telefone, telefone.codigo
    
    
    
    select cardapio.nome_prod, avg(cardapio.valor_prod) from cardapio where (cardapio.valor_prod > 14) group by cardapio.nome_prod
    
    
    
    select funcionario.nome_func, funcionario.tel_func from funcionario group by nome_func, tel_func

#### 9.8	CONSULTAS COM LEFT, RIGHT E FULL JOIN (Mínimo 4)<br>

    select endereco.cod_cliente, endereco.rua_cliente, cliente.cod_cliente
    from endereco
    left outer join cliente
    on (cliente.cod_cliente = endereco.cod_cliente)
    order by cliente.cod_cliente;
    
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.8/1.bmp)

    select telefone.codigo, telefone.telefone, cliente.nome_cliente
    from cliente
    right outer join telefone
    on (telefone.codigo = cliente.cod_cliente)
    order by telefone.codigo;
    
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.8/2.bmp)
    
    select pedido.cod_pedido, pedido.data_pedido, pedido.cod_cliente_pedido, pedido.cod_func_pedido, cliente.nome_cliente
    from pedido
    full outer join cliente
    on (cliente.cod_cliente = pedido.cod_cliente_pedido)
    order by pedido.cod_cliente_pedido;
    
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.8/3.bmp)

    select pedido.data_pedido, pedido.cod_func_pedido, funcionario.cod_func
    from pedido
    full outer join funcionario
    on (pedido.cod_func_pedido = funcionario.cod_func)
    where funcionario.nome_func like '%i%';
    
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.8/4.bmp)

#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Mínimo 6)<br>
        a) Uma junção que envolva Self Join (caso não ocorra na base justificar e substituir por uma view)
        b) Outras junções com views que o grupo considere como sendo de relevante importância para o trabalho

#### 9.10	SUBCONSULTAS (Mínimo 4)<br>

     select cliente.nome_cliente, endereco.bairro_cliente from cliente 
     inner join endereco on (cliente.cod_cliente = endereco.cod_cliente 
     where (endereco.bairro_cliente = 'Taquara')
     
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.10/9.10%201.png)  

     select cardapio.nome_prod, sum (cardapio.valor_prod) from cardapio 
     where (cardapio.valor_prod > (select min (valor_prod) from cardapio + 1) 
     group by nome_prod, valor_prod order by cardapio.valor_prod
     
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.10/9.10%202.png)  

     select cliente.nome_cliente as nome, telefone.telefone as celular from cliente 
     inner join telefone on cliente.cod_cliente = telefone.codigo order by nome desc
     
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.10/9.10%203.png)  

     select cardapio.nome_prod as nome, cardapio_pedido.quant_pedido as quantidade 
     from cardapio_pedido inner join cardapio 
     on cardapio_pedido.cod_item = cardapio.cod_prod order by quantidade
     
![Alt text](https://github.com/ClaudioMBJr/Lanchonete-BD/blob/master/images/9.10/9.10%204.png) 
     

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


