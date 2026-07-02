# Biblioteca.2026
# Sistema de Biblioteca Web

Este projeto foi desenvolvido para a disciplina de Programação Web II do Instituto Federal de Mato Grosso (IFMT) – Campus Campo Verde (Turma 2024).

---

## Integrantes do Grupo e Orientação
* **Michelly Aparecida Suhre**
* **Keylla Vitória Campos Silva**
* **Professor Orientador:** Samuel Oliveira Silva Bianch
* **Ano:** 2026

---

## Descrição do Projeto & Evolução

No primeiro bimestre, o foco do projeto foi estritamente a camada de apresentação, construindo uma interface visual organizada e estática utilizando o padrão MVC, onde todas as informações dos livros e autores estavam inseridas diretamente no código-fonte.

Nesta segunda etapa, o sistema passou por uma evolução significativa para se aproximar de aplicações reais de mercado. Foi implementada a **persistência de dados dinâmica utilizando o banco de dados MySQL**, permitindo que livros e autores passem por operações completas de manipulação sem a necessidade de alterar o código manualmente.

### Funcionalidades Atuais (CRUD)
* **Cadastro de Autores:** Inclusão de nome, biografia detalhada e foto. Permite listagem, edição de dados e exclusão.
* **Cadastro de Livros:** Inclusão de título, data de publicação, quantidade de páginas, sinopse e foto da capa. 
* **Relacionamento Dinâmico:** Vinculação do tipo **Um para Muitos (1:N)** através do Entity Framework Core, onde um autor pode possuir vários livros cadastrados, mas cada livro está associado a apenas um autor por meio da chave `AutorId`.

---

## Tecnologias Utilizadas
* **Backend:** ASP.NET Core MVC (Ambiente .NET)
* **Banco de Dados:** MySQL (Executado localmente)
* **ORM / Mapeamento:** Entity Framework Core & Migrations
* **Padrão de Projeto:** Padrão *Repository* (para abstração do acesso a dados)
* **Frontend:** Razor Pages (`.cshtml`), HTML5, CSS3, Bootstrap
* **IDE de Desenvolvimento:** Visual Studio / Visual Studio Code

---

## Organização do Projeto (Arquitetura MVC)

O sistema utiliza a arquitetura MVC combinada com uma camada de repositórios para garantir a separação de responsabilidades e um código limpo.

### Modelos (Models)
* `Livro.cs` → Estrutura de dados do livro e mapeamento da chave estrangeira.
* `Autor.cs` → Estrutura de dados do autor e sua relação com as obras.

### Controladores (Controllers)
* `BibliotecaController.cs` → Gerencia o fluxo do catálogo, detalhes dos livros e as ações de salvar, editar e deletar do CRUD.

### Repositórios (Repositories)
* `LivroRepository.cs` → Abstrai o acesso ao banco para a tabela de livros, utilizando `.Include(l => l.Autor)` para carregar os relacionamentos.
* `AutorRepository.cs` → Centraliza as operações de banco referentes à tabela de autores.

### Vistas (Views)
* `Views/Biblioteca/Index.cshtml` → Página inicial com carrossel dinâmico de destaques e listagem do catálogo geral.
* `Views/Biblioteca/Livro.cshtml` → Página detalhada exibindo capa, sinopse completa e dados do autor.
* `Views/Shared/_Layout.cshtml` → Layout padrão compartilhado (cabeçalho, navegação e rodapé).

---

## Como Executar o Projeto

### Pré-requisitos
Antes de começar, certifique-se de ter instalado em sua máquina:
1. SDK do .NET instalado.
2. Servidor MySQL Server ativo localmente.

### Passos para Configuração e Execução

1. **Clonar o Repositório:**
2. **Configure uma Conexão com o Banco de Dados:**
   *Abra o arquivo appsettings.jsonna raiz do projeto e edite a linha de conexão informando suas credenciais locais do MySQL:*
   *"ConnectionStrings": {
  "DefaultConnection": "Server=localhost;Database=biblioteca_db;Uid=SEU_USUARIO;Pwd=SUA_SENHA;"
}* 
3. **Criar a Estrutura do Banco Automaticamente (Migrações):**
*Execute o comando abaixo no terminal da pasta do projeto para que o Entity Framework gere o banco de dados e as tabelas ( livrose autores) no seu MySQL:*
*dotnet ef database update*
4. **Rodar a aplicação:**
*Iniciar o servidor local do projeto:*
*dotnet run*
