# Running Portainer behind Traefik Proxy

This repository provides instructions and configuration files to set up Portainer behind a Traefik reverse proxy.
Portainer is a web-based Docker management interface, and Traefik is a popular reverse proxy and load balancer.

## Prerequisites

Before you begin, ensure you have the following prerequisites installed and set up:

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Traefik](https://github.com/erkenes/docker-traefik)

## Installation

1. Clone this repository to your server:

    ```shell
    git clone https://github.com/erkenes/docker-portainer.git
    cd docker-portainer
    ```

2. Create a `.env` file and configure your settings. You can use the provided `.env.example`
   ```shell
   cp .env.example .env
   nano .env
   ```

3. (optional) if you want to secure portainer with [Authentik](https://github.com/erkenes/docker-authentik), uncomment the middleware line in the `docker-compose.yml` file
   ```yaml
   services:
     portainer:
       labels:
         - 'traefik.http.routers.${PROJECT_IDENTIFIER}.middlewares=middlewares-authentik@file'
   ```

4. Start Portainer
   ```shell
   docker compose up -d
   ```

5. Your Portainer instance is now up and running, ready to manage your Docker containers.

## Configuration

- `.env` - This file contains the environment variables for the Portainer container. You can change the domain for Portainer by changing the `PORTAINER_FQDN` variable.

## Troubleshooting

If you encounter issues or have questions, please open an issue or refer to the official documentation for [Portainer](https://docs.portainer.io/) and [Traefik](https://docs.traefik.io/).

## License

This project is licensed under the [MIT License](LICENSE).

## Contributing

Contributions are welcome! If you have any improvements, bug fixes, or feature requests, please open an issue or submit a pull request.
