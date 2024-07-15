# Guide to run koii node on vps:
These are the commands that were used in : 
https://youtu.be/h9LkcSo29IA

for more detailed information please check:
https://docs.koii.network/run-a-node/task-nodes/Running-on-VPS


**-Update the apt**
```
sudo apt update
sudo apt upgrade
```
**-Install git**
```
sudo apt install git
```
**-Clone the project**
```
git clone https://github.com/koii-network/VPS-task
```
**-let's go to the cloned project directory**
```
cd VPS-task
```
**-Download koii cli**
```
sh -c "$(curl -sSfL https://raw.githubusercontent.com/koii-network/k2-release/master/k2-install-init.sh)"
```
**-check if it works**
```
koii --version
```
**-configure the testnet url**
```
koii config set --url https://testnet.koii.network/
```
**-check if it works**
```
koii balance
```
**-create new wallet**
```
koii-keygen new -o /root/.config/koii/id.json
```
Now update your .env-local file:

```
cd VPS-task
nano .env-local
```
Change ENVIRONMENT from development to production

```
ENVIRONMENT="production"
```
Set initial staking wallet balance to whatever you want (keep in mind this should bigger than all staked koii in all of the tasks combined):

```
INITIAL_STAKING_WALLET_BALANCE=4
```
Change taskID to the new task id, for example the free token task:

```
TASKS="Gz2xuLQW1scgiasVLfefteifwWj4GnCJCt1SyYTSr3L4"
```
**-install docker**
```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$UBUNTU_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
**-check if docker-compose was installed proberly**
```
docker compose --version
```
**-run the docker ((you have to be in the VPS-Task directory))**
```
docker compose up
```

**-If it docker-compose up is running properly then press ctrl + c then write**
```
docker compose up -d
```

**-this will run docker in the background**

**-to check if docker is running proberly use**
```
docker logs -f --tail 10 task_node
```

**To Claim rewards**
**-install npm library**
```
sudo apt install npm
```

**-Run this command**
```
cd
npx @_koii/create-task-cli@latest
```

**-then choose claim rewards for this example i will use the free token Task**

**Task id:** Gz2xuLQW1scgiasVLfefteifwWj4GnCJCt1SyYTSr3L4

**stakePotAccount:** stakepotaccountvNjz8uPsh9ar4NJJK6euYcgxjSj2

**address that the funds will be transfered to:** your_wallet_address

**path to claimer wallet:** VPS-task/namespace/staking_wallet.json


##
--------------------------------------------------------------------------
##


