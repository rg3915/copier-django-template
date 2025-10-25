# copier-django-template

Version: **1.1**

**English 🇺🇸 | Português 🇧🇷**

## 🇺🇸 About

This project is a reusable [Copier](https://copier.readthedocs.io/) template for bootstrapping Django applications quickly and consistently. It includes a pre-configured Django project with:

- Django 5.2+
- Django Ninja 1.4+ (API)
- Environment variables using `python-decouple`

Use this template to save time setting up new Django projects, especially when working with APIs using Django Ninja.

---

## 🇺🇸 Getting Started

### 1. Create your project folder and copier folder

```bash
mkdir -p ~/projects/django_ninja_example
mkdir -p ~/projects/copier_tmp
````

### 2. Generate your project using Copier

```bash
cd ~/projects/copier_tmp

python -m venv .venv
source .venv/bin/activate

pip install copier

copier copy https://github.com/rg3915/copier-django-template.git ~/projects/django_ninja_example
```

### Result

```
.
├── apps
│   ├── api.py
│   ├── asgi.py
│   ├── core
│   │   ├── api.py
│   │   ├── apps.py
│   │   ├── __init__.py
│   │   └── schemas.py
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── env.sample
├── manage.py
├── README.md
└── requirements.txt
```

### 3. How to run the new project

```bash
deactivate  # deactivate copier venv

cd ~/projects/django_ninja_example

python -m venv .venv
source .venv/bin/activate

pip install -r requirements.txt

cp env.sample .env
```

### 4. Run migrations and create a superuser

```bash
python manage.py migrate
python manage.py createsuperuser --username="admin" --email=""
```

### 5. Start the development server

```bash
python manage.py runserver
```

### Docs

Enter in

http://localhost:8000/api/v1/docs

![](img/swagger.png)

### Ninja Scaffold Command

This template includes a powerful Django management command to quickly scaffold apps with models and APIs.

**Create a new model with fields:**

```bash
python manage.py ninja_scaffold crm Person name:charfield email:emailfield age:integerfield
```

**Create model with relationships:**

```bash
python manage.py ninja_scaffold crm Provider name:charfield email:charfield person:foreignkey
```

**Generate schemas, API and admin from existing model:**

```bash
python manage.py ninja_scaffold --generate-from-model crm Person
```

**Supported field types:**
- Basic: `charfield`, `textfield`, `integerfield`, `booleanfield`
- Numbers/Dates: `decimalfield`, `datefield`, `datetimefield`
- Special: `emailfield`, `urlfield`, `slugfield`, `uuidfield`
- Files: `filefield`, `imagefield`
- Advanced: `jsonfield`, `foreignkey`, `manytomanyfield`, `onetoone`

**The command automatically generates:**
- `models.py` - Django model with specified fields
- `schemas.py` - Django Ninja schemas (input/output)
- `api.py` - Complete CRUD routes (GET, POST, PATCH, DELETE)
- `admin.py` - Django admin interface
- `apps.py` - App configuration with correct project path
- **Automatically updates** `settings.py` - Adds app to INSTALLED_APPS
- **Automatically updates** `api.py` - Adds router to main API

**Complete workflow example:**

```bash
# Enter the project folder
cd apps

# Create first app with model
python ../manage.py ninja_scaffold crm Person name:charfield email:emailfield age:integerfield
python manage.py makemigrations crm
python manage.py migrate

# Add another model to the same app
python ../manage.py ninja_scaffold crm Customer name:charfield email:emailfield age:integerfield
python manage.py makemigrations
python manage.py migrate

# Create a new app with model
python ../manage.py ninja_scaffold product Product title:charfield sku:charfield
python manage.py makemigrations product
python manage.py migrate
```

### Plus

If you want to run everything on Linux with a script, type

```bash
wget https://gist.githubusercontent.com/rg3915/7842b05ff93d9fd87f977d3c0b9300d3/raw/6dea5f85478bc582b86121f2bd8b79aab6518215/script.sh

source script.sh
```

![](img/copier.gif)

---

## 🇧🇷 Sobre

Este projeto é um template reutilizável do [Copier](https://copier.readthedocs.io/) para iniciar aplicações Django de forma rápida e padronizada. Ele já vem com uma estrutura pronta contendo:

* Django 5.2+
* Django Ninja 1.4+ (para APIs)
* Variáveis de ambiente com `python-decouple`

Ideal para quem deseja agilidade na criação de projetos Django com suporte a APIs.

---

## 🇧🇷 Como começar

### 1. Crie a pasta do seu projeto e a pasta do copier

```bash
mkdir -p ~/projects/django_ninja_example
mkdir -p ~/projects/copier_tmp
````

### 2. Gere seu projeto com o Copier

```bash
cd ~/projects/copier_tmp

python -m venv .venv
source .venv/bin/activate

pip install copier

copier copy https://github.com/rg3915/copier-django-template.git ~/projects/django_ninja_example
```

### Resultado

```
.
├── apps
│   ├── api.py
│   ├── asgi.py
│   ├── core
│   │   ├── api.py
│   │   ├── apps.py
│   │   ├── __init__.py
│   │   └── schemas.py
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── env.sample
├── manage.py
├── README.md
└── requirements.txt
```

### 3. Como rodar o novo projeto

```bash
deactivate  # desative a venv do copier

cd ~/projects/django_ninja_example

python -m venv .venv
source .venv/bin/activate

pip install -r requirements.txt

cp env.sample .env
```

### 4. Rode as migrações e crie um superusuário

```bash
python manage.py migrate
python manage.py createsuperuser --username="admin" --email=""
```

### 5. Inicie o servidor de desenvolvimento

```bash
python manage.py runserver
```

### Docs

Entre em

http://localhost:8000/api/v1/docs

![](img/swagger.png)


### Comando Ninja Scaffold

Este template inclui um poderoso comando de gerenciamento Django para criar rapidamente apps com models e APIs.

**Criar um novo model com campos:**

```bash
python manage.py ninja_scaffold crm Person name:charfield email:emailfield age:integerfield
```

**Criar model com relacionamentos:**

```bash
python manage.py ninja_scaffold crm Provider name:charfield email:charfield person:foreignkey
```

**Gerar schemas, API e admin de um model existente:**

```bash
python manage.py ninja_scaffold --generate-from-model crm Person
```

**Tipos de campos suportados:**
- Básicos: `charfield`, `textfield`, `integerfield`, `booleanfield`
- Números/Datas: `decimalfield`, `datefield`, `datetimefield`
- Especiais: `emailfield`, `urlfield`, `slugfield`, `uuidfield`
- Arquivos: `filefield`, `imagefield`
- Avançados: `jsonfield`, `foreignkey`, `manytomanyfield`, `onetoone`

**O comando gera automaticamente:**
- `models.py` - Model Django com os campos especificados
- `schemas.py` - Schemas do Django Ninja (input/output)
- `api.py` - Rotas CRUD completas (GET, POST, PATCH, DELETE)
- `admin.py` - Interface de administração Django
- `apps.py` - Configuração da app com caminho correto do projeto
- **Atualiza automaticamente** `settings.py` - Adiciona app em INSTALLED_APPS
- **Atualiza automaticamente** `api.py` - Adiciona router na API principal

**Exemplo de workflow completo:**

```bash
# Entrar na pasta do projeto
cd apps

# Criar primeira app com model
python ../manage.py ninja_scaffold crm Person name:charfield email:emailfield age:integerfield
python manage.py makemigrations crm
python manage.py migrate

# Adicionar outro model na mesma app
python ../manage.py ninja_scaffold crm Customer name:charfield email:emailfield age:integerfield
python manage.py makemigrations
python manage.py migrate

# Criar uma nova app com model
python ../manage.py ninja_scaffold product Product title:charfield sku:charfield
python manage.py makemigrations product
python manage.py migrate
```

### Plus

Se quiser rodar tudo no Linux com um script, digite

```bash
wget https://gist.githubusercontent.com/rg3915/7842b05ff93d9fd87f977d3c0b9300d3/raw/6dea5f85478bc582b86121f2bd8b79aab6518215/script.sh

source script.sh
```

![](img/copier.gif)