# Microservices

# Requirements

- Docker

# To Run this project

1. Download the associated Dev-Stack:
    - [LEPR-DevStack](https://github.com/PlanetDebug/LEPR-Stack)
2. Copy or clone this repository into the `src` folder.

## Project Steps

1. Created Dockerfile for php - this enables the install and enable of specific tools: vi, pdo, xdebug

Note: This would require changes for deployment as Postgres saves credentials based on OS anyone who accesses the container is able to make changes, this would require additional authentication along with the removal of `bash` from the used images to prevent unwarranted access to the container. 

2. Created `docker-compose.yml` in this file the containers are set up (see README.md in root).

This is conducted to ensure the environment is reproducible. In this example I modified the LAMP stack I usually use to instead utilise postgres over MySQL, along with the addition of containers for additional technologies: RabbitMQ.

3. Created docker volume - this is a workaround, usually I would add a volume in the compose file linked to a directory within the root, this folder would be ignored by .gitignore, however, postgres does not allow for this, instead, the data is persisted in a volume and the database populated through a .sql file. 

4. Created SQL for creation of database, and data population. 

5. Created Models for the database tables

6. Create Controllers for each model. 

Utilising object oriented programming each of these is done through a class, due to some issues, mentioned below, this is the further milestone in a 2 hour period. 

## Occuring Issues

1. Postgres does not allow dir/data:db/data - workaround to use a docker volume instead.

2. Postgres security concern - this would have to be rectified in a deployment image to ensure only warranted access is permitted due to postgres policies. 

3. RabbitMQ starts without enabled plugins - as a workaround a enabled file was created and added via the volume: `./rabbitmq/enabled_plugins:/etc/rabbitmq/enabled_plugins` to ensure the necessary plugins were enabled at startup.

## Next
In continuation of this project I would first set up controllers for each model, furthermore I would first focus on developign the foreign service to send data to the microservice. 

From here the microservice should then check the received payload type, this should then route the informaiton to the correct microservices only. Using RabbitMQ this service would be the producer, the other services would act as consumers picking up the information from RabbitMQ based on the provided ruleset. 

More experience is required utilising RabbitMQ and Lumen before stepping to the next section. As such, I will continue working on these skills as I have not experienced these technologies before now.

# Lumen PHP Framework

[![Build Status](https://travis-ci.org/laravel/lumen-framework.svg)](https://travis-ci.org/laravel/lumen-framework)
[![Total Downloads](https://poser.pugx.org/laravel/lumen-framework/d/total.svg)](https://packagist.org/packages/laravel/lumen-framework)
[![Latest Stable Version](https://poser.pugx.org/laravel/lumen-framework/v/stable.svg)](https://packagist.org/packages/laravel/lumen-framework)
[![License](https://poser.pugx.org/laravel/lumen-framework/license.svg)](https://packagist.org/packages/laravel/lumen-framework)

Laravel Lumen is a stunningly fast PHP micro-framework for building web applications with expressive, elegant syntax. We believe development must be an enjoyable, creative experience to be truly fulfilling. Lumen attempts to take the pain out of development by easing common tasks used in the majority of web projects, such as routing, database abstraction, queueing, and caching.

## Official Documentation

Documentation for the framework can be found on the [Lumen website](https://lumen.laravel.com/docs).

## Contributing

Thank you for considering contributing to Lumen! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Security Vulnerabilities

If you discover a security vulnerability within Lumen, please send an e-mail to Taylor Otwell at taylor@laravel.com. All security vulnerabilities will be promptly addressed.

## License

The Lumen framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
