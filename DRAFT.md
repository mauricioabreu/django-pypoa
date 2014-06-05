Sobre o que eu devo falar?
==========================

Este documento descreve meus pensamentos sobre como deve ser uma introdução ao framework Django.

O que é Django?
===============

Django é um framework web. Ele foi desenhado para ser um framework com muitas baterias inclusas. Diferente de frameworks como Flask, Django tem seu próprio ORM, Admin, Auth e outras features.
A versão atual do Django é a 1.6, mas a 1.7 está em testes (dev). É possível observar no código fonte do Github comentários sobre a versão 1.9.

Como instalar?
==============

É possível instalar de várias maneiras. A melhor maneira de se instalar um pacote Python é utilizando o **pip**:
pip install Django (instalará a versão atual, 1.6.5 até o momento desta apresentação).
Para instalar a versão beta você pode utilizar pip e passando como parâmetro um link externo:
pip install https://www.djangoproject.com/download/1.7.b4/tarball/
Para instalar a versão de desenvolvimento (não segura) você pode utilizar o **git** baixando o repositório diretamente do .git do **Github**.
git clone https://github.com/django/django.git

Como o Django funciona?
=======================

Django é um framework MTV. MTV se refere a "Model Template View". Muitos podem acham que Django é um framework MVC, mas o Controller é uma propriedade que o framework se encarrega de cuidar, desenvolvendo-se entre o ciclo "Request->Response".

Primeiros passos
================

Após instalar o Django, é possível facilmente começar um novo projeto. Django vem com uma camada de comandos padrões. Um deles é o **django-admin**. Com ele você pode começar um novo projeto executando a seguinte linha no terminal:
django-admin.py startproject nomedoprojeto
O Django elimina o boilerplate que muitos frameworks não eliminam, deixando a carga do usuário criar sua própria estrutura de projeto. Isso é debatível.

A estrutura do projeto ficará assim:
nomedoprojeto
- manage.py
- nomedoprojeto/
-  \__init\__.py
-  settings.py
-  urls.py
-  wsgi.py

Breve descrição:
manage.py é utilizado para executar comandos padrões e customizados após o projeto ser criado. Não utilizar o django-admin.py para executar comandos.
nomedoprojeto é onde ficam os principais arquivos do projeto, no mesmo nível das **apps**.
settings.py é onde o Django busca configuração de debug, bancos de dados, caches, configurações customizadas, etc.
urls.py é a raiz das urls. Todas as principais rotas devem ser descritas neste urls.py, porém cada projeto pode ter o seu, organizando melhor as urls por **app**.
wsgi.py é o arquivo usado para fazer a implementação do projeto em produção. Os Webservers com Apache, Nginx, Gunicorn, etc usam esse arquivo como container de aplicação web.

Diferença entre app e projeto
=============================

Em Django há uma diferença entre app e projeto.
O projeto é o todo e um projeto pode conter nenhuma ou múltiplas apps.
Uma app é utilizada para descrever o comportamento do projeto. Cada app pode ter modelos, formulários e templates. E estes podem ser reutilizados em outras partes do seu projeto ou até em novos projetos.

Executando o projeto recém criado
=================================

manage.py vem com um comando chamado runserver. Django já vem com suporte a um servidor web de desenvolvimento. Para executar este servidor e consequentemente seu projeto:
Abra seu browser preferiro em localhost:8000 e você verá uma página de parabenização para você saber que o Django está funcionando corretamente.

Criando uma app
===============

Uma app é um módulo. Para criar uma app você também pode usar o arquivo manage.py:
manage.py startapp minhaapp

A estrutura da app ficará assim:
minhaapp/
- \__init\__.py
- admin.py
- models.py
- tests.py
- views.py

Models
======

Models são representações dos seus dados. Eles têm atributos \(campos\) e comportamentos.
Cada model mapeia uma única tabela de um banco de dados.
Models abstratos que não geram tabela, mas compõem atributos/comportamento.
Models proxy são apenas models para mudar o comportamento. É útil quando se quer inferir comportamentos em um model de terceiros.

Forms
=====

Forms são maneiras de entrar com dados na aplicação. Estes forms podem ou não ser **acoplados**.
Um form pode ou não ser acoplado a um model.
Quando um form é acoplado os campos são sanitizados e validados de acordo com os campos do model.
Quando não são acomplados, cada campo pode ter seus tipo de dado e uma validação.
A renderização do form fica mais fácil de controlar.


Views
=====

Views são funções ou classes Python que gerenciam uma requisição.
Responsáveis por gerenciar o **Request** e o **Response**.
Recebe: **Request**
Retorna: **Response**
O fluxo da aplicação é codificado nas views. Uma única view pode processar forms, models e templates.


URLs
====

Templates
=========

Testes
======

Encerramento
============
