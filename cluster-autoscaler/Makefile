IMAGE_NAME := baseten/cluster-autoscaler
GIT_SHA := $(shell git rev-parse HEAD)

DOCKER_BUILD_PUSH_CMD := docker buildx build --platform linux/amd64 -t $(IMAGE_NAME):$(GIT_SHA) . --push

.PHONY: tidy
tidy:
	go fmt ./...
	go mod tidy -v

.PHONY: docker-build
docker-build:
	$(DOCKER_BUILD_PUSH_CMD)