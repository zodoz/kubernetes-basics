# Kubernetes Architecture
## and how to get stuff done

---

# Agenda
* Architecture
  * Nodes
  * Containers
  * Pods
  * Deployments/Replica Sets
  * Services
  * General terms
* GTD
  * kubectl
  * get vs describe
  * contexts and namespaces
  * basic service
  * public entry
  * admin entry
  * misc

---

# Architecture

---

# Nodes

---

# Containers

---

# Pods

---

# Deployments and Replica Sets

---

# Services

* ClusterIP - cluster-internal IP address
* NodePort - exposes a port on the node (physical server)
* LoadBalancer - expose to public via external IP address. Creates NodePort and ClusterIP automatically
* ExternalName - exposes a public DNS name (e.g. foo.spredfast.com) - we do not currently have access to this AFAIK

---

# Nodes

* Capacity
  * m = milli
  * K = thousand ≈ Ki
  * M = million ≈ Mi
  * G = billion ≈ Gi
  * T = trillion ≈ Ti
  * P = quadrillion ≈ Pi

CPU - 0.1 = 100m ([preferred](https://kubernetes.io/docs/concepts/configuration/manage-compute-resources-container/#meaning-of-cpu)) ~ one tenth of a CPU
RAM - 128M ≈ 128Mi = 128 megabytes of RAM

Never request any whole numbered capital letters of CPU!!!

---

# Terms

* kubelet - the process running on each node maintaining state
* etcd - only key/value store supported by Kubernetes - maintains state
* Image Registry - where all the docker images are stored and pulled from

---

# Review

* A pod is one or more containers
* A deployment is a definition of a replica set of pods
* A service is an entrypoint into a set of pods

---

# Sidecar patterns

* [storage](https://hub.docker.com/r/neshte/gluster-k8s-sidecar/) - may not be recommended
* [auto-sync git repository](https://github.com/kubernetes/git-sync)
* [service](https://medium.com/airbnb-engineering/smartstack-service-discovery-in-the-cloud-4b8a080de619) [discovery](http://relistan.com/sidecar-service-discovery-for-all-docker-environments/)
* [database](https://github.com/cvallance/mongo-k8s-sidecar)
* [service ambassador](https://docs.docker.com/engine/admin/ambassador_pattern_linking/)
* [logging](https://www.loggly.com/blog/how-to-implement-logging-in-docker-with-a-sidecar-approach/)
