Study with me series: Kubernetes

Architecture:

  Control plane: 
    Is a collectin of multiple components responsible for managing the cluster itself. They run on controller machines.
        kube-api-server: Controls the Kubernetes API
             can be loadbalanced
        Etcd: Is the data store for the state of the cluster.
            stacked means replicated for HA

            Can also have an external etcd, running on external nodes in HA themselves.
            
        kube-scheduler: Selects the node to run pods.
        kube-controller-manager: Run multiple utilities.
        cloud-controller-manager: Interface between k8s and cloud platforms.

Worker Nodes:
    The power. Use a container runtime like docker
      kubelet: Agent 
    
Namespaces: A mechanism for isolating groups of resources within a single cluster.
      default: What the same means
       kube-system: 

        kube-ctl get pods --all-namespaces: find a pod in all namespaces

         kubectl create namespaces: creates a namespaces


Management tools:
      kubectl: is the official command line interface
      kubeadm: tool that allows to create clusters
      minikube: similar to kubeadm, for single-node 
      helm: package management creates charts (templates)
      kompose: translate docker compose files to kubernetes objects
      kustomize: configuration management tool. 
