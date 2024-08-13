# Verify Zero-Knowledge Proofs with Succinct SP1

<img src="https://app.ashbyhq.com/api/images/org-theme-wordmark/b045220d-46fa-4dd2-9364-ea30bc7bb174/81de4234-5c9f-40cf-8566-4324fd3a42f4.png" width="700"/>

## About Succinct
Succinct is creating a decentralized network that secures blockchain applications with cryptographic truth, offering reliable and cost-effective infrastructure for zero-knowledge proof systems.
* [Twitter](https://x.com/SuccinctLabs)
* [Website](https://succinct.xyz/)
* [Discord](https://discord.gg/succinctlabs)
* [Docs](https://docs.succinct.xyz/)
* [Github](https://github.com/succinctlabs)

## About SP1
SP1 is a high-performance virtual machine (zkVM) that uses zero-knowledge proofs (ZKPs) to verify that programs are executing correctly. It allows you to easily implement ZKPs using code written in the Rust. By simplifying the complexity of traditional ZKP systems, SP1 provides secure and fast solutions in various blockchain applications such as rollups, bridges, and light clients. As an entirely open-source platform, SP1 is trusted by leading blockchain projects and undergoes regular security audits to ensure its reliability.

For more about SP1, check [here](https://docs.succinct.xyz/introduction.html).


<img src="https://docs.succinct.xyz/sp1.png" width="700"/>

Note: The script only works on Ubuntu (20.04/22.04). 


## Step 1: System Updates and Installation of Required Tools

### Update System Packages
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install cmake pkg-config libssl-dev build-essential -y
```

### Rust and Cargo Installation
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
```

### Docker Installation
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update >/dev/null 2>&1
sudo apt-get install -y docker-ce docker-ce-cli containerd.io >/dev/null 2>&1
sudo docker run hello-world >/dev/null 2>&1
```
#### Check Docker version:
```bash
docker --version
```

## Step 2: Install SP1 Toolchain

### Download and Install SP1 
```bash
curl -L https://sp1.succinct.xyz | bash
source ~/.bashrc
sp1up
```

![1](https://github.com/user-attachments/assets/394f0326-56a0-4b78-928d-da591125d72a)


#### Check the version of the SP1 toolchain to make sure it is installed correctly:
```bash
cargo +succinct --version
```

## Step 3: Initialize and Configure SP1 Project

### Initialize New SP1 Project
```bash
cargo prove new fibonacci
cd fibonacci/script
```

### Run and Verify the Project (Note: This step may take a little longer.)
```bash
# First, execute the project without generating a proof to ensure that everything is set up correctly:
RUST_LOG=info cargo run --release -- --execute

# After confirming that the project runs successfully, generate and verify ZK proof:
RUST_LOG=info cargo run --release -- --prove
```

#### You can verify the successful installation of the SP1 CLI by checking the version of `cargo prove`:
```bash
cargo prove --version
```
![2](https://github.com/user-attachments/assets/c5a7d96a-779d-4669-b768-8f46906469ef)


