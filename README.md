# OAI-5G-UERANSIM
Simulated UE and RAN connected to OAI 5GC
## For running the core services
```
sudo docker compose -f docker-compose-basic-vpp-nrf.yaml up -d

```
## For running virtual UE and RAN

```
sudo docker compose -f docker-compose-ueransim-vpp.yaml up -d
```
## Check if all the services are running 
```
sudo docker ps -a
```
## UERANSIM logs
```
sudo docker logs ueransim #you will get UE ip in the last line
```
## AMF logs
Here you can check if the gNg and UE are connected
```
sudo docker logs --follow oai-amf
```
## Ping test
* Here we ping UE from external DN container
```
sudo docker exec -it oai-ext-dn ping -c 3 <UE_IP>
```
* Here we ping external DN from UE (UERANSIM) container
```
sudo docker exec ueransim ping -c 3 -I uesimtun0 google.com
```
## Iperf test
Here we do iperf traffic test between UERANSIM UE and external DN node. We can make any node as iperf server/client.
Running iperf server on external DN container
```
docker exec -it oai-ext-dn iperf3 -s
docker exec -it ueransim iperf3 -c 192.168.73.135 -B 12.2.1.2
```
refrence:
https://gitlab.eurecom.fr/oai/cn5g/oai-cn5g-fed/-/blob/master/docs/DEPLOY_SA5G_WITH_UERANSIM.md
