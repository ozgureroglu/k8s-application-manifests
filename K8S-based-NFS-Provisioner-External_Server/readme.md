## Bir hostpathi sunan bir nfs-provisioner kurar

PhyVol --->  /hostpath ---> Provisioner <--- NFS PV <--- NFS PVC <--- POD


https://github.com/kubernetes-sigs/nfs-subdir-external-provisioner

Halihazirda kurulu olan bir NFS sunucusunu kullanarak provision yapan provisioner/
Onceden kurulmus bir NFS Server gerekiyor. Docker server projesi icindeki NFS-Server kullanilabilir. 



```
helm install nfs-subdir-external-provisioner nfs-subdir-external-provisioner/nfs-subdir-external-provisioner \
    --set nfs.server=10.10.10.10:2049 \
    --set nfs.path=/data
```


asagidaki yontemi kullanmadan once values.yaml edit edilmelidir. 
```
helm install nfs-server stable/nfs-server-provisioner --values ./nfs-values.yaml
```

```
helm uninstall nfs-server
```

Volume Mount error alirsan tum nodelarda: 
apt-get install nfs-common -y