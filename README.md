# dockerswarm-stacks
Testing deployments on docker swarm with compose files/stacks

## traefik.yml
Deploy traefik stack first as `lb` so the `lb_proxy` network is created and ready for services
```docker stack deploy -c traefik lb```

## hello-world.yml
Next deploy the service stack that connects to traefik's network `lb_proxy` so the proxy can connect back
```docker stack deploy -c hello-world.yml hw```

