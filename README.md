# Teamcity-SSL
This repository provides a setup for running a TeamCity server with Traefik reverse proxy and SSL provider on production. The configuration is done using Docker Compose.

### Prerequisites
Make sure you have Docker and Docker Compose installed on your machine before proceeding with the setup.

### Directory Structure
The directory structure of this repository is as follows:

```markdown
traefik/
    Dockerfile
    traefik.yml
docker-compose.yml
LICENCE
README.md
```

- `traefik/` directory contains the Dockerfile and configuration file for Traefik.
  - `Dockerfile` defines the Docker image for Traefik.
  - `traefik.yml` contains the configuration for Traefik. (This is where you'll provide your email address for Let's Encrypt.)
- `docker-compose.yml` defines the services and their configurations using Docker Compose.
- `LICENSE` contains the license information for this repository.
- `README.md` (this file) provides an overview of the repository and setup instructions.

### Setup
Follow the steps below to set up the TeamCity-SSL:
> **Note:** The setup instructions assume that you have a domain name and DNS records pointing to your server. Plus you have already configured your domain and email in [traefik.yml](traefik/traefik.yml).

1. Clone this repository to your local machine:
    ```bash
    git clone https://github.com/KingBHD/Teamcity-SSL.git
    cd Teamcity-SSL
    ```
2. Edit the `docker-compose.yml` file to configure the necessary volumes, ports, and environment variables according to your requirements. By default, the TeamCity server is exposed on port 8111, Traefik on ports 80 and 443. You can also uncomment and configure the TeamCity agent service if needed.
3. Build the Traefik Docker image:
    ```bash
    docker-compose -f docker-compose.yml build
    ```
4. Start the services:
    ```bash
    docker-compose up -d
    ```

This will start the TeamCity server, Traefik reverse proxy, and optionally the TeamCity agent if enabled. The services will be running in the background (-d flag).

### Accessing the Service(s)
- TeamCity Server: You can access the TeamCity server by navigating to domain in your web browser. Which you have set in [traefik.yml](traefik/traefik.yml).

### SSL Configuration
This setup utilizes Traefik as the SSL provider. By default, Traefik uses the ACME protocol to automatically obtain SSL certificates from Let's Encrypt. The SSL certificates and related configuration are stored in the `traefik` volume.

Please note that in a production environment, you might want to customize the SSL configuration and use your own SSL certificates.

### License
This repository is licensed under the terms of the GNU Affero General Public License v3.0. See the [LICENSE](LICENSE) file for more details.

### Contributing
If you find any issues or have suggestions for improvements, feel free to open an issue or create a pull request. Contributions are always welcome!

### Acknowledgements
This setup is based on the TeamCity server image provided by JetBrains and the Traefik reverse proxy. Thanks to the respective developers for their excellent work.

### Disclaimer
This repository is provided as-is without any warranty. Use it at your own risk.