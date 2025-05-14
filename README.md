# copier-django-template

**English 🇺🇸 | Português 🇧🇷**

## 🇺🇸 About

This project is a reusable [Copier](https://copier.readthedocs.io/) template for bootstrapping Django applications quickly and consistently. It includes a pre-configured Django project with:

- Django 5.2+
- Django Ninja 1.4+ (API)
- Environment variables using `python-decouple`

Use this template to save time setting up new Django projects, especially when working with APIs using Django Ninja.

---

## 🇺🇸 Getting Started

### 1. Create your project folder
```bash
mkdir -p ~/projects/django_ninja_example
````

### 2. Generate your project using Copier

```bash
copier copy https://github.com/rg3915/copier-django-template.git ~/projects/django_ninja_example
```

### 3. Set up the environment

```bash
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

---

## 🇧🇷 Sobre

Este projeto é um template reutilizável do [Copier](https://copier.readthedocs.io/) para iniciar aplicações Django de forma rápida e padronizada. Ele já vem com uma estrutura pronta contendo:

* Django 5.2+
* Django Ninja 1.4+ (para APIs)
* Variáveis de ambiente com `python-decouple`

Ideal para quem deseja agilidade na criação de projetos Django com suporte a APIs.

---

## 🇧🇷 Como começar

### 1. Crie a pasta do seu projeto

```bash
mkdir -p ~/projects/django_ninja_example
```

### 2. Gere seu projeto com o Copier

```bash
copier copy https://github.com/rg3915/copier-django-template.git ~/projects/django_ninja_example
```

### 3. Configure o ambiente

```bash
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

