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
docker logs ueransim
```
## Ping test
