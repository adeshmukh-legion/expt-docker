.PHONY: images run

images: ./*-exec ./*-shell
	for d in $^; do \
	  docker build -t $$d:latest -f $$d/Dockerfile $$d; \
	done

run: override-cmd override-entrypoint-cmd

override-cmd: ./*-shell ./*-exec
	@echo "🔹 Override CMD"
	@for d in $^; do \
	  echo ""; \
	  echo "▸ Running: docker run $$d:latest echo More or less"; \
	  egrep "^(CMD|ENTRYPOINT)" $$d/Dockerfile | sed 's:^:  +  :'; \
	  docker run "$$d:latest" echo More or less; \
	done
	@echo ""

override-entrypoint-cmd: ./*-shell ./*-exec
	@echo "🔹 Override ENTRYPOINT and CMD"
	@for d in $^; do \
	  echo ""; \
	  echo "▸ Running: docker run $$d:latest --entrypoint time echo More or less"; \
	  egrep "^(CMD|ENTRYPOINT)" $$d/Dockerfile | sed 's:^:  +  :'; \
	  docker run  --entrypoint time "$$d:latest" echo More or less; \
	done
	@echo ""
