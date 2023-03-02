.PHONY: images run

images: ./*-exec ./*-shell
	for d in $^; do \
	  docker build -t docker-scratch-$$d:latest -f $$d/Dockerfile $$d; \
	done

run: ./*-exec ./*-shell
	for d in $^; do \
	  echo "Running docker-scratch-$$d:latest"; \
	  docker run "docker-scratch-$$d:latest"; \
	done
