# Setup
1. Install MetalLB
```console
kubectl apply -f https://raw.githubusercontent.com/google/metallb/v0.8.1/manifests/metallb.yaml
```
2. Configure MetalLB using the loadbalancer.yaml
```console
kubectl apply -f loadbalancer.yaml
```

3. Define a service and define the ip(example rabbitmq service)
```yaml
---
kind: Service
apiVersion: v1
metadata:
  namespace: rabbitmq
  name: rabbitmq
  labels:
    app: rabbitmq
    type: LoadBalancer
spec:
  type: LoadBalancer
  loadBalancerIP: 10.10.10.10
  ports:
  - name: mqtt
    protocol: TCP
    port: 1883
    targetPort: 1883
  - name: http
    protocol: TCP
    port: 15672
    targetPort: 15672
  - name: amqp
    protocol: TCP
    port: 5672
    targetPort: 5672
  selector:
    app: rabbitmq
```
