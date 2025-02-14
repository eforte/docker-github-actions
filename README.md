## Simple python docker dev example for the official docker docs
https://docs.docker.com/language/python/develop/

## Clone sample application
git clone https://github.com/estebanx64/python-docker-dev-example

## Create docker assets
cd python-docker-dev-example
docker init

## Run the application container
docker compose up --build

## Test the API endpoint
Open a new terminal then make a request to the server using the curl commands:
Create an object with a post method
curl -X 'POST' \
  'http://localhost:8001/heroes/' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "id": 1,
  "name": "my hero",
  "secret_name": "austing",
  "age": 12
}'

## Automatically Update Services
Use Compose Watch to automatically update your running Compose services as you edit and save your code. 
Add the following to the compose.yaml file, right after the line that reads - db-password:
    develop:
      watch:
        - action: rebuild
          path: .

## Run the application with Compose Watch
docker compose watch

In a different terminal, curl the application to get a response.
curl http://localhost:8001
You should see: "Hello, Docker!"

Any changes to the application's source files on your local machine will now be immediately reflected in the running container.

Open python-docker-dev-example/app.py in an IDE or text editor and update the Hello, Docker! string by adding a few more exclamation marks.
-    return 'Hello, Docker!'
+    return 'Hello, Docker!!!'

Save the changes to app.py and then wait a few seconds for the application to rebuild. Curl the application again and verify that the updated text appears.

curl the application to get a response.
curl http://localhost:8001
You should see: "Hello, Docker!!!"
