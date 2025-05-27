# 🚀 ACL Padrão com Filament

Este repositório contém um projeto Laravel 12 que implementa um sistema de Controle de Lista de Acesso (ACL) utilizando o painel administrativo Filament e o pacote Spatie Permission. O objetivo é fornecer uma base sólida para gerenciamento de usuários, papéis (roles) e permissões.

## 📜 Visão Geral

*   **Framework:** Laravel 12
*   **Painel Admin:** Filament 3.x
*   **Controle de Acesso:** Spatie Laravel Permission 6.x
*   **PHP:** 8.2+

O projeto oferece uma estrutura organizada para gerenciar o acesso a diferentes partes da sua aplicação, facilitando a criação de interfaces administrativas com Filament.

## 🔑 Lógica de Permissões (Spatie Permission)

Este projeto utiliza o pacote `spatie/laravel-permission` para gerenciar o controle de acesso. A lógica principal se baseia em três componentes:

1.  **Usuários (Users):** Representam os indivíduos que interagem com o sistema.
2.  **Papéis (Roles):** Agrupam um conjunto de permissões. Funcionam como "funções" ou "cargos" dentro do sistema (ex: Administrador, Editor, Visitante).
3.  **Permissões (Permissions):** Definem ações específicas que podem ou não ser realizadas (ex: `criar post`, `editar usuário`, `ver relatório`).

A relação funciona da seguinte maneira:

*   Um **Usuário** pode ter um ou mais **Papéis** atribuídos.
*   Um **Papel** possui uma ou mais **Permissões** associadas a ele.
*   O sistema verifica se um **Usuário** tem uma determinada **Permissão**. Essa verificação pode ser direta (permissão atribuída diretamente ao usuário) ou, mais comumente, indireta: o sistema verifica se algum dos **Papéis** do usuário possui a **Permissão** necessária.

**Exemplo:**

*   O usuário "João" tem o papel "Editor".
*   O papel "Editor" tem as permissões "criar post" e "editar post".
*   Quando João tenta criar um post, o sistema verifica: João tem a permissão "criar post"? Sim, pois ele tem o papel "Editor", que por sua vez possui essa permissão.

Essa estrutura oferece flexibilidade para gerenciar o acesso de forma granular e organizada.

## 🛠️ Pré-requisitos

Antes de começar, garanta que seu ambiente de desenvolvimento atenda aos seguintes requisitos:

*   **PHP:** Versão 8.2 ou superior.
    ```bash
    php -v
    ```
*   **Composer:** Gerenciador de dependências para PHP. ([Instrução de Instalação](https://getcomposer.org/))
*   **Conexão com a Internet:** Para baixar as dependências.
*   **Banco de Dados:** Um SGBD compatível com Laravel (MySQL, PostgreSQL, SQLite, etc.).

## ⚙️ Passos para Instalação e Configuração

Siga estas etapas para configurar o projeto localmente:

1.  **Clonar o Repositório:**
    Obtenha o código-fonte do projeto.
    ```bash
    git clone https://github.com/GabrielCapoia-Dev/ACL-Padrao-Filament.git
    ```
    Ou baixe o ZIP diretamente do GitHub.

2.  **Navegar para o Diretório:**
    Entre na pasta do projeto recém-clonado.
    ```bash
    cd ACL-Padrao-Filament
    ```

3.  **Instalar Dependências:**
    Use o Composer para instalar os pacotes PHP necessários.
    ```bash
    composer install
    ```

4.  **Configurar Variáveis de Ambiente:**
    Copie o arquivo de exemplo `.env.example` para `.env`.
    ```bash
    # Linux / macOS
    cp .env.example .env

    # Windows (prompt de comando)
    copy .env.example .env
    ```
    Abra o arquivo `.env` e configure as variáveis, especialmente as de conexão com o banco de dados (`DB_CONNECTION`, `DB_HOST`, `DB_PORT`, `DB_DATABASE`, `DB_USERNAME`, `DB_PASSWORD`).

5.  **Gerar Chave da Aplicação:**
    Gere a chave de segurança única para a aplicação.
    ```bash
    php artisan key:generate
    ```

6.  **Configurar Banco de Dados:**
    Execute as migrações para criar as tabelas e os seeders para popular o banco com dados iniciais (incluindo o usuário admin).
    ```bash
    php artisan migrate:refresh --seed
    ```
    *Nota: `migrate:refresh` apaga todas as tabelas e as recria. Use `php artisan migrate --seed` se preferir apenas aplicar novas migrações e popular.* 

## ▶️ Executando a Aplicação

Após a configuração, inicie o servidor de desenvolvimento local do Laravel:

```bash
php artisan serve
```

A aplicação estará acessível, por padrão, em `http://127.0.0.1:8000` ou `http://localhost:8000`.

## 🔑 Acessando o Painel Administrativo

1.  Abra seu navegador e acesse a URL da aplicação seguida de `/admin` (ex: `http://127.0.0.1:8000/admin`).
2.  Utilize as credenciais padrão criadas pelo seeder:
    *   **Email:** `admin@admin.com`
    *   **Senha:** `123456`
3.  Após o login, você terá acesso ao painel do Filament para gerenciar usuários, papéis e permissões.

## 🖼️ Telas do Projeto

Nesta seção, você pode adicionar capturas de tela para ilustrar as principais funcionalidades e interfaces da aplicação.

_(Insira aqui as imagens/prints do projeto. Exemplo:)

**Tela de Login:**
```markdown
![Tela de Login](URL_DA_IMAGEM_AQUI)
```

**Dashboard Administrativo:**
```markdown
![Dashboard Administrativo](URL_DA_IMAGEM_AQUI)
```

## ✅ Considerações Finais

Este projeto serve como um ponto de partida robusto para aplicações Laravel que necessitam de controle de acesso detalhado com uma interface administrativa moderna. Sinta-se à vontade para adaptar e expandir conforme suas necessidades. Bom desenvolvimento! 👍

