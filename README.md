# TecnoTasks – Prueba técnica *Backend* 🐍⚙️

¡Bienvenido!  
Este repositorio contiene el esqueleto de una pequeña API de gestión de tareas que **deberás completar** como parte del proceso de selección de *backend developers* junior en Python + Django.

---

## 1. Objetivo del reto
Implementar un servicio REST que permita a cada usuario:

1. Registrarse e iniciar sesión (token JWT).  
2. Crear, listar, actualizar y eliminar **sus** tareas.  
3. Filtrar por estado (`is_done`), fecha de vencimiento (`due_before`) y buscar texto (`search`).  
4. Recibir resultados paginados (page size configurable).

Además, demostrarás buenas prácticas de **pruebas**, **Git** y **documentación**.

---

## 2. Stack y dependencias

| Tecnología | Versión mínima | Uso principal |
|------------|---------------|---------------|
| Python     | 3.12          | Lenguaje base |
| Django     | 5.x           | Framework web |
| Django REST Framework | 3.15 | Endpoints REST |
| djangorestframework-simplejwt | 5.x | Autenticación JWT |
| pytest & pytest-django | 8.x | Pruebas unitarias |
| coverage.py | 7.x | Métrica de cobertura |
| (Opc.) Django-filters | 24.x | Filtros avanzados |
| (Opc.) Docker + Compose | latest | Contenedorización |

> **Bonus:** Si incluyes `ruff`/`flake8`, pre-commit hooks o un workflow de CI, ¡suma puntos extra!

---

## 3. Estructura del proyecto

