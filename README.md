# k8s-vagrant
```bash
cd k8s_centos\vagrant-provisioning>
vagrant up
vagrant status
vagrant ssh kmaster
[vagrant@kmaster ~]$ kubectl get nodes
```
```bash
kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | sls admin-user | ForEach-Object { $_ -Split '\s+' } | Select -First 1)
```

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
