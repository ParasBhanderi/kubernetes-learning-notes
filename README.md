# Kubernetes learning notes

A practical notebook for learning Kubernetes concepts, testing them, and recording what worked.

## How I will use this repo

1. Pick a topic from the roadmap below.
2. Explain it in my own words.
3. Run a small lab and record the commands, observations, and cleanup steps.
4. Add the result and next question to the learning log.

Do not commit kubeconfig files, tokens, passwords, or other secrets.

## Repository layout

- **notes/** groups dated learning notes by subject.
- **examples/** groups runnable manifests by topic.

## Roadmap

- [ ] **Foundations:** clusters, control plane, nodes, API objects, namespaces, and kubectl.
- [ ] **Workloads:** Pods, Deployments, ReplicaSets, Jobs, CronJobs, and rollouts.
- [ ] **Networking:** Services, DNS, Ingress or Gateway, and network policies.
- [ ] **Configuration and storage:** ConfigMaps, Secrets, volumes, and persistent storage.
- [ ] **Operations:** requests and limits, probes, autoscaling, scheduling, RBAC, and troubleshooting.
- [ ] **Production design:** availability, upgrades, security, backups, and deployment practices.

## Topic note template

For each topic, capture:

- **In my own words:** what the concept does and when to use it.
- **Key ideas:** the terms and relationships I need to explain.
- **Hands-on lab:** goal, environment, steps or manifests, expected result, and actual result.
- **Troubleshooting and cleanup:** what failed, how I diagnosed it, and what I removed.
- **Architecture implications:** trade-offs, security concerns, and operational needs.
- **Sources and follow-up questions.**

## Learning log

| Date | Topic | What I tried | Result | Next step |
| --- | --- | --- | --- | --- |
| 2026-10-11 | [ClusterIP, NodePort, and LoadBalancer](notes/networking/2026-10-11-services.md) | Studied Service types and YAML | Note and examples added; live lab pending | Apply and test the manifests |

