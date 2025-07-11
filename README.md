# TecnoTasks – Prueba técnica Emasa-TecnoBot

¡Bienvenido!  
Este repositorio contiene el esqueleto de una pequeña API de gestión de tareas que **deberá completar** como parte del proceso de selección junior en Python
---

## 1. Objetivo del reto
Implementar un servicio REST que permita a cada usuario:

1. Registrarse e iniciar sesión (token JWT).  
2. Crear, listar, actualizar y eliminar **sus** tareas.  
3. Filtrar por estado (`is_done`), fecha de vencimiento (`due_before`) y buscar texto (`search`).  
4. Recibir resultados paginados (page size configurable).

Además, demostrar buenas prácticas de **pruebas**, **Git** y **documentación**.

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
```
#tecnotasks/
├─ manage.py
├─ requirements.txt # o pyproject.toml + poetry.lock
├─ Dockerfile # opcional (bonus)
├─ compose.yaml # opcional (bonus)
├─ core/ # settings, URLs globales
│ └─ ...
└─ tasks/ # <--- trabaja aquí
├─ models.py
├─ serializers.py
├─ views.py
├─ urls.py
└─ tests/
└─ test_api.py
README.md ← estás aquí
```

---

## 4. Puesta en marcha rápida

```bash
# 1. Clona tu fork y entra al directorio
git clone https://github.com/<tu-usuario>/tecnotasks.git
cd tecnotasks

# 2. Crear entorno virtual
python -m venv venv
source venv/bin/activate      #  Windows: .\venv\Scripts\activate

# 3. Instale dependencias
pip install -r requirements.txt
#   o: poetry install

# 4. Cargue variables de entorno si las añades (.env)

# 5. Preparar la base de datos
python manage.py migrate

# 6. Ejecutar servidor
python manage.py runserver
# Visita http://127.0.0.1:8000/
```

---

## 5. Endpoints requeridos
 

| Método        | Ruta                  | Descripción                                                           |
| ------------- | --------------------- | --------------------------------------------------------------------- |
| `POST`        | `/api/auth/register/` | Registro de usuario                                                   |
| `POST`        | `/api/auth/login/`    | Obtención de `access` y `refresh` token                               |
| `GET`         | `/api/tasks/`         | Listar tareas propias (`is_done`, `due_before`, `search`, paginación) |
| `POST`        | `/api/tasks/`         | Crear tarea                                                           |
| `GET`         | `/api/tasks/{id}/`    | Ver detalle                                                           |
| `PUT`/`PATCH` | `/api/tasks/{id}/`    | Actualizar                                                            |
| `DELETE`      | `/api/tasks/{id}/`    | Eliminar                                                              |

>Todos los endpoints, salvo registro/login, requieren encabezado
 `Authorization: Bearer <access_token>`.


## 6. Ejemplos rápidos (cURL)
```bash
# Registro
curl -X POST http://127.0.0.1:8000/api/auth/register/ \
     -H "Content-Type: application/json" \
     -d '{"username":"ana","password":"Secreto123"}'

# Login
curl -X POST http://127.0.0.1:8000/api/auth/login/ \
     -H "Content-Type: application/json" \
     -d '{"username":"ana","password":"Secreto123"}'
# => {"access": "...", "refresh": "..."}

# Crear tarea
curl -X POST http://127.0.0.1:8000/api/tasks/ \
     -H "Authorization: Bearer <access>" \
     -H "Content-Type: application/json" \
     -d '{"title":"Comprar leche","description":"Semidescremada","due_date":"2025-07-15"}'
```

---
## 7. Estilo de código
 * Sigue PEP 8.

 * Mantener funciones y métodos ≤ 25 líneas cuando sea posible.

 * Nombres explícitos (due_date, no fecha).

 * Sin lógica duplicada: use mixins/helpers.

---
## 8. Guía de Git
Fork este template → crea rama feature/solucion.

Commits atómicos y mensajes en imperativo:
```bash
git commit -m "Agrega modelo Task y migración inicial"
```


## 9. Licencia
Este proyecto se entrega únicamente con fines de evaluación técnica.
Puedes reutilizar el código para su portafolio personal, pero no lo publique hasta que termine el proceso de selección.

## 10. Decisiones de diseño (rellena aquí)
Explica brevemente:

* Arquitectura elegida (CBV + mixins, ViewSets, genéricos, etc.).

* Validaciones: campos obligatorios, fechas pasadas, etc.

* Pagos técnicos admitidos.





---
¡Éxitos! Esperamos ver tu creatividad y buenas prácticas.
Cualquier duda, abre un Issue en tu fork y la responderemos públicamente para que todos los participantes tengan la misma información.
