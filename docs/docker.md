# Using Docker

With this installation guide, you can use our Docker image instead of [manually installing the backend](./git.md#install-backend). If you want to use the frontend, you will have to follow the [installation instructions](./git.md#install-frontend).

The backend Docker allows you to easily run the server in a Docker container without needing to install the required technologies and to configure a database on your system.

The following steps show how to install and run the backend Docker:

- [Install Docker](https://docs.docker.com/get-docker/) on your system
- __Optional:__ You can [run Docker as non root user on Linux](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user)
- [Install Docker Compose](https://docs.docker.com/compose/install/) (already included in Docker Desktop)
- Clone the backend Docker repository recursively:  
`git clone --recursive <backend-docker-repository>`
- Run the postgres container: `sudo docker-compose up postgres`
- Execute the database commands defined in the backend database file in a separate terminal to create all the tables needed:  
`sudo docker-compose exec postgres psql spanner\_db spanner\_user -f /opt/backend/database/spanners\_tables.pgsql`
- Stop the postgres container by typing `Ctrl+C`.
- Start the Docker containers: `sudo docker-compose up`

The server is now running and accessible under `localhost:4711` on the host system.

Notes:

- Code changes can be made directly in the backend directory.
- Changes will be compiled when `sudo docker-compose up` is called.
- Run commands in the backend by `sudo docker-compose exec backend <command>`. Replace `backend` with `postgres` to run commands on the postgres database Docker container.
- While `sudo docker-compose up` is running, the shell can be accessed in another terminal by `sudo docker-compose exec backend bash`.
- The backend code is located at `/opt/backend`.
- Rebuild Docker images (helpful if changes have been made in the Dockerfile): `sudo docker-compose up --build`
-  As TSL requires a signed certificate and a key file, the TSL encryption is disabled in `docker-compose.yml`. This allows a quick and easy installation of the server. The encryption is highly recommended if you use compose in production.