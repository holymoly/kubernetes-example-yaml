# Setup
Deploy pihole on kubernetes. Quad9 will be used as DNS Servers.

1. Setup MetalLB as Loadbalancer, see onPremiseLoadbalancer example
2. User pihole.yaml to setup pihole on kubernetes
```
kubectl apply -f pihole.yaml
```
