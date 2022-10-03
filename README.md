## Deploying Bob

This gathers reference deployments for [Bob](https://bob-cd.github.io/) on various platforms. The cluster is configured as follows with a single replica setup of:
- [PostgreSQL](https://www.postgresql.org/)
- [RabbitMQ](https://www.rabbitmq.com/)
- [apiserver](https://github.com/bob-cd/bob/tree/main/apiserver)
- [entities](https://github.com/bob-cd/bob/tree/main/entities)
- [runner](https://github.com/bob-cd/bob/tree/main/runner)
- [resource-git](https://github.com/bob-cd/resource-git)
- [artifact-store](https://github.com/bob-cd/artifact-local)

**Note: There are no resource limits configured and all defaults used. This is intended to be a reference for actual deployments.**

### [Kubernetes](https://kubernetes.io/)

#### Requirements
- Kubernetes 1.20+
- [kubectl](https://kubernetes.io/docs/reference/kubectl/overview/)

#### Deploying

From the root of the dir:
- Run `kubectl apply -f k8s/` to create all the necessary services.
- Run `kubectl port-forward service/bob-apiserver 7777:7777` to forward the `7777` port on the local machine and should be available on it.
- To clean up, run:
  - `kubectl delete -f k8s/`
  - `kubectl delete pvc --all`

### [Docker](https://www.docker.com/) or [Podman](https://podman.io/)

#### Requirements
- [Docker](https://docs.docker.com/get-docker/) 20+ or [Podman](https://podman.io/getting-started/installation) 4+
- [docker compose](https://docs.docker.com/compose/install/#install-compose) or [podman-compose](https://github.com/containers/podman-compose)

#### Deploying

Using podman is recommended here as it can do truly **rootless containers in addition to being unprivileged**.
- Run `podman-compose up` or `docker-compose up` if using docker to create all the necessary services.
- The service should be available on port `7777`.

## License

Copyright © 2022 Bob authors.

Distributed under the MIT License. See LICENSE.
