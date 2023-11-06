## Prerequisite Software

- [Docker](https://docs.docker.com/engine/install/)

## Suggested Hardware Configuration

- Minimum 8GB RAM
- Minimum 500GB Storage (HDD acceptable, SSD recommended)
- 5mb/s+ Internet Download Speed

## Installation and Configuration Guidelines

### Docker Configuration for Non-Root Users (Optional)

If you intend to operate Docker as a root user, you may bypass this section. For non-root user operations, ensure to include your user in the `docker` user group by executing the following command:

```
sudo usermod -a -G docker `whoami`
```

Following this modification, a re-login is necessary for the changes to become effective.

### Oracle Operation Procedure

1. Oracle Approval: Please reach out to Mantle LSP Team.
2. Ethereum Account Funding: Deposit at least 1 Ether into your oracle's EOA.
3. Beacon API Configuration: Obtain a Beacon API URL and update the `BEACON_NODE_URL` field in the configuration file.

   - Example Provider: Ankr [Beacon API](<https://rpc.ankr.com/premium-http/eth_beacon/$(BEACON_API_AUTH_TOKEN_ANKER)>) (https://rpc.ankr.com/premium-http/eth_beacon/$(BEACON_API_AUTH_TOKEN_ANKER))

4. Docker Compose File Adjustment: Modify the `docker-compose.yml` file with the relevant details:

   - `SERVICE_PRIVATE_KEY`: Private key of oracle EOA (without "0x" prefix)
   - `RPC_URL`: Mainnet RPC URL
   - `BEACON_NODE_URL`: Beacon API URL

5. Oracle Initialization:

```
docker-compose -f docker-compose.yml up -d
```

> The command initializes the node in a detached mode (`-d`), allowing continuous operation in the background. Re-execute this command following any system shutdown.

1.  Oracle Termination:

```
docker-compose -f docker-compose.yml down
```

> This command halts the node operation without erasing any volumes. You can securely execute this command and re-initiate the node later.

1.  Log Monitoring:

```
docker-compose logs <service name>
```

> Access the logs for a specified service. Employ the `-f` flag to monitor logs for a service in real-time.
