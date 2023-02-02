# check docker login

docker login

# check buildx drivers

docker buildx ls

# create builder

docker buildx create --name multiarch --driver docker-container

# use builder

docker buildx use multiarch

# inspect docker buildx

docker buildx inspect --bootstrap

# create repo on docker-hub

# build

docker buildx build \
--platform linux/amd64,linux/arm64/v8 \
-t alexwucpu05/conda-multiarch-test:latest \
--push \
.

docker buildx build --platform linux/amd64,linux/arm64/v8 -t alexwucpu05/conda-multiarch-test:latest --push .
