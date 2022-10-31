# marvel_yearbook

## Project prereq
```
Make sure you have docker installed
```

### Steps to get started
1. Start docker:
```
service docker start
```

2. Pull latest app docker image:
```
docker pull alza3im/marvel_front_end_vue:latest
```

3. Run container from above image:
```
docker run -it -p 8080:80 --rm --name marvel-flask-app-frontend  alza3im/marvel_front_end_vue:latest
```

### Frontend is currently hosted on an AWS ec2 instance http://18.212.55.232:8080
