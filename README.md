### Build Dev image
docker build -f dockers/Dockerfile.dev -t ccoupe/whisper:1.0 .

### Run Dev container
mount this dir:

docker run --gpus all --ipc=host --ulimit memlock=-1 --ulimit stack=67108864 -p5003:5003 -v ${HOME}/Projects/iot/whisper:/app -it --rm ccoupe/whisper:1.0

### Build production image
docker build -f dockers/Dockerfile.prod -t ccoupe/whisper:1.0 .

### Start production container
docker run --gpus all --ipc=host --ulimit memlock=-1 --ulimit stack=67108864 -p5003:5003  -it  -d --restart unless-stopped --name=glados-stt ccoupe/whisper:1.0
