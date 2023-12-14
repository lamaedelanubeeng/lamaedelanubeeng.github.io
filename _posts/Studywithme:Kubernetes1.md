Study with me series: Kubernetes

Architecture:

Definitions:
  Control plane: 
    Is a collectin of multiple components responsible for managing the cluster itself. They run on controller machines.
        kube-api-server: Controls the Kubernetes API
        Etcd: Is the data store for the state of the cluster. 
        kube-scheduler: Selects the node to run pods.
        kube-controller-manager: Run multiple utilities.
        cloud-controller-manager: Interface between k8s and cloud platforms.

      
    
