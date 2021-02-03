docker commands for testing

UI

# create image

docker build -t vetrip/employees-ui:2.00 .
docker image ls
docker push vetrip/employess-ui:2.0.0

# create container

docker run --name employees-ui -p 3100:80 --rm vetrip/employees-ui:2.0.0
docker container ls
docker exec it <CONTAINER_ID> sh
