# Leonardo Buonanno RM98315  
# Victor Fusco RM552399
# Matheus Da Silva Ferreira RM552431
# Lucas de Lavor RM552426
# Henrrique Ferreira Cardoso RM552325

1. Escolha da Arquitetura
Monolítica ou Microservices:
Monolítica: Como você está criando uma API CRUD básica com integração ao Oracle, a arquitetura monolítica seria mais adequada, pois simplifica o desenvolvimento e a manutenção. Em aplicações menores ou em MVPs, é mais fácil gerenciar a lógica e os componentes em um único projeto. Isso facilita a manutenção, reduz a sobrecarga de comunicação entre serviços e é menos complexo na fase inicial.
Microservices: Utilize esta abordagem se a aplicação crescer e houver necessidade de escalabilidade, onde cada componente (serviço) pode ser desenvolvido, implantado e gerenciado de forma independente.
Neste caso, vamos adotar a arquitetura monolítica devido à simplicidade e ao escopo limitado.

# Design patterns utilizados: 

Repository Pattern
Propósito: Abstrair a lógica de acesso a dados, fornecendo uma interface entre a API e o banco de dados Oracle. Esse padrão facilita a separação das regras de negócio da lógica de persistência de dados.
Benefícios: Facilita a manutenção, trocas de banco de dados e testes unitários.

Unit of Work Pattern
Propósito: Coordenar a gravação das mudanças no banco de dados como uma única operação, gerenciando transações e garantindo consistência de dados.
Benefícios: Evita múltiplas conexões desnecessárias ao banco, garantindo que operações de diferentes repositórios sejam tratadas em uma única transação.

Singleton Pattern
Propósito: Garantir que uma classe tenha apenas uma única instância durante a execução da aplicação. No contexto do seu projeto, pode ser usado para gerenciar a configuração de conexão com o banco de dados Oracle ou outros recursos globais.
Benefícios: Controle centralizado de recursos compartilhados.

Factory Pattern
Propósito: Desacoplar a criação de objetos complexos (por exemplo, conexões de banco de dados) da lógica da aplicação. Ideal para a criação de diferentes tipos de conexões, como o Oracle ou outro banco de dados.
Benefícios: Facilita a substituição de implementações sem alterar o código que usa os objetos.

Dependency Injection
Propósito: Facilitar a injeção de dependências como serviços e repositórios nos controladores da API, promovendo uma arquitetura desacoplada.
Benefícios: Facilita a testabilidade e manutenção ao permitir a injeção de mock objects.

Instruções para rodar a API

Pré-requisitos
.NET SDK: Certifique-se de ter o SDK do .NET instalado.

Banco de Dados Oracle: Configure seu Oracle DB, instale o Oracle Client e tenha a string de conexão adequada pronta.

Configurar o Banco de Dados
Configuração da String de Conexão: No arquivo appsettings.json, adicione a string de conexão ao banco Oracle.

Adicionar o Contexto do Banco: Certifique-se de que o DbContext ou a configuração de acesso ao banco esteja configurada no projeto.

Efetuar Migrações (se estiver usando Entity Framework): Se estiver usando o Entity Framework para manipular o banco, execute as migrações para criar ou atualizar o banco de dados:

Configurar o Projeto
Verifique se o arquivo Program.cs ou Startup.cs está configurado para registrar os serviços necessários, como o DbContext e o repositório

Rodar a API Localmente

Testar a API

 Publicar e Hospedar a API (opcional)
Se for necessário hospedar a API no Azure, AWS, ou outro servidor, você pode usar:
dotnet publish para criar o artefato de distribuição.
Docker (se estiver usando contêineres).
GitHub Actions ou outro pipeline de CI/CD para automação.
8. Verificar Logs e Erros
Verifique os logs no terminal para garantir que o projeto está rodando corretamente. Se houver falhas de conexão com o banco, ajuste a string de conexão e valide o status do banco de dados.
