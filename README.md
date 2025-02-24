Overview:

This repository contains a configured Flask application that has run on Docker with Postgres. It also implements Gunicorn as a WSGI server and leverages Nginx for handling requests. Using Nginx, it has served static and user-uploaded media files as well. These are the applications dependencies: Flask v2.3.2, Docker v23.0.5, and Python v3.11.3.


Build Instructions:

1. You must initially confirm that you have Docker and Docker Compose installed on your system.
2. First, you must clone and cd into your repository using the commands:
   ```
   git clone <your-repo-url>
   cd <your-repo-name>
   ```
3. Create a .env.dev file in the project root to store environment variables for development.
4. Key Docker commands:
   Start services in development mode: If you want to bring up the development containers (which includes building images if necessary), use:
   ```
   docker compose up -d
   ```
   For development: Removing volumes along with containers:
   ```
   docker compose down -v
   ```
   For production: Bringing down the development containers (and the associated volumes with the -v flag):
   ```
   docker compose -f docker-compose.prod.yml down -v
   ```
   For building the production images and spinning up the containers: If you modify any Dockerfile or dependencies, rebuild the images with:
   ```
   docker compose -f docker-compose.prod.yml up -d --build
   ```
   Creating the table:
   ```
   docker-compose exec web python manage.py create_db
   ```
   Viewing logs for troubleshooting:
   ```
   docker compose -f docker-compose.prod.yml logs -f
   ```
   
   
