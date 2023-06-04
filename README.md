# Docker Compose Configuration for Apache, PHP 8.2, and MariaDB 10.11.3 (Development Environment)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![Apache](https://img.shields.io/badge/apache-%23D42029.svg?style=for-the-badge&logo=apache&logoColor=white) ![PHP](https://img.shields.io/badge/php-%23777BB4.svg?style=for-the-badge&logo=php&logoColor=white) ![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white) ![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white) ![NPM](https://img.shields.io/badge/NPM-%23CB3837.svg?style=for-the-badge&logo=npm&logoColor=white)

This is a sample Docker Compose configuration that sets up a development environment with Apache, PHP 8.2, and MariaDB 10.11.3. It allows you to quickly spin up a local development environment for web applications that require these technologies.

## Prerequisites
- Docker (https://www.docker.com/)
- Docker Compose (https://docs.docker.com/compose/)

## Usage
1. Clone this repository:
`git clone https://github.com/zeyadmbk/docker-compose-apache-php-mariadb-dev.git`
2. Navigate to the project directory:
`cd docker-compose-apache-php-mariadb-dev`
3. Modify the `docker-compose.yml` file according to your requirements. You can adjust the exposed ports, database credentials, and other settings as needed.
4. Start the containers:
`docker-compose -f docker-compose.yml up -d`
5. Access your web application in a browser:
`http://localhost:80`

## Configuration
The `docker-compose.yml` file contains the following services:

### `apache-php`
- Build: using custom docker image built using `./build/apache-php/Dockerfile` file.
- Ports:
  - `80:80` (map container port 80 to host port 80)
- Volumes:
  - `/usr/dev/project/:/var/www/html/` (mount the `/usr/dev/project/` directory to Apache's document root)

### `mariadb`
- Image: `mariadb:10.11.3`
- Environment variables:
  - `MYSQL_ROOT_PASSWORD` (set your desired root password)
  - `MYSQL_DATABASE` (set the name of the initial database) (Optional)
  - `MYSQL_USER` (a username account to be created when the container is created) (Optional)
  - `MYSQL_PASSWORD` (a password for the user account above to be created when the container is created) (Optional)

Feel free to modify this configuration based on your specific requirements.

## Notes
- This configuration is intended for development purposes only. It may not be suitable for production environments.
- Make sure to secure your database by using strong passwords and other security measures when deploying to a production environment.

## License
This project is licensed under the [MIT License](https://chat.openai.com/LICENSE). Feel free to use and modify it to suit your needs.

---

For more information on Docker Compose and its capabilities, please refer to the [official documentation](https://docs.docker.com/compose/).
