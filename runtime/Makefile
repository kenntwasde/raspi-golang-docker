NAME = kenntwasde/raspi-golang-runtime
#DEBIAN_VER = jessie
DEBIAN_VER = wheezy
GO_VER = 1.4
ARCH=$(shell uname -m)
BUILDVER = $(shell cat ../buildversion)
MAINVER = $(GO_VER)-linux-$(ARCH)
VERSION = $(MAINVER)-$(BUILDVER)

.PHONY: all build tag_latest release

all: build

build:
	docker build --rm --no-cache  -t "$(NAME):$(VERSION)" .


tag_latest:
	docker tag -f $(NAME):$(VERSION) $(NAME):$(MAINVER)
	docker tag -f $(NAME):$(VERSION) $(NAME):latest

release: tag_latest
	@if ! docker images $(NAME) | awk '{ print $$2 }' | grep -q -F $(VERSION); then echo "$(NAME) version $(VERSION) is not yet built. Please run 'make build'"; false; fi
	@if ! head -n 1 ../Changelog.md | grep -q 'release date'; then echo 'Please note the release date in ../Changelog.md.' && false; fi
	docker push $(NAME)
	@echo "*** Don't forget to create a tag. git tag $(VERSION) && git push origin $(VERSION)"
