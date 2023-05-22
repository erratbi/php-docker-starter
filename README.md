Docker PHP MySQL Redis Nginx Traefik phpMyAdmin Starter Template
================================================================

This repository provides a starter template for setting up a Docker-based environment with PHP, MySQL, Redis, Nginx,
Traefik, and phpMyAdmin. It includes configuration files and Dockerfiles for each component, allowing you to quickly
spin up a development environment with these services.

Prerequisites
-------------

Before you begin, make sure you have the following prerequisites installed on your system:

- Docker: [Installation Guide](https://docs.docker.com/get-docker/)
- mkcert: [Installation Guide](https://github.com/FiloSottile/mkcert)

Getting Started
---------------

To use this starter template, follow the steps below:

1. Clone this repository to your local machine:

   `git clone https://github.com/erratbi/php-docker-starter`

2. Change to the cloned repository's directory:

   `cd php-docker-starter`

3. Rename env file and define your database credentials and app domaine name:

   `mv .env.example .env`

4. Generate SSL certificates using mkcert:

   `mkcert -install`
   `mkcert -cert-file="./certs/app-cert.pem" -key-file="./certs/app-key.pem" example.localhost *.example.localhost`

   The above command will generate a self-signed SSL certificate for the `example.localhost` domain and any subdomains
   like `phpmyadmin.example.localhost` which will give you access to phpMyAdmin. the certificates and
   keys files are saved in the `certs` directory.

5. Start the Docker containers:

`docker-compose up -d`

This command will start all the required containers defined in the `docker-compose.yml` file.

6. Access the services:

    - PHP application: Open your browser and visit `https://example.localhost`.
    - phpMyAdmin: Open your browser and visit `https://phpmyadmin.example.localhost`.
    - Traefik dashboard: Open your browser and visit `http://traefik.docker.localhost`.


7. Start developing!

   Your code goes in the `src` directory. You can now start building your PHP application and access it through the
   Nginx reverse proxy. MySQL and Redis are
   available as separate services for your application's database and caching needs.

Customization
-------------

Feel free to modify the provided configuration files to suit your specific requirements. For example, you can change PHP
versions, add additional PHP extensions, modify Nginx server configurations, etc.

Contributing
------------

Contributions to this starter template are welcome! If you find any issues or have suggestions for improvements, please
open an issue or submit a pull request.

License
-------

This repository is licensed under the [MIT License](https://chat.openai.com/LICENSE). Feel free to use and modify the
files as per the license terms.

Acknowledgements
----------------

This starter template was inspired by and built upon various open-source projects and configurations. We would like to
acknowledge the following projects:

- Docker: [https://www.docker.com](https://www.docker.com/)
- Traefik: [https://traefik.io](https://traefik.io/)
- phpMyAdmin: [https://www.phpmyadmin.net](https://www.phpmyadmin.net/)
- mkcert: <https://github.com/FiloSottile/mkcert>

Special thanks to the contributors of these projects for their valuable work.

* * * * *

That's it! You now have a Docker-based environment with PHP, MySQL, Redis, Nginx, Traefik, and phpMyAdmin up and
running. Happy coding!