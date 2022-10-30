# marvel_yearbook

## Project prereq
```
Make sure you have docker installed
```

### Build a docker image
```
docker build -t <insert-image-name>
```

### Run docker container 
```
docker run -it -p 8080:80 -d --name <insert-container-name> <insert-image-name>
```