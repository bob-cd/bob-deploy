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
- The service should be available on port `7777`.
- To clean up, run:
  - `kubectl delete -f k8s/`
  - `kubectl delete pvc --all`

## License

Copyright © 2021 Bob authors.

Distributed under the MIT License. See LICENSE.
