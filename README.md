# API Service (Go)

Basic development setup for this project using VS Code, Dev Containers, and Docker Compose.

## Prerequisites

- Docker + Docker Compose
- VS Code
- VS Code extension: `Dev Containers` (`ms-vscode-remote.remote-containers`)

## Quick Start (VS Code)

1. Open this folder in VS Code.
2. Run Command Palette: `Dev Containers: Reopen in Container`.
3. Wait for the container to build and start.
4. Open a terminal in VS Code (it defaults to `zsh` in the container).
5. Run:

```bash
make test
```

Inside the container, commands like `make test`, `make build`, `make fmt`, and `make vet` are expected to work directly.

## Starting Environment From Host

If you prefer using host-side commands first:

```bash
make setup
```

Then either:

- Attach with VS Code Dev Containers, or
- Enter the container shell manually:

```bash
make docker-shell
```

Stop services:

```bash
make down
```

Destroy services, volumes, and images:

```bash
make teardown
```

## Make Targets

Host (outside container):

- `make setup` - start dev environment
- `make down` - stop dev environment
- `make teardown` - remove dev environment
- `make docker-setup` - start app container
- `make docker-down` - stop containers
- `make docker-destroy` - remove containers, images, and volumes
- `make docker-shell` - open shell in app container
- `make docker-test` - run tests in container
- `make docker-build` - build in container
- `make docker-fmt` - format in container
- `make docker-vet` - vet in container
- `make docker-install-deps` - download dependencies in container
- `make docker-swagger-gen` - run swagger generation in container

Container (inside dev container):

- `make test`
- `make build`
- `make fmt`
- `make vet`
- `make install-deps`
- `make run-api` (live reload via `air`)

Show all commands:

```bash
make help
```

## Go Modules (`go.mod`)

If this repository does not have a `go.mod` yet, initialize it from project root:

```bash
go mod init github.com/<your-org-or-user>/<repo-name>
go mod tidy
```

Then download dependencies:

```bash
make install-deps
```

## Notes

- The container sets `INSIDE_DEV_CONTAINER=true`, and some `make` targets enforce this.
- Port `8080` is forwarded by Docker Compose and Dev Container settings.
