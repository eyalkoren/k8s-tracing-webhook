# Makefile for building the Admission Controller webhook server + docker image.

.DEFAULT_GOAL := docker-image

IMAGE ?= eyalkoren/tracing-webhook:latest

webhook: $(shell find .. -name '*.go')
	CGO_ENABLED=0 GOOS=linux go build -ldflags="-s -w" -o $@ ../webhook

.PHONY: docker-image
docker-image: webhook
	docker build -t $(IMAGE) .

.PHONY: push-image
push-image: docker-image
	docker push $(IMAGE)
