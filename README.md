# Simple Mantle LSP Oracle Node

## Required Software

- [docker](https://docs.docker.com/engine/install/)

## Recommended Hardware

- 8GB+ RAM
- 500GB+ disk (HDD works for now, SSD is better)
- 5mb/s+ download


## Installation and Setup Instructions

### Configure Docker as a Non-Root User (Optional)

If you're planning to run Docker as a root user, you can safely skip this step.
However, if you're using Docker as a non-root user, you'll need to add yourself to the `docker` user group:

```sh
sudo usermod -a -G docker `whoami`
```

You'll need to log out and log in again for this change to take effect.


### run oracle

####  Sending your EOA address of oralce to mantle to get approve to run a oralce 

jeremy.zhang@mantle.xyz



####  Get some eth into your oracle EOA
1 should be enough


####  Get a beacon api url and replace in the config file  : BEACON_NODE_URL

example: ankr
https://rpc.ankr.com/premium-http/eth_beacon/$(BEACON_API_AUTH_TOKEN_ANKER)



#### changing the docker-compose.yml file accordingly 
SERVICE_PRIVATE_KEY : private key of oracle EOA (with eth) ,without "0x"

RPC_URL: rpc of mainnet

BEACON_NODE_URL : beacon api url


#### start oralce

```sh
docker-compose -f docker-compose.yml up -d 
```

Will start the node in a detatched shell (`-d`), meaning the node will continue to run in the background.
You will need to run this again if you ever turn your machine off.


#### Stop

```sh
docker-compose -f docker-compose.yml down
```

Will shut down the node without wiping any volumes.
You can safely run this command and then restart the node again.

#### Logs

```sh
docker-compose logs <service name>
```

Will display the logs for a given service.
You can also follow along with the logs for a service in real time by adding the flag `-f`.


