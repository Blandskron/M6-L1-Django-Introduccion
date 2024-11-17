# Proyecto Educativo Django

Este proyecto educativo tiene como objetivo enseñar a los estudiantes los conceptos básicos y avanzados de Django, un framework web de alto nivel basado en Python. Sigue este tutorial paso a paso para comprender cómo configurar, desarrollar y desplegar una aplicación web utilizando Django.

---

## Índice

1. [Introducción a Django](#1-introducción-a-django)
2. [Requisitos Previos](#2-requisitos-previos)
3. [Configuración del Entorno](#3-configuración-del-entorno)
4. [Creación del Proyecto](#4-creación-del-proyecto)
5. [Estructura de Archivos](#5-estructura-de-archivos)
6. [Configuración Inicial](#6-configuración-inicial)
7. [Creación de una Aplicación](#7-creación-de-una-aplicación)
8. [Definición de Modelos](#8-definición-de-modelos)
9. [Creación de Vistas y URLs](#9-creación-de-vistas-y-urls)
10. [Uso del Panel Administrativo](#10-uso-del-panel-administrativo)

---

## 1. Introducción a Django

Django es un framework web escrito en Python que facilita el desarrollo rápido de aplicaciones web seguras y escalables. Proporciona un conjunto de herramientas integradas como un sistema ORM (Object Relational Mapping), un servidor de desarrollo y un panel administrativo preconfigurado.

## 2. Requisitos Previos

Antes de comenzar, asegúrate de cumplir con los siguientes requisitos:

- Python 3.8 o superior instalado.
- Acceso a una terminal (CMD, PowerShell o terminal de Linux/macOS).
- Un editor de texto, preferiblemente [Visual Studio Code](https://code.visualstudio.com/).

## 3. Configuración del Entorno

### Instalación de un Entorno Virtual

Un entorno virtual permite aislar las dependencias del proyecto. Sigue estos pasos:

1. Crea un entorno virtual:
   ```bash
   python -m venv venv
   ```
2. Activa el entorno virtual:
   - En Windows:
     ```bash
     venv\Scripts\activate
     ```
   - En macOS/Linux:
     ```bash
     source venv/bin/activate
     ```

3. Instala Django dentro del entorno virtual:
   ```bash
   pip install django
   ```

## 4. Creación del Proyecto

1. Crea un proyecto Django:
   ```bash
   django-admin startproject my_project
   ```
2. Navega a la carpeta del proyecto:
   ```bash
   cd my_project
   ```

## 5. Estructura de Archivos

El proyecto creado tendrá la siguiente estructura inicial:

```
my_project/
├── manage.py
├── my_project/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
```

## 6. Configuración Inicial

1. Aplica las migraciones iniciales para configurar la base de datos SQLite:
   ```bash
   python manage.py migrate
   ```
2. Inicia el servidor de desarrollo:
   ```bash
   python manage.py runserver
   ```
   Accede a `http://127.0.0.1:8000/` en tu navegador para confirmar que Django está funcionando.

## 7. Creación de una Aplicación

1. Crea una aplicación llamada `core`:
   ```bash
   python manage.py startapp core
   ```
2. Registra la aplicación en `settings.py`:
   ```python
   INSTALLED_APPS = [
       ...
       'core',
   ]
   ```

## 8. Definición de Modelos

Define un modelo en `core/models.py`:

```python
from django.db import models

class Estudiante(models.Model):
    nombre = models.CharField(max_length=100)
    apellido = models.CharField(max_length=100)
    correo = models.EmailField()

    def __str__(self):
        return f"{self.nombre} {self.apellido}"
```

Aplica las migraciones para reflejar el modelo en la base de datos:

```bash
python manage.py makemigrations
python manage.py migrate
```

## 9. Creación de Vistas y URLs

1. Define una vista básica en `core/views.py`:
   ```python
   from django.http import HttpResponse

   def index(request):
       return HttpResponse("Bienvenido a Django!")
   ```
2. Configura las rutas en `core/urls.py`:
   ```python
   from django.urls import path
   from . import views

   urlpatterns = [
       path('', views.index, name='index'),
   ]
   ```
3. Conecta las URLs de la aplicación al proyecto en `my_project/urls.py`:
   ```python
   from django.contrib import admin
   from django.urls import include, path

   urlpatterns = [
       path('admin/', admin.site.urls),
       path('', include('core.urls')),
   ]
   ```

## 10. Uso del Panel Administrativo

1. Registra el modelo en `core/admin.py`:
   ```python
   from django.contrib import admin
   from .models import Estudiante

   admin.site.register(Estudiante)
   ```
2. Crea un superusuario:
   ```bash
   python manage.py createsuperuser
   ```
3. Accede al panel administrativo en `http://127.0.0.1:8000/admin`.


## Conclusión

Este proyecto básico te ayudará a entender los fundamentos de Django. A medida que avances, puedes agregar más funcionalidades como formularios, autenticación de usuarios y APIs. ¡Explora, experimenta y disfruta aprendiendo Django!

---
