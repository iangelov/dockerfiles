all: help

help:
	@echo 'Options available:"'
	@echo '  make image VERSION=x.x.x'
	@echo '  make push  VERSION=x.x.x'

check-version:
ifndef VERSION
	@echo "Error: VERSION is undefined."
	@make --no-print-directory help
	@exit 1
endif

image: check-version
	sed -r -e "s/^ENV\s+MARATHON_VER.*$\/ENV MARATHON_VER $(VERSION)/g" Dockerfile.template > Dockerfile
	docker build -t iangelov/marathon:$(VERSION) .
	rm -f Dockerfile

push: check-version
	docker push iangelov/marathon:$(VERSION)
