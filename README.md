# Docker Setup for Nette

Highly customizable Docker setup for Nette projects development. 

## Local dev guide

1. Create `.docker/local/.env` based on `.docker/local/.env.example`.
2. Start containers using `./run.sh local up`.
3. Access the PHP container terminal using `docker exec -it ${APP_NAME}_php bash` (replace `${APP_NAME}` with your app name). Now, you can create a Nette project using:
```sh
composer create-project nette/web-project nette_app
```
The Nette project folder must be named `nette_app` because of how the `root` is configured in the `.docker/local/nginx/default.conf` file:
```conf
root /var/www/nette_app/www;
```
Choosing a different name for the Nette project is possible by modifying the `.docker/local/nginx/default.conf` file like so:
```conf
root /var/www/<YOUR_NETTE_APP_FOLDER_NAME>/www;
```