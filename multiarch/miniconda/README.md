# docker login

docker login

# docker build

docker build -t miniconda-arm64:0.1 .

# docker run

docker run -it --rm miniconda-arm64:0.1 /bin/bash

# docker buildx

## check buildx drivers

docker buildx ls

## create builder

docker buildx create --name m1builder --driver docker-container

## use builder

docker buildx use m1builder

## inspect

docker buildx inspect --bootstrap

# multiarch build

docker buildx build \
--platform linux/arm64/v8,linux/amd64 \
-t alexwucpu05/conda-multiarch-test:0.1 \
--push \
.
