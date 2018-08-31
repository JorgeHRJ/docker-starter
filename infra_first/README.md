# Docker Starter - First Infrastructure

Docker Starter Kit for a Symfony 4 project.
 
##### Stack: PHP 7 + MySQL + nginx
    
## Requirements

- Docker (https://docs.docker.com/install/)
- Docker Compose (https://docs.docker.com/compose/install/)

## Installation

1. Open docker-compose.yml. Then, find and replace 'boilerplate' word with your project name.
2. If you have a database sql dump you want to use, put it into db/data and uncomment lines at the bottom of db/Dockerfile 
   in order to use it.
3. Configure 'web/etc/nginx/conf.d/boilerplate-site.conf' with your project info.

