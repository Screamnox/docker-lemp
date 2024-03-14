# LEMP Development Environment with Docker Compose

## Getting Started

This project provides a Docker Compose setup for a **development** (not production) environment with the following services:
- Nginx (web server)
- PHP (application runtime)
- MariaDB (database server)
- phpMyAdmin (database administration tool)

## Prerequisites
- Docker: Ensure you have Docker installed on your system. Refer to the official documentation for installation instructions: https://docs.docker.com/engine/install/
- Docker Compose: Install Docker Compose following the guide: https://docs.docker.com/compose/install/ (In the following, it is assumed that you have a recent version of Docker that allows you to perform commands with `docker compose` otherwise replace them with `docker-compose`.)

## Project Structure
```
.
├── app              # Your application code goes here
├── .docker
│   ├── nginx
│   │   └── conf.d   # Nginx configuration files
│   └── php
│       └── Dockerfile  # PHP Dockerfile
├── .env          # Environment variables (like, database password)
├── README.md  # This file
└── compose.yaml  # Docker Compose configuration
```

## Preparation
1. Clone the Repository:
```bash
git clone https://github.com/Screamnox/docker-lemp.git
```

2. Replace `app` Directory:

    - If you already have your application code, replace the `app` directory (containing a basic `index.php` file to say "Hello World") with your codebase.
    - If you're starting a new project, create your application code within the `app` directory (you can remove also `index.php` file). 

4. Environment Variables:

For sensitive information like database passwords, it's recommended to use a `.env` file. Create a `.env` file (not tracked by Git) and define variables like `MYSQL_ROOT_PASSWORD=your_password`. Reference them in `compose.yaml` using `${VARIABLE_NAME}` syntax.

## Customization (Optional)

You can modify environment variables, configuration options, ports, volumes, and custom Dockerfiles directly in the corresponding files (`compose.yaml`, `.env`, `.docker/*`). Don't forget to refer to the official documentation for Nginx, MariaDB, and PHP for further configuration options.

## Running the Environment
1. Navigate to the Project Directory:
```bash
cd docker-lemp
```
2. Build and Start Services:
```bash
docker compose up -d
```
- The `-d` flag runs the containers in detached mode (background).

## Accessing Services
- Web Application: Your application will be accessible at `http://localhost:80` (default port).
- phpMyAdmin: The phpMyAdmin interface will be available at `http://localhost:8080` (default port). Use `root` for the username and the password set in the `MYSQL_ROOT_PASSWORD` environment variable (default: root).

## Stopping and Removing Services:
### Stop services:
```bash
docker compose stop
```
### Remove Containers and Volumes (Optional):
```bash
docker compose down --volumes
```
- Refer to the Docker Compose documentation for details: https://docs.docker.com/reference/cli/docker/compose/down/
