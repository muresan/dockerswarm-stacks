# dockerswarm-stacks
Testing deployments on docker swarm with compose files/stacks

## traefik.yml
Deploy traefik stack first as `lb` so the `lb_proxy` network is created and ready for services

```docker stack deploy -c traefik.yml lb```

## hello-world.yml
Next deploy the service stack that connects to traefik's network `lb_proxy` so the proxy can connect back

```docker stack deploy -c hello-world.yml hw```

## roach.yml
Stack that deploys a cockroachdb cluster 

```docker stack deploy -c roach.yml c```

## elasticsearch-sinle.yml
Stack that deploys an elasticsearch clsuter. Needs docker 17.09+ as that includes a fix so ES can start with a VIP.

```docker stack deploy -c elasticsearch-single.yml es```

## kafka-single.yml
Stack that deploys a ZooKeeper and Kafka pair with kafka-manager to provide visibility into Kafka

```docker stack deploy -c kafka-single.yml kafka```

