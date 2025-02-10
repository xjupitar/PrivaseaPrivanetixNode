# Recommended Configurations
| SPECS | LEVEL 1 | LEVEL 2 | LEVEL 3 | LEVEL 4 |
|-------------|-------------|-------------|-------------|-------------|
| OS | Debian/Ubuntu | Debian/Ubuntu | Debian/Ubuntu | Debian/Ubuntu |
| Storgae | 100GB available | 100GB available | 100GB available | 100GB available |
| Processor | 16 cores and above| 8 cores and above | 4 cores and above| 4 cores and below  |
|Memory| 8GB and above|4GB and above| 4GB|4GB and Below|
|Port|Open TCP port 8181 |Open TCP port 8181 |Open TCP port 8181 |Open TCP port 8181 |
|Network| Public static IP|Public static IP|Public static IP|Public static IP|
|Weight Coefficient|2x|1.5x|1.2x|1x|

### Some Tips choosing the right VPS server: 
Device performance impacts your PoW rewards. Rewards are calculated using the following formula:
<p align="center">​Points = Weight Coefficient x Uptime Percentage</p>

Tasks are completed randomly and during that time if you node failed to complete the task, your node will be considered as Level 4 even though your node meets the Level 1,2, or 3 configuration. So Make sure you choose a stable server such as 'Hetzner' during purchasing any VPS.

# Setup Guide
## Step 1: Install Docker
If Docker is already installed, you can skip this step. Otherwise follow these commands. 
<pre><code>sudo apt update && apt upgrade -y</code></pre>
<pre><code>sudo apt install docker.io</code></pre>
<pre><code>sudo apt update</code></pre>
Now verify if docker is installed sucessfully using following command
<pre><code>sudo docker --version</code></pre>
You will see output similar to the following image if docker is installed correctly.

<p align="center">
   <img src="Images/dockerexample.png">
</p>

## Step 2: Enable Docker Service
<pre><code>sudo systemctl start docker
sudo systemctl enable docker</code></pre>

## Step 3: Pull Docker Mirroring
<pre><code>sudo docker pull privasea/acceleration-node-beta</code></pre>

## Step 4: Creating Directory
First switch to root user (For most, root is automatically selected). 
<pre><code>sudo su</code></pre>
Enter your machine password to confirm.

<p align="center">
   <img src="Images/superuser.png">
</p>

Now let's create a directory for running the node program.
<pre><code>mkdir -p  /privasea/config && cd  /privasea</code></pre>

## Step 4: Creating Keystore File
Execute the following command to generate a new Keystore file.
<pre><code>sudo docker run -it -v "/privasea/config:/app/config"  \
privasea/acceleration-node-beta:latest ./node-calc new_keystore</code></pre>
### It will ask you to enter a password. Password won't show. So just make sure you put same passowrd to cofirm it.
### Remember this password. You will need this password later.
