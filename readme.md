# Django Channels Project

This project demonstrates the use of Django Channels to implement real-time features in a Django application.

## Features

- Real-time chat application using WebSockets
- Django Channels integration
- Redis as the channel layer backend

## Requirements

- Python 3.8 or higher
- Django 5.1
- Channels 4.2
- Redis server

## Installation

1. Clone the repository:

   ```sh
   git clone https://github.com/joseyx/django-channels-pt1.git
   cd django-channels-pt1
   ```

2. Create and activate a virtual environment:

   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. Install the dependencies:

   ```sh
   pip install -r requirements.txt
   ```

4. Install Redis (if not already installed) and start the Redis server.

## Configuration

1. Update the `DATABASES` setting in `mysite/settings.py` if you are not using SQLite.

2. Ensure the `CHANNEL_LAYERS` setting in `mysite/settings.py` is configured to use Redis:

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

## Running the Project

1. Apply the migrations:

   ```sh
   python manage.py migrate
   ```

2. Start the Django development server:

   ```sh
   python manage.py runserver
   ```

3. Open your browser and navigate to `http://127.0.0.1:8000/` to see the application in action.
