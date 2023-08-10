### Redis Cluster

Burada basit bir 1 Main,  2Backup server olacak. Dolayisi ile 3 adet PV uretiyoruz. Bu servisler STS olarak calisacagi icin bunlari
local storage kullanacak sekilde calsitiriyorum, yani eger bir instance olurse tekrar ayaga kalktiginda hangi storage a baglanmasi gerektigini 
biliyor olacak. 

Servis headless bir service. 

Endpoints for the Redis instance are as 
#syntax
pod_name.service_name.namespace.svc.cluster.local

#Example
redis-0.redis.redis.svc.cluster.local
redis-1.redis.redis.svc.cluster.local
redis-2.redis.redis.svc.cluster.local

Redis-0 burada master node ve digerleri replica

Bu nodeler arasindaki replikasyon durumunu asagidaki komutlar ile gorebilirsin
* kubectl -n redis describe pod redis-0
* kubectl -n redis logs redis-0


REF:
https://www.airplane.dev/blog/deploy-redis-cluster-on-kubernetes