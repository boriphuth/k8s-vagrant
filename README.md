# k8s-vagrant
```bash
cd k8s_centos\vagrant-provisioning>
vagrant up
vagrant status
vagrant ssh kmaster
[vagrant@kmaster ~]$ kubectl get nodes
```
kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | sls admin-user | ForEach-Object { $_ -Split '\s+' } | Select -First 1)

eyJhbGciOiJSUzI1NiIsImtpZCI6IkpOandXaFI4VW9LYzJFMnZSVnBzbTVwTjQxbmRrWWVDeEdpRHdOZWxFS3cifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJrdWJlcm5ldGVzLWRhc2hib2FyZCIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VjcmV0Lm5hbWUiOiJhZG1pbi11c2VyLXRva2VuLTIycGtjIiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZXJ2aWNlLWFjY291bnQubmFtZSI6ImFkbWluLXVzZXIiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC51aWQiOiJmNzA1MThiYy1kMjg2LTQwMWUtYmQ3Ny0yM2Q5NGYwZDZiY2YiLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6a3ViZXJuZXRlcy1kYXNoYm9hcmQ6YWRtaW4tdXNlciJ9.dcfJSwacinui99PajEnlLk6wrW4lMhtzyyB4xpQdi36ZK1shp1B21eCHsAVd7pDeUX3KQZA19H1s53Lz46uXLyxCHSlHGeWlbQHWkzgsN05vnv-EqchZwSAtONGaw4n_pFloHrSVoXGd6y1gtewEQUXtfEmelO__Q1wg3PkAdOLw2r-jhd4tKTNYyiwXqgB2vJdmwnGrCfDbqHRPro6UtuJK21F3BoPJZbDNerCKkRy0JFErLIk9ge8x_N4kmBz9_SPaKmmVYm1FbmVe-CgNkolBqcregh3MQ6bmOdK_dbj5NODM9u__iDTZvIHRdWXM1zqIIdXX62JLrS-Z1K9-8g

## Issue Vagrant up - VBoxManage.exe error: VT-x is not available (VERR_VMX_NO_VMX) code E_FAIL (0x80004005) gui headless
## https://stackoverflow.com/questions/37955942/vagrant-up-vboxmanage-exe-error-vt-x-is-not-available-verr-vmx-no-vmx-code
To turn Hypervisor off, run this from Command Prompt (Admin) (Windows+X):
bcdedit /set hypervisorlaunchtype off
and reboot your computer. To turn it back on again, run:

bcdedit /set hypervisorlaunchtype on
If you receive "The integer data is not valid as specified", try:

bcdedit /set hypervisorlaunchtype auto