### Description Kubeplugin

This plugin show the CPU and RAM usage of each resource in the cluster. 
> NOTE: The plugin is based on the `kubectl top` command.

### Prerequisites:
- kubectl command line interface  [doc](https://kubernetes.io/docs/tasks/tools/)
- your cluster has metrics-server [doc](https://github.com/kubernetes-sigs/metrics-server/#installation)

### Installation kubeplugin:

General documentaion how to install, use plugins [doc](https://kubernetes.io/docs/tasks/extend-kubectl/kubectl-plugins/)

- Clone repo and copy `kubeplugin` to your _$PATH_ like: `/usr/local/bin/kubectl-kubeplugin` as name of **kubectl-kubeplugin**
- Add executable permission to `kubeplugin` as `sudo chmod +x /usr/local/bin/kubectl-kubeplugin`
- Check plugin with `kubectl plugin list` you should see `kubectl-kubeplugin` in the list

### Usage kubeplugin:

For getting the CPU and RAM usage of each resource in the cluster you can use `kubectl kubeplugin` command with arguments `resource-type` and `namespace`

**Example:**

```bash
➜ kubectl kubeplugin pod kube-system
R-TYPE  NS           NAME                                    CPU  MEM
pod     kube-system  coredns-77ccd57875-24xbq                5m   23Mi
pod     kube-system  local-path-provisioner-957fdf8bc-m276z  1m   13Mi
pod     kube-system  metrics-server-648b5df564-578mp         11m  30Mi
pod     kube-system  svclb-traefik-7afa9488-c9nmg            0m   0Mi
pod     kube-system  traefik-64f55bb67d-xnpwb                5m   40Mi

...

➜ kubectl kubeplugin node kube-system
R-TYPE  NS           NAME               CPU   MEM
node    kube-system  k3d-argo-server-0  222m  2%

```

