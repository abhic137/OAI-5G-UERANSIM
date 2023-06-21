# OAI-5G-UERANSIM
Simulated UE and RAN connected to OAI 5GC
## For running the core services
```
sudo docker-compose -f docker-compose-basic-vpp-nrf.yaml up -d

```
## For running virtual UE and RAN

```
sudo docker-compose -f docker-compose-ueransim-vpp.yaml up -d
```
## Check if all the services are running 
```
sudo docker ps -a
```
## UERANSIM logs
```
docker logs ueransim #you will get UE ip in the last line
```
## Ping test
*Here we ping UE from external DN container
```
sudo docker exec -it oai-ext-dn ping -c 3 <UE_IP>
```
*Here we ping external DN from UE (UERANSIM) container
```
sudo docker exec ueransim ping -c 3 -I uesimtun0 google.com
```
