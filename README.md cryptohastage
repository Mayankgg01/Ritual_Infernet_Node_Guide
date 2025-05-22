<div align="center">

#  👨🏻‍💻 **Ritual Infernet Node Guide** 👨🏻‍💻

</div>


# -Device/System Requirements 💻

![image](https://github.com/user-attachments/assets/76006807-e83d-4c33-9d9d-8f7c95c8cdeb)


# Pre-Requirements 🛠

-Docker Desktop

-Evm wallet with minimum 5$ of BASE ETH

-Base Mainnet Rpc URL from ALCHEMY 

-Installations of Apt packages

```
sudo apt update && sudo apt upgrade -y
```

```
sudo apt -qy install curl git nano jq lz4 build-essential screen
```


# Install Docker & Docker Compose (vps)


```
sudo apt update && sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```
sudo apt update && sudo apt install -y docker-ce && sudo systemctl enable --now docker
```

```
sudo usermod -aG docker $USER && newgrp docker
```


```
sudo curl -L "https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | jq -r .tag_name)/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose
```


*  Verify installation

```
docker --version && docker-compose --version
```

# Allow Incoming connections on Ports (vps only)

```
sudo apt install ufw -y
sudo ufw allow 22
sudo ufw allow 3000
sudo ufw allow 4000
sudo ufw allow 6379
sudo ufw allow 8545
```

```
sudo ufw allow ssh
sudo ufw enable
```

# Cloning The Starter Repository

```
git clone https://github.com/ritual-net/infernet-container-starter
```

Navigate to the Repository

```
cd infernet-container-starter
```


# Running hello-world container

🔺before applying this command start the Docker in background (local pc)

* Pull

```
docker pull ritualnetwork/hello-world-infernet:latest
``` 

```
project=hello-world make deploy-container
```

![image](https://github.com/user-attachments/assets/82572d5f-86f9-4cca-aa85-164b8313c5ac)

* Open a New Terminal/termius Tab for further Process-

# Edit Node Configuration Files

* 1️⃣)- Will change config for this file - `~/infernet-container-starter/deploy/config.json` 

1.1) Run this command 

```
rm ~/infernet-container-starter/deploy/config.json && nano ~/infernet-container-starter/deploy/config.json
```

1.2) Paste this full code given below

1.3) Replace `ENTER_API_KEY` with your actual API key!

1.4) Replace `ENTER_YOUR_PVT_KEYS` with your actual EVM wallet PVT key.. add (0x) before the key!

1.5) `ctrl+x` , `Y` + `Enter` to save this!

```
{
    "log_path": "infernet_node.log",
    "server": {
        "port": 4000,
        "rate_limit": {
            "num_requests": 100,
            "period": 100
        }
    },
    "chain": {
        "enabled": true,
        "trail_head_blocks": 3,
        "rpc_url": "ENTER_API_KEY",
        "registry_address": "0x3B1554f346DFe5c482Bb4BA31b880c1C18412170",
        "wallet": {
          "max_gas_limit": 4000000,
          "private_key": "ENTER_YOUR_PVT_KEYS",
          "allowed_sim_errors": []
        },
        "snapshot_sync": {
          "sleep": 3,
          "batch_size": 500,
          "starting_sub_id": 240000,
          "sync_period": 30
        }
    },
    "startup_wait": 1.0,
    
    "redis": {
        "host": "redis",
        "port": 6379
    },
    "forward_stats": true,
    "containers": [
        {
            "id": "hello-world",
            "image": "ritualnetwork/hello-world-infernet:latest",
            "external": true,
            "port": "3000",
            "allowed_delegate_addresses": [],
            "allowed_addresses": [],
            "allowed_ips": [],
            "command": "--bind=0.0.0.0:3000 --workers=2",
            "env": {},
            "volumes": [],
            "accepted_payments": {},
            "generates_proofs": false
        }
    ]
}
```



* 2️⃣)- Will change config for this file - `~/infernet-container-starter/projects/hello-world/container/config.json` 

2.1) Run this command 

```
rm ~/infernet-container-starter/projects/hello-world/container/config.json && nano ~/infernet-container-starter/projects/hello-world/container/config.json
```

2.2) Paste this full code given below

2.3) Replace `ENTER_API_KEY` with your actual API key!

2.4) Replace `ENTER_YOUR_PVT_KEYS` with your actual EVM wallet PVT key.. add (0x) before the key!

2.5) `ctrl+x` , `Y` + `Enter` to save this!



```
{
    "log_path": "infernet_node.log",
    "server": {
        "port": 4000,
        "rate_limit": {
            "num_requests": 100,
            "period": 100
        }
    },
    "chain": {
        "enabled": true,
        "trail_head_blocks": 3,
        "rpc_url": "ENTER_API_KEY",
        "registry_address": "0x3B1554f346DFe5c482Bb4BA31b880c1C18412170",
        "wallet": {
          "max_gas_limit": 4000000,
          "private_key": "ENTER_YOUR_PVT_KEYS",
          "allowed_sim_errors": []
        },
        "snapshot_sync": {
          "sleep": 3,
          "batch_size": 500,
          "starting_sub_id": 240000,
          "sync_period": 30
        }
    },
    "startup_wait": 1.0,
   
    "redis": {
        "host": "redis",
        "port": 6379
    },
    "forward_stats": true,
    "containers": [
        {
            "id": "hello-world",
            "image": "ritualnetwork/hello-world-infernet:latest",
            "external": true,
            "port": "3000",
            "allowed_delegate_addresses": [],
            "allowed_addresses": [],
            "allowed_ips": [],
            "command": "--bind=0.0.0.0:3000 --workers=2",
            "env": {},
            "volumes": [],
            "accepted_payments": {},
            "generates_proofs": false
        }
    ]
}
```



* 3️⃣)- Will change config for this file - `~/infernet-container-starter/projects/hello-world/contracts/script/Deploy.s.sol` 

3.1) Run this command 

```
rm ~/infernet-container-starter/projects/hello-world/contracts/script/Deploy.s.sol && nano ~/infernet-container-starter/projects/hello-world/contracts/script/Deploy.s.sol
```

3.2) Paste this full code given below

3.3) `ctrl+x` , `Y` + `Enter` to save this!


```
// SPDX-License-Identifier: BSD-3-Clause-Clear
pragma solidity ^0.8.13;

import {Script, console2} from "forge-std/Script.sol";
import {SaysGM} from "../src/SaysGM.sol";

contract Deploy is Script {
    function run() public {
        // Setup wallet
        uint256 deployerPrivateKey = vm.envUint("PRIVATE_KEY");
        vm.startBroadcast(deployerPrivateKey);

        // Log address
        address deployerAddress = vm.addr(deployerPrivateKey);
        console2.log("Loaded deployer: ", deployerAddress);

        address registry = 0x3B1554f346DFe5c482Bb4BA31b880c1C18412170;
        // Create consumer
        SaysGM saysGm = new SaysGM(registry);
        console2.log("Deployed SaysHello: ", address(saysGm));

        // Execute
        vm.stopBroadcast();
        vm.broadcast();
    }
}
```




* 4️⃣)- Will edit Makefile - `~/infernet-container-starter/projects/hello-world/contracts/Makefile` 

4.1) Run this command 

```
rm ~/infernet-container-starter/projects/hello-world/contracts/Makefile && nano ~/infernet-container-starter/projects/hello-world/contracts/Makefile
```

4.2) Paste this full code given below

4.3) Replace `ENTER_YOUR_PVT_KEYS` with your actual EVM wallet PVT key.. add (0x) before the key!

4.4) Replace `ENTER_API_KEY` with your actual API key!

4.5) `ctrl+x` , `Y` + `Enter` to save this!


```
# phony targets are targets that don't actually create a file
.phony: deploy

# anvil's third default address
sender := ENTER_YOUR_PVT_KEYS
RPC_URL := ENTER_API_KEY

# deploying the contract
deploy:
	@PRIVATE_KEY=$(sender) forge script script/Deploy.s.sol:Deploy --broadcast --rpc-url $(RPC_URL)

# calling sayGM()
call-contract:
	@PRIVATE_KEY=$(sender) forge script script/CallContract.s.sol:CallContract --broadcast --rpc-url $(RPC_URL)
```



* 5️⃣)- Will change config for this file - `~/infernet-container-starter/deploy/docker-compose.yaml`



5.1) Run this command 

```
rm ~/infernet-container-starter/deploy/docker-compose.yaml && nano ~/infernet-container-starter/deploy/docker-compose.yaml
```

5.2) Paste this full code given below

5.3) `ctrl+x` , `Y` + `Enter` to save this!




```
services:
  node:
    image: ritualnetwork/infernet-node:1.4.0
    ports:
      - "0.0.0.0:4000:4000"
    volumes:
      - ./config.json:/app/config.json
      - node-logs:/logs
      - /var/run/docker.sock:/var/run/docker.sock
    tty: true
    networks:
      - network
    depends_on:
      - redis
      - infernet-anvil
    restart:
      on-failure
    extra_hosts:
      - "host.docker.internal:host-gateway"
    stop_grace_period: 1m
    container_name: infernet-node

  redis:
    image: redis:7.4.0
    ports:
    - "6379:6379"
    networks:
      - network
    volumes:
      - ./redis.conf:/usr/local/etc/redis/redis.conf
      - redis-data:/data
    restart:
      on-failure
    container_name: infernet-redis

  fluentbit:
    image: fluent/fluent-bit:3.1.4
    expose:
      - "24224"
    environment:
      - FLUENTBIT_CONFIG_PATH=/fluent-bit/etc/fluent-bit.conf
    volumes:
      - ./fluent-bit.conf:/fluent-bit/etc/fluent-bit.conf
      - /var/log:/var/log:ro
    networks:
      - network
    restart:
      on-failure
    container_name: infernet-fluentbit

  infernet-anvil:
    image: ritualnetwork/infernet-anvil:1.0.0
    command: --host 0.0.0.0 --port 3000 --load-state infernet_deployed.json -b 1
    ports:
      - "8545:3000"
    networks:
      - network
    container_name: infernet-anvil

networks:
  network:

volumes:
  node-logs:
  redis-data:
```




# Stop Docker Compose

```
cd $home
```

```
docker compose -f infernet-container-starter/deploy/docker-compose.yaml stop
```

# Installing Foundry 

```
curl -L https://foundry.paradigm.xyz | bash
```



```
echo 'export PATH="$HOME/.foundry/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```


```
foundryup
```



# Install the forge-std library and Install the infernet-sdk:



```
cd ~/infernet-container-starter/projects/hello-world/contracts && \
rm -rf lib/forge-std lib/infernet-sdk && \
forge install foundry-rs/forge-std && \
forge install ritual-net/infernet-sdk && \
ls lib/forge-std && \
ls lib/infernet-sdk
```



# Initialize Configuration by Start the Docker compose

```
cd $home
``` 

```
docker compose -f infernet-container-starter/deploy/docker-compose.yaml up -d
```

👉Verify that all 5 containers are running:

```
docker ps
```

![image](https://github.com/user-attachments/assets/887d4f3c-0f2b-491c-8572-06cfce78926a)



# Deploy Consumer Contract

* Deploy the SaysGM contract:

```
cd ~/infernet-container-starter
```

```
project=hello-world make deploy-contracts
```


🔺 Congo Contract Deploy Done✅ Save the Contract Address-

![image](https://github.com/user-attachments/assets/4cfa9d1c-3420-44df-944d-ac3ff6666a8f)


![image](https://github.com/user-attachments/assets/a2c3ea3d-5354-402b-b4de-576e5f396a1d)



# Call Contract

* Open-

```
  nano ~/infernet-container-starter/projects/hello-world/contracts/script/CallContract.s.sol
```

* Edit your SaysGM Contract with your actual one-

![image](https://github.com/user-attachments/assets/22bcea31-392c-41ef-811a-d8d094b31d5b)

* `ctrl+x` , `Y` + `Enter` to save


* Calling the SayGM Contract

```
project=hello-world make call-contract
```


Done✅ You could see some transactions there!

![image](https://github.com/user-attachments/assets/c6303c17-df13-40f3-a49f-fede0fdcf173)



🚀🚀**NOW, let the Node run on your VPS or Local Device..! It will Generate transactions on Base Mainnet!**


![image](https://github.com/user-attachments/assets/d8467d05-5cfa-4dc8-80a4-2c6599aba25a)






<div align="center">

#  ⚕️ **How to Start Next Day on Local PC?** ⚕️

</div>

```
docker compose -f infernet-container-starter/deploy/docker-compose.yaml down
```

```
docker compose -f infernet-container-starter/deploy/docker-compose.yaml up -d
```



<div align="center">

#  ⚕️ **How to delete Whole node Data** ⚕️

</div>

📣 * If u have did anything wrong then u can follow below command to delete all node Data and do it from scratch again:


```
cd $home
```

```
docker compose -f infernet-container-starter/deploy/docker-compose.yaml stop
```

* Delete Directory -:

```
sudo rm -rf infernet-container-starter
```

♦️📣Now u can follow From step - `Cloning The Starter Repository`




👉 Join TG for more Updates: https://telegram.me/cryptogg

If U have any issue then open a issue on this repo or Dm me on TG~

Thank U! 👨🏻‍💻 

Happy Coding💗

