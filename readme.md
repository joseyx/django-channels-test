# Django Channels Project

Este proyecto demuestra el uso de Django Channels para implementar características en tiempo real en una aplicación Django.

## Características

- Aplicación de chat en tiempo real usando WebSockets
- Integración con Django Channels
- Redis como backend de capa de canales

## Requisitos

- Python 3.8 o superior
- Django 5.1
- Channels 4.2
- Servidor Redis
- Docker (opcional, para la contenedorización)

## Sin Docker

1. Clona el repositorio:

   ```sh
   git clone https://github.com/joseyx/django-channels-pt1.git
   cd django-channels-pt1
   ```

2. Crea y activa un entorno virtual:

   ```sh
   python -m venv venv
   venv\Scripts\activate
   ```

3. Instala las dependencias:

   ```sh
   pip install -r requirements.txt
   ```

4. Instala Redis (si no está instalado) y arranca el servidor Redis.

### Configuracion

1. Actualiza la configuración de DATABASES en mysite/settings.py si no estás usando SQLite.

2. Asegúrate de que la configuración de CHANNEL_LAYERS en mysite/settings.py esté configurada para usar Redis:

   ```python
   CHANNEL_LAYERS = {
       "default": {
           "BACKEND": "channels_redis.core.RedisChannelLayer",
           "CONFIG": {
               "hosts": [("127.0.0.1", 6379)],
           },
       },
   }
   ```

### Ejecutando el Proyecto

1. Aplica las migraciones::

   ```sh
   python manage.py migrate
   ```

2. Arranca el servidor de desarrollo de Django::

   ```sh
   python manage.py runserver
   ```

3. Abre tu navegador y navega a http://127.0.0.1:8000/ para ver la aplicación en acción.

## Con Docker

1. Clona el repositorio:

   ```sh
   git clone https://github.com/joseyx/django-channels-pt1.git
   cd django-channels-pt1
   ```

2. Construye y arranca los contenedores Docker:

   ```sh
   docker-compose up --build
   ```

3. Aplica las migraciones:

   ```sh
   docker-compose exec web python ./mysite/manage.py migrate
   ```

4. Abre tu navegador y navega a http://127.0.0.1:8000/ para ver la aplicación en acción.

### Comandos de django con docker

1. Acceso a la Shell de Django

   ```sh
   docker-compose exec web python ./mysite/manage.py shell
   ```

2. Crear un Superusuario

   ```sh
   docker-compose exec web python ./mysite/manage.py createsuperuser
   ```
