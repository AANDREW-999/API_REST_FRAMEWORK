# 📚 API REST Biblioteca

API REST desarrollada con **Django** y **Django REST Framework** para gestionar una biblioteca.  
Permite administrar **autores, libros y préstamos**, incluyendo funcionalidades de búsqueda, filtrado y endpoints personalizados.

---

# 🚀 Tecnologías utilizadas

- Python
- Django
- Django REST Framework
- Django Filter
- SQLite

---

# 📂 Estructura del proyecto


api_rest_biblioteca/
│
├── api_rest_biblioteca/
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── biblioteca/
│   ├── models.py
│   ├── serializers.py
│   ├── views.py
│   ├── urls.py
│   ├── admin.py
│   └── migrations/
│
└── db.sqlite3


---

# 📦 Instalación del proyecto

## 1️⃣ Clonar repositorio

```bash
git clone https://github.com/tu-usuario/api_rest_biblioteca.git
cd api_rest_biblioteca
```

## 2️⃣ Crear entorno virtual

```bash
python -m venv venv
```

### Activar entorno

#### Windows

```bash
venv\Scripts\activate
```

#### Linux / Mac

```bash
source venv/bin/activate
```

## 3️⃣ Instalar dependencias

```bash
pip install django
djangorestframework
django-filter
```

## 4️⃣ Ejecutar migraciones

```bash
python manage.py makemigrations
python manage.py migrate
```

## 5️⃣ Crear superusuario

```bash
python manage.py createsuperuser
```

## 6️⃣ Ejecutar servidor

```bash
python manage.py runserver
```

### Abrir en navegador

```
http://127.0.0.1:8000/
```

---

# 📡 Endpoints de la API

## Base URL

```
/api/
```

### 👨‍💻 Autores

| Método | Endpoint          | Descripción         |
|--------|-------------------|---------------------|
| GET    | /api/autores/     | Listar autores      |
| POST   | /api/autores/     | Crear autor         |
| GET    | /api/autores/{id}/| Ver autor           |
| PUT    | /api/autores/{id}/| Actualizar autor    |
| DELETE | /api/autores/{id}/| Eliminar autor      |

### 📚 Libros

| Método | Endpoint          | Descripción         |
|--------|-------------------|---------------------|
| GET    | /api/libros/      | Listar libros       |
| POST   | /api/libros/      | Crear libro         |
| GET    | /api/libros/{id}/ | Ver libro           |
| PUT    | /api/libros/{id}/ | Actualizar libro    |
| DELETE | /api/libros/{id}/ | Eliminar libro      |

### 🔎 Búsqueda

#### Ejemplo

```
/api/libros/?search=python
```

Busca por:

- título
- nombre del autor
- apellido del autor

### 🎯 Filtros

#### Ejemplo

```
/api/libros/?genero=novela
```

### 🔃 Ordenamiento

```
/api/libros/?ordering=titulo
```

o

```
/api/libros/?ordering=-fecha_publicacion
```

### ⭐ Endpoint personalizado

#### Libros disponibles

```
GET /api/libros/disponibles/
```

Devuelve únicamente los libros disponibles.

### 📖 Préstamos

| Método | Endpoint          | Descripción         |
|--------|-------------------|---------------------|
| GET    | /api/prestamos/   | Listar préstamos    |
| POST   | /api/prestamos/   | Crear préstamo      |

#### 📚 Endpoint para prestar libro

```
POST /api/libros/{id}/prestar/
```

Este endpoint:

- Verifica si el libro está disponible.
- Crea un préstamo para el usuario autenticado.
- Marca el libro como no disponible.

#### Ejemplo de respuesta

```json
{
 "mensaje": "Libro 'El Quijote' prestado exitosamente"
}
```

### 🔐 Seguridad de préstamos

En el `PrestamoViewSet`:

- **Administrador (is_staff)** puede ver todos los préstamos
- **Usuario normal** solo puede ver sus propios préstamos

### 🧪 Autenticación

Django REST Framework incluye login para pruebas

```
/api-auth/login/
```

---

# 👨‍💻 Autor

Proyecto desarrollado por:

**AANDREW**  
Tecnólogo en Análisis y Desarrollo de Sistemas