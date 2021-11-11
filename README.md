## Teste Prático Back-end Pleno WiiD

  
Este repositório foi criado com intuito de disponibilizar os pré-requisitos e o para prático para se tornar um Desenvolvedor Back-end Pleno da empresa Work In Ideas - WiiD.

### Introdução

Sistema de boleto de cobrança (com autenticação)

Desenvolva uma **RESTFul API** voltada para usuários cobrarem seus pagadores onde os mesmos poderão criar, editar, excluir e listar boletos e os pagadores. A API deverá ser desenvolvida em **.NET**. 

É de suma importância se utilizar das melhores práticas para um projeto seguro e organizado, como a utilização de **controllers**, **models**, **middlewares** ou semelhantes, controle de exceções, utilização de um **ORM** (*Object Relational Mapper*) para operações de banco de dados *(Eloquent, Doctrine ou outro*). Utilize um **banco de dados relacional** para persistir os dados da aplicação (*SQL Server, Postgresql ou MySQL de preferência*).

Para que os usuários possam realizar suas operações básicas eles devem estar autenticados no sistema. Utilize **JWT** (*JSON Web Token*) para controle de autenticação gerando um Token com **10 MINUTOS** de expiração.

#### Entidades

-	**Usuários**
	-	Id - Primary Key
	-	Nome - Obrigatório
	-	Sobrenome - Obrigatório
	-	Email - Obrigatório
	-	Senha (Criptografada) - Obrigatório

- **Boletos**
	- Id da boleto - Primary Key
	- Id do usuário - Obrigatório
	- Id do pagador - Obrigatório
	- Data Vencimento - Obrigatório
	- Valor do boleto - Obrigatório
	- instrucao1 - Não obrigatório
	- instrucao2 - Não obrigatório
	- instrucao3 - Não obrigatório
	- Descrição - Obrigatório
	- Tipo Multa - Não obrigatório - int -  1 - (Fixo) 2 - (Porcentagem)
	- Valor Multa - Obrigatorio se tiver "Tipo Multa" -  Valor da multa em modeda ou porcetagem
	- Tipo Juros - Não obrigatório - int -  1 - (Fixo) 2 - (Porcentagem)
	- Valor Juros - Obrigatorio se tiver "Tipo Juros" -  Valor da multa em modeda ou porcetagem
	- Tipo Desconto	- Não obrigatório - int -  1 - (Fixo) 2 - (Porcentagem)
	- Valor desconto - Obrigatorio se tiver "Tipo Desconto" -  Valor da multa em modeda ou porcetagem
	- Data Limite Desconto - Obrigatorio se tiver "Tipo Desconto"
	- Referencia - Não obrigatório

- **Pagadores**
	- Id - Primary Key
	- Id do usuário - Obrigatório
	- Nome do Pagador - Obrigatório
	- Documento do Pagador - Obrigatório
	- Celular do Pagador - Obrigatório
	- Email do Pagador - Obrigatório
	- Data Nascumento do Pagador - Obrigatório
	- Endereço Cep do Pagador - Obrigatório
	- Endereço Rua do Pagador - Obrigatório
	- Endereço Bairro do Pagador - Obrigatório
	- Endereço Numero do Pagador - Não obrigatório
	- Endereço Complemento do Pagador - Não obrigatório
	- Endereço Cidade do Pagador - Obrigatório
	- Endereço Estado do Pagador - Obrigatório

*Caso queira, você poderá criar propriedades.*

#### Rotas Obrigatórias:

- **usuários**
	- **POST /api/register** (rota para criação de novos usuários)
	- **POST /api/login** (rota para autenticação usuários)
	- **POST /api/me** (rota que retorna os dados do usuário, a senha deverá estar oculta. Essa rota necessita de autenticação)

- **Boletos** (Todas as requisições para as rotas de Boletos devem ser autenticadas por um token JWT gerado para o usuário)
	- **POST /api/boleto/create** (Cria um boleto)
	- **POST /api/boleto/update/{boleto_id}** (Altera um boleto do usuário)
	- **POST /api/boleto/delete/{boleto_id}** (Exclui um boleto do usuário)
	- **GET /api/boleto/me** (Lista todas os boletos do usuário logado)
	- **GET /api/boleto/pagador/{pagador_id}** (Lista todos os boletos do usuário por pagador)

- **Pagadores** (Todas as requisições para as rotas de Pagadores devem ser autenticadas por um token JWT gerado para o usuário)
	- **POST /api/pagador/create** (Cria um novo pagador)
	- **POST /api/pagador/update/{pagador_id}** (Altera um pagador do usuário)
	- **POST /api/pagador/delete/{pagador_id}** (Exclui um pagador do usuário, uma exceção deverá ser lançada caso se tente deletar um usuário que tenha algum boleto gerado)
	- **GET /api/pagador/me** (Lista todos os pagadores do usuário)

## Processo de submissão

O teste deve ser **versionado e disponibilizado no GitHub do candidado**.  
Enviar o link para:  [contato@wi-id.com](mailto:contato@wi-id.com)  e  [charles@wi-id.com](mailto:charles@wi-id.com)  

Boa sorte a todos e  
Bom trabalho!!

