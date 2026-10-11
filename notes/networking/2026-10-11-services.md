# Kubernetes Services: ClusterIP, NodePort, and LoadBalancer

**Date:** 2026-10-11  
**Study record:** I learned these three Service types and how to create Service YAML files. The screenshot shows lessons titled Services, Services Cluster IP, and Services - Loadbalancer. The examples below are study examples; a live cluster test has not been recorded yet.

## In my own words

A Service gives a group of Pods a stable network endpoint. Its selector matches Pod labels. The Service type determines how clients can reach it.

| Type | Reachability | Typical use |
| --- | --- | --- |
| ClusterIP | Inside the cluster | Communication between workloads |
| NodePort | A port on each node, plus a ClusterIP | Direct access through a node |
| LoadBalancer | External load balancer, when supported | Exposing an application outside the cluster |

ClusterIP is the default type. NodePort also creates a ClusterIP. LoadBalancer needs a cloud provider or another load balancer implementation; an external address may stay pending without one.

## Important YAML fields

- `apiVersion: v1` and `kind: Service` identify the resource.
- `metadata.name` names the Service.
- `spec.type` selects the exposure method.
- `spec.selector` must match the target Pods' labels.
- `port` is the Service port; `targetPort` is the Pod port.
- `nodePort` is optional for NodePort; Kubernetes can assign it.

These examples assume Pods labeled `app: demo` that listen on TCP port 8080. Replace the selector and ports for a real workload.

### ClusterIP: service-clusterip.yaml

    apiVersion: v1
    kind: Service
    metadata:
      name: demo-clusterip
    spec:
      type: ClusterIP
      selector:
        app: demo
      ports:
        - protocol: TCP
          port: 80
          targetPort: 8080

### NodePort: service-nodeport.yaml

    apiVersion: v1
    kind: Service
    metadata:
      name: demo-nodeport
    spec:
      type: NodePort
      selector:
        app: demo
      ports:
        - protocol: TCP
          port: 80
          targetPort: 8080
          # nodePort: 30080  # Optional; must be free and in the configured range.

### LoadBalancer: service-loadbalancer.yaml

    apiVersion: v1
    kind: Service
    metadata:
      name: demo-loadbalancer
    spec:
      type: LoadBalancer
      selector:
        app: demo
      ports:
        - protocol: TCP
          port: 80
          targetPort: 8080

## Next hands-on check

1. Create a test workload labeled `app: demo` that listens on port 8080.
2. Save and apply each manifest with `kubectl apply -f <filename>`.
3. Inspect the Services with `kubectl get services` and `kubectl describe service <name>`.
4. Test connectivity, record the result, and delete the test resources.

**Question to revisit:** Which type should be used when an application must only be reachable inside the cluster?

## Source

- [Kubernetes Service documentation](https://kubernetes.io/docs/concepts/services-networking/service/)

