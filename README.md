# Aztec-Network
<img width="900" height="511" alt="image" src="https://github.com/user-attachments/assets/5e7c9285-172e-4501-8172-e3ea9e625d4b" />

# Aztec Network Sequencer Node
Learn to run an `Aztec sequencer node` in simple, baby steps.

  * `Sequencer`: sequencer node on Aztec is the one that orders transactions, builds blocks, and helps secure the network.

## Roles Info
You can earn the Guardian role by running an Aztec sequencer node. 

A random weekly snapshot decides who qualifies, and the team announces it in #apprentice-announcements once it’s done.

---

## Hardware Requirements
- CPU: 4+ Cores
- RAM: 16GB+ 
- Storage: 500GB+ SSD/NVMe
- Network Speed: 20+ Mbps

---

**VPS Users**: can get started via a `VPS` with 4 cores CPU, 16GB RAM! [Contabo](https://contabo.com/en/)

---

## 1. Install Dependecies
* Update packages:
```bash
sudo apt-get update && sudo apt-get upgrade -y
```

* Install Packages:
```bash
sudo apt install curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```

* Install Docker: (Skip if you took Docker installed VPS)
- Wait for the installation. Docker setup usually takes 2–5 minutes.
```bash
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Test Docker
sudo docker run hello-world

sudo systemctl enable docker
sudo systemctl restart docker
```
<img width="406" height="56" alt="image" src="https://github.com/user-attachments/assets/b2edbda2-a33b-4689-825d-ef2561225d4e" />

- Enter `Y` if asked

---

## 2. Install Aztec Tools
```bash
bash -i <(curl -s https://install.aztec.network)
```
<img width="593" height="277" alt="image" src="https://github.com/user-attachments/assets/e100a842-9f6b-406c-8a27-edddb0d93c2b" />

- Enter `Y` if asked

```bash
echo 'export PATH="$HOME/.aztec/bin:$PATH"' >> ~/.bashrc

source ~/.bashrc
```
* **Just Restart or Close and Open your Terminal** now to apply changes.
* Check if you installed successfully:
```bash
aztec
```

---

## 3. Update Aztec (Skip this step)
```bash
aztec-up 1.2.1
```
Make sure you are on 1.2.1
```bash
aztec -V
```
<img width="920" height="31" alt="image" src="https://github.com/user-attachments/assets/5c3366cb-326d-4681-a240-e155cc08ef1f" />

---

## 4. Obtain RPC URLs

Best way is to Run your own geth and prysm node to get `Sepolia RPC URL` and `Beacon RPC URL` Follow guide if you want to run on your own [geth-prysm](https://github.com/cryptocattelugu/Ethereum-Full-Node)
  
### Free:
* `RPC URL`: Create a Sepolia Ethereum HTTP API in [Alchemy](https://dashboard.alchemy.com/)
* ### To get an Sepolia RPC from Alchemy:
- Create a new app → fill in details → choose Ethereum → click next → app is created → select chain = Ethereum, network = Sepolia → copy the Network URL
<img width="932" height="404" alt="Screenshot 2025-08-19 134900" src="https://github.com/user-attachments/assets/2a2a8e4a-50d6-43f6-8908-6193825f2e1d" />

* `BEACON RPC`: Create an account on [drpc](https://drpc.org/) and search for `Sepolia Ethereum Beacon Chain ` Endpoints.

### To get a Beacon RPC from dRPC:
Go to dashboard → click Add Key and name it → open Endpoints → search Ethereum Beacon → select Sepolia → copy your Beacon RPC.

<img width="707" height="160" alt="image" src="https://github.com/user-attachments/assets/2d135c48-4f9b-4a30-85b7-be75c474a298" />

### Paid: 
For example: [Ankr](https://www.ankr.com/rpc/?utm_referral=XTqd8eN4w5) is supporting `RPC URL` & `Beacon URL`. You can Register, Fund it with a little USDT via your wallet, Create a project, get your normal **sepolia rpc** and **beacon sepolia rpc**.

* Steps:
- Click `Create Project` & give it a name and select chain as `Ethereum` and then click `Create`

<img width="662" height="296" alt="Screenshot 2025-08-20 094656" src="https://github.com/user-attachments/assets/1cdb1fa7-8da8-43ec-912f-748b76274d91" />

- To get Beacon RPC from Ankr
<img width="670" height="229" alt="Screenshot 2025-08-20 094904" src="https://github.com/user-attachments/assets/dbabaac1-31f3-48df-9fb2-993b979f1a15" />


(or)
- You can use Mintair as an alternate option and it's way cheaper compared to Ankr but on Miantair RPC's are Sold out for now

<img width="950" height="383" alt="Screenshot 2025-08-20 092517" src="https://github.com/user-attachments/assets/794dedf6-2262-458b-ad6b-428030aca21f" />



> Best way is to run your own Geth & Prysm nodes to get your own `RPC URL` & `BEACON RPC` or find any other 3rd party solutions


---

## 5. Generate Ethereum Keys
Create a new Ethereum wallet, then safely back up your `private key` and `public address`.

---

## 6. Get Sepolia ETH
Fund your Ethereum Wallet with `ETH Sepolia` (MIN 1 ETH)

- If you have Sepolia ETH in your main wallet, you can transfer it to your Aztec wallet.
                                   (or)
- You can buy Sepolia ETH using [Testnet Bridge](https://testnetbridge.com/sepolia)

---

## 7. Find IP
```bash
curl ipv4.icanhazip.com
```
* Save it

---

## 8. Enable Firewall & Open Ports
```console
# Firewall
ufw allow 22
ufw allow ssh
ufw enable

# Sequencer
ufw allow 40400
ufw allow 8080
```
<img width="944" height="187" alt="image" src="https://github.com/user-attachments/assets/a8278de2-f927-4abf-be06-1c4eb7e360e6" />

- `Y` and then Enter
---

## 9. Run Sequencer Node
You can run Sequencer Node through one of these two methods: `Docker` or `CLI`

### Method 1: Run via Docker
* Delete CLI Node
```bash
# Stop docker containers
docker stop $(docker ps -q --filter "ancestor=aztecprotocol/aztec") && docker rm $(docker ps -a -q --filter "ancestor=aztecprotocol/aztec")

# Stop screens
screen -ls | grep -i aztec | awk '{print $1}' | xargs -I {} screen -X -S {} quit
```

* Create `aztec` directory:
```bash
mkdir aztec
```

* Get into `aztec` directory:
```bash
cd aztec
```
 
* Create `.env`
```bash
nano .env
```

* Replace the following code in `.env`
```env
ETHEREUM_RPC_URL=RPC_URL
CONSENSUS_BEACON_URL=BEACON_URL
VALIDATOR_PRIVATE_KEY=0xYourPrivateKey
COINBASE=0xYourAddress
P2P_IP=P2P_IP
```
* Replace the following variables before you Run Node:
  * `RPC_URL` & `BEACON_URL`: Step 4
  * `0xYourPrivateKey`: Your EVM wallet private key starting with `0x...`
  * `0xYourAddress`: Your EVM wallet public address starting with `0x...`
  * `P2P_IP`: Your server IP (Step 7)

* Output should look like this
<img width="950" height="458" alt="Screenshot 2025-08-19 142522" src="https://github.com/user-attachments/assets/21eeae22-f013-4976-8b80-7e548bd6cb9f" />

- Ctrl + `O`
- Then `Enter`
- Ctrl + `X`


* Create `docker-compose.yml`:
```bash
nano docker-compose.yml
```

* Replace the following code in `docker-compose.yml`
```yml
services:
  aztec-node:
    container_name: aztec-sequencer
    network_mode: host 
    image: aztecprotocol/aztec:1.2.1
    restart: unless-stopped
    environment:
      ETHEREUM_HOSTS: ${ETHEREUM_RPC_URL}
      L1_CONSENSUS_HOST_URLS: ${CONSENSUS_BEACON_URL}
      DATA_DIRECTORY: /data
      VALIDATOR_PRIVATE_KEY: ${VALIDATOR_PRIVATE_KEY}
      COINBASE: ${COINBASE}
      P2P_IP: ${P2P_IP}
      LOG_LEVEL: debug
    entrypoint: >
      sh -c 'node --no-warnings /usr/src/yarn-project/aztec/dest/bin/index.js start --network alpha-testnet --node --archiver --sequencer'
    ports:
      - 40400:40400/tcp
      - 40400:40400/udp
      - 8080:8080
    volumes:
      - /root/.aztec/alpha-testnet/data/:/data
```

- Ctrl + `O`
- Press `Enter`
- Ctrl + `X`

  
* Run Node Docker:
```bash
docker compose up -d
```

<img width="950" height="101" alt="image" src="https://github.com/user-attachments/assets/cd681ea1-c7fe-4fab-ad67-e95e03bb3330" />


* To check Node Logs:
 ```bash
docker compose logs -fn 1000
```

* Optional: Stop and Kill Node
```bash
docker compose down -v
```
* Done, you can now head to Step 10.


### Method 2: Run via CLI
* Open screen
```bash
screen -S aztec
```

* Run Node
```
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls RPC_URL  \
  --l1-consensus-host-urls BEACON_URL \
  --sequencer.validatorPrivateKey 0xYourPrivateKey \
  --sequencer.coinbase 0xYourAddress \
  --p2p.p2pIp IP
```
Replace the following variables before you Run Node:
* `RPC_URL` & `BEACON_URL`: Step 4
* `0xYourPrivateKey`: Your EVM wallet private key starting with `0x...`
* `0xYourAddress`: Your EVM wallet public address starting with `0x...`
* `IP`: Your server IP (Step 7)

### Optional Commands:
**Screen Commands:**
* Minimze screen: `Ctrl` + `A` + `D`
* Return to screen: `screen -r aztec`
* Kill screen (when inside): `Ctrl`+`C+
* Kill screen (when outside): `screen -XS aztec quit`

---

## 10. Sync Node (Optional)
After entering the command, your node starts running, It takes a few minutes for your node to get synced.

* Check the latest synced block number of your sequencer:
```
curl -s -X POST -H 'Content-Type: application/json' \
-d '{"jsonrpc":"2.0","method":"node_getL2Tips","params":[],"id":67}' \
http://localhost:8080 | jq -r ".result.proven.number"
```

## 11. Register Validator
Make sure your Sequencer node is fully synced, before you proceed with Validator registration.

**Official Validator Registration: ZKPassport**
* Visit: https://testnet.aztec.network/add-validator
* Complete ZKPassport humanity verification:
* Connect the wallet you used to run your Aztec sequencer node
* Make sure your passport has NFC (electronic chip)
* After verification, you’ll enter the validator registration queue and earn the Explorer Discord role
* If you don’t have a passport or it lacks a chip, fill out the form to join the validator set https://tally.so/r/mVWM7v

---

## 12. Aztec Dashboard
* Visit the https://dashtec.xyz/
* Check your validators health
* Connect your X & Discord

---

## 🔃 Update Sequencer Node

### Update docker-compose method Nodes
1- Stop node
```console
docker stop $(docker ps -q --filter "ancestor=aztecprotocol/aztec") && docker rm $(docker ps -a -q --filter "ancestor=aztecprotocol/aztec")

# Or

cd aztec
docker compose down -v
```

2- Update CLI commands
```bash
source ~/.bashrc
aztec-up 1.2.1
```

3- Delete old data
```bash
rm -rf ~/.aztec/alpha-testnet/data/
```

4- Rerun your node
```
docker compose up -d
```
* Make sure you are in `aztec` directory where `docker-compose.yml` file exists.
* You can read the full details of running the node via [docker compose](#method-1-run-via-docker)

#

### Update CLI method Nodes
1- Stop node
```
screen -ls | grep -i aztec | awk '{print $1}' | xargs -I {} screen -X -S {} quit
```
* Or manually stop the screen session you are running your node in it

2- Update CLI commands
```bash
source ~/.bashrc
aztec-up 1.2.1
```

3- Delete old data
```bash
rm -rf ~/.aztec/alpha-testnet/data/
```

4- Rerun using this CLI command
```bash
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls RPC_URL  \
  --l1-consensus-host-urls BEACON_URL \
  --sequencer.validatorPrivateKey 0xYourPrivateKey \
  --sequencer.coinbase 0xYourAddress \
  --p2p.p2pIp IP
```
Replace the following variables before you Run the node:
* `RPC_URL` & `BEACON_URL`: Step 4
* `0xYourPrivateKey`: Your EVM wallet private key starting with `0x...`
* `0xYourAddress`: Your EVM wallet public address starting with `0x...`
* `IP`: Your server IP (Step 7)

---

## Troubleshooting:
If you encountered: `ERROR: world-state:block_stream Error processing block stream: Error: Obtained L1 to L2 messages failed to be hashed to the block inHash`

* You have to stop your node, delete data and restart it.
* Follow [Update Node](https://github.com/0xmoei/aztec-network/blob/main/README.md#-update-sequencer-node) steps

---

## To Get Guardian Discord Role:
Claim the Guardian role as you are running a Sequencer Node and keep an uptime.

* To claim:
  * Go to the `upgrade-role` channel
  * Type `/checkip`
  * Enter your `IP` & `Node Address`

* If you are not eligible to claim the Guardian role, wait until the next snapshot.
