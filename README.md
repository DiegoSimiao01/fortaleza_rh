# Sistema de cadastro com tema do Fortaleza Esporte Clube

✨ Funcionalidades

    Página Principal: Um dashboard de boas-vindas com a navegação principal.

    Sistema de CRUD completo para Funcionários:

        Adicionar (Create): Formulário para cadastrar novos funcionários.

        Listar (Read): Lista todos os funcionários cadastrados no banco de dados.

        Editar (Update): Permite alterar as informações de um funcionário existente.

        Deletar (Delete): Permite remover um funcionário do sistema.

    Interface Temática: Layout e estilo (CSS) personalizados com as cores e logo do Fortaleza EC.

    Pronto para Produção: O projeto foi configurado para sair do ambiente de desenvolvimento (SQLite) e rodar em produção (PostgreSQL).

🛠️ Tecnologias Utilizadas

    Backend: Python 3.12, Django 5.2

    Frontend: HTML5, CSS3

    Banco de Dados (Desenvolvimento): SQLite3

    Banco de Dados (Produção): PostgreSQL (hospedado no Neon)

    Servidor WSGI: Gunicorn

    Serviço de Arquivos Estáticos: WhiteNoise

    Deploy (Produção): Render

🚀 Como Rodar o Projeto

O projeto está configurado para deploy em produção, mas pode ser rodado localmente com algumas etapas.

1. Rodando em Modo de Produção (Recomendado)

Este modo usa o mesmo banco de dados que está no Render (Neon).

    Clone o repositório:
    Bash

git clone https..

Crie e ative um ambiente virtual:
Bash

python -m venv venv
source venv/bin/activate  # No Linux/Mac
.\venv\Scripts\activate   # No Windows

Instale as dependências:
Bash

pip install -r requirements.txt

Crie um arquivo .env:

    Na raiz do projeto (ao lado do manage.py), crie um arquivo chamado .env.

    Adicione suas variáveis de ambiente (as mesmas que você usou no Render):

Ini, TOML

DATABASE_URL=postgres://...sua_url_secreta_do_neon...
DEBUG=True

Rode o servidor:
Bash

    python manage.py runserver

    Acesse http://127.0.0.1:8000/ no seu navegador.

2. Rodando em Modo de Desenvolvimento (Novo Banco SQLite)

Este modo ignora o Neon e cria um novo banco db.sqlite3 limpo.

    Siga os passos 1, 2 e 3 acima (clonar, criar venv, instalar dependências).

    Não crie o arquivo .env.

    Altere o arquivo sistema_rh/settings.py:

        Comente (com um #) a seção DATABASES do dj_database_url.

        Descomente (remova o #) a configuração original do DATABASES para SQLite3 (ela já deve estar lá, mais abaixo).

    Rode as migrações (para criar um novo db.sqlite3):
    Bash

python manage.py migrate

Crie um superusuário (para acessar o /admin):
Bash

python manage.py createsuperuser

Rode o servidor:
Bash

    python manage.py runserver

☁️ Configuração de Deploy (Render)

Este projeto está ativo na web, hospedado na plataforma Render.

    Serviço: Web Service

    Comando de Build: pip install -r requirements.txt && python manage.py collectstatic --noinput && python manage.py migrate

    Comando de Início: gunicorn sistema_rh.wsgi

    Variáveis de Ambiente Requeridas:

        DATABASE_URL: (A URL secreta do banco de dados PostgreSQL)

        DEBUG: False

        PYTHON_VERSION: (Ex: 3.12.3)

👨‍💻 Autor

    Diego Simião - GitHub: DiegoSimiao01
 
