# Run stress test tool on docker


``` make up ``` to deploy the container

``` make down ``` to destroy


### docker-compose.yml

```
version: '3'

services:
  stress:
    image: progrium/stress
    container_name: stresser
    command: --cpu 8 --io 1 --vm 2 --vm-bytes 8196M --vm-hang 0
    deploy:
        # mode: replicated
        # replicas: 1
        # placement:
          # max_replicas_per_node: 1
          # constraints:
            # - node.role == worker
            # - node.role == manager
        resources:
          limits:
            cpus: "8"
            memory: 16g
          reservations:
            cpus: "8"
            memory: 16g
```

you can run the test on your swarm nodes to do so  uncomment and adjust for your needs