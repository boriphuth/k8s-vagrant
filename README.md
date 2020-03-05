# k8s-vagrant
```bash
cd k8s_centos\vagrant-provisioning>
vagrant up
vagrant status
vagrant ssh kmaster
[vagrant@kmaster ~]$ kubectl get nodes
```
# Administer the Kubernetes Cluster from your host
```bash
#Create the configuration directory
$ mkdir -p ~/.kube
#Find the SSH port of the kmaster server
$ vagrant port kmaster
#Copy the file using scp (ssh password is vagrant)
$ scp -P 2222 vagrant@127.0.0.1:/home/vagrant/.kube/config ~/.kube/config
password: vagrant

$ kubectl cluster-info
$ kubectl get pods --all-namespaces
```

# Kubernetes Dashboard
```bash
$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-rc5/aio/deploy/recommended.yaml
# Create An Authentication Token (RBAC)
$ kubectl apply -f k8s_centos/dashboard/kubernetes-dashboard-service-np.yaml

# Bearer Token
# For Bash:
$ kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')

# For Powershell:
$ kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | sls admin-user | ForEach-Object { $_ -Split '\s+' } | Select -First 1)
```
Access the Kubernetes Dashboard using the URL https://172.42.42.100:30002/#/login

## Issue Vagrant up - VBoxManage.exe error: VT-x is not available (VERR_VMX_NO_VMX) code E_FAIL (0x80004005) gui headless
```bash
https://stackoverflow.com/questions/37955942/vagrant-up-vboxmanage-exe-error-vt-x-is-not-available-verr-vmx-no-vmx-code
```

To turn Hypervisor off, run this from Command Prompt (Admin) (Windows+X):
```bash
bcdedit /set hypervisorlaunchtype off

and reboot your computer. To turn it back on again, run:

bcdedit /set hypervisorlaunchtype on
If you receive "The integer data is not valid as specified", try:

bcdedit /set hypervisorlaunchtype auto
```
