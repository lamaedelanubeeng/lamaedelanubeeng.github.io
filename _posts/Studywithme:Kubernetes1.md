<h1> Study with me series: Kubernetes</h1>

<h2>Architecture:</h2>

  <b>Control plane:</b>
    Is a collection of multiple components responsible for managing the cluster itself. They run on controller machines.
     
   * kube-api-server: Controls the Kubernetes API
          can be loadbalanced
   * Etcd: Is the data store for the state of the cluster. Every configuration is here
          Types of HA:
          Stacked: Same management nodes, replicated Etcs
          External: running on external nodes in HA themselves.
            
   * kube-scheduler: Selects the node to run pods.
   * kube-controller-manager: Run multiple utilities.
   * cloud-controller-manager: Interface between k8s and cloud platforms.

 <b>Worker Nodes: </b>
     The power. Use a container runtime like docker
     * kubelet: Agent 
    

<b>Namespaces: </b>
A mechanism for isolating groups of resources within a single cluster.
    default: 
    kube-system: Support services

        kube-ctl get pods --all-namespaces: # find a pod in all namespaces

        kubectl create namespaces: # creates a namespaces


Management tools:
* kubectl: is the official command line interface
* kubeadm: tool that allows to create clusters
* minikube: similar to kubeadm, for single-node 
* helm: package management creates charts (templates)
* kompose: translate docker compose files to kubernetes objects
* kustomize: configuration management tool.


<b>Draining:</b>
  Taking a node of off service without impacting applications. (maintenance mode). Graceful terminates containers.
  
      kubectl drain <node> --ignore-daemonsets  ##This flag means to ignore the pods specific for the node, like the vcls

<b>Uncordoning a node: </b>
 Taking out of maintenance mode

      kubectl uncordon <node>


<b>Upgrading control plane node: </b>
  1. Upgrade kubeadm on control node
  2. Drain the control node
  3. Plan the upgrade (kubeadm upgrade plan)
  4. Apply the upgrade (kubeadm upgrade apply)
  5. Uncordon

<b>Upgrading worker nodes </b>
  1. Drain
  2. upgrade kubeadm
  3. upgrade kubelet configuration (kubeadm upgrade node)
  4. upgrade kubelet and kubectl
  5. uncordon

<b>Backing up and restoring</b>
    etcdctl snapshot save

<b>Restoring </b>
     etcdctl snapshot restore <filename>

    
<b>Kubectl</b>
    get: list objects
       - o Set output format
       --sort-by 
       --selector 

    describe: get detailed information about an objecy

    create: that
      -f   from a yaml file

    apply: same than create, it will modify an object that exists with the same name. Create will give an error

    exec: run a command inside a container 

        kubectl exec <pod name> -c <container name> -- <command>


   Imperative commands
      Define objects using commands and flags

          --dry-run  will run a command in simulation mode

          kubectl create deployment my-deployment --image=nginx -=dry-run -o yaml

          
   Declarative commands 
     Define objects using datastructores like yaml



<b>RBAC in Kubernetes </b>
    Role:
      Defines permissions in a namespace
      
    ClusterRoles:
      Cluster wide permission 

    RoleBinding:
      Attach users to roles
    RoleBindings:
      Attach roles to cluster roles

  You create roles with YAML

        apiVersion: rbac.authorization.k8s.io/v1
        kind: Role

        metadata
            namespace: default
            name: pod-reader
        rules:
        - apiGroups: [""]
          resources: ["pods", [pods/logs]]
          verbs: ["get", "watch","list"]


    Rolebinding:
       apiVersion: rbac.authorization.k8s.io/v1
       kind: RoleBinding
       metadata:
         name: pod-reader
         namespace: default
       subjects:
       - kind: user
         name: dev
         apiGroup: rbac.authorization.k8s.io
       roleRef:
         kind: Role
         name: pod-reader
         apiGroup: rbac.authorization.k8s.io


Creating Service accounts
Account used by Pods to access the Kubernetes API

     created with YAML
       apiVersion: v1
       kind: ServiceAccount
       metadata:
         name: my-serviceaccount


      or, create with command:
      kubectl create sa <name> -n <namespace>
    and then binding 

Inspecting resource usage 

Kubernetes metric server
  needs to be installed 
  kubectl apply -f <>

  then
  kubectl top pod --sort-by <> selector

  kubectl top node 

  kubecetl top node --sort-by cpu


</h3>Kubernetes network model</h3>

Defines how pods communicated between them, pods get an IP.

<b>CNI plugings</b>
Plugins that implement the network model
Calico is one really extended

Nodes will remain in NotReady status if there is not network plugin

<b>DNS</b>
Runs as a service in a pod, normally in the kube-system namespace
CoreDNS for example

