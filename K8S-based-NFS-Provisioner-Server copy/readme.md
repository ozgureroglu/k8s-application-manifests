## Bir hostpathi sunan bir nfs-provisioner kurar

PhyVol --->  /hostpath ---> Provisioner <--- NFS PV <--- NFS PVC <--- POD

https://github.com/kubernetes-sigs/nfs-ganesha-server-and-external-provisioner/tree/master/deploy/kubernetes

Kubernetes worker nodelarindan birisine bagli olarak calisacak olan bir NFS server bu. 
Once bir node u label atarak sabitlememmiz gerekiyor.
Bunu node terminalinden hostname komutu ile alip values,yml dosyaindaki hostname alanina ekle.
Burada NFS sunucusu Kubernetes uzerinde calisiyor.

```
helm install nfs-server stable/nfs-server-provisioner --values ./nfs-values.yaml
```

```
helm uninstall nfs-server
```

Volume Mount error alirsan tum nodelarda: 
apt-get install nfs-common -y