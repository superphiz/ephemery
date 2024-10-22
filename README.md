# ephemery
Guide to getting started with the Ethereum Ephemery Testnet quickly

https://ephemery.dev is the central repository for all things Ephemery

## 0. Notes

This guide will become outdated VERY quickly! It's meant to capture a moment in time of Ephemery development, and unless it has been updated recently will be mostly useless after a month.

Everything in this guide is free for anyone to follow, including the software and Ephemery Ether. The only things that could incur an expense are the hardware and Internet connection. Virtual Private Servers (VPS) services often provide a server that you can use for around $6 a month.

## 1. Test machine setup

This demonstration is being done on an Ubuntu 24.04.1 (Noble Numbat) Desktop installed on a VirtualBox Virtual machine. 
- The Desktop version isn't generally recommended for running a validator, but it won't hurt and I'm using it to make copy/pasting easier when I create the video.
- I installed the VirtualBox Additions before starting this guide. It isn't necessary to do this, but you can.
- In order to install VirtualBox Additions, I also installed some pre-requisites: ```sudo apt install gcc make perl```

## 2. The big picture

Running an Ethereum validator requires two different pieces of software to work together, these are called the Execution client (historically called an "Eth1 client") and the Consensus client (the "Eth2 cleint). They work in concert, with the execution client managing transactions and the consensus client managing the chain. In order to have a validator running, we'll need both of these clients up and running, then we can deposit 32 [Ephemery]Ether to be a validator.

## 3. Execution Client

For this demonstration I'm using T-ess's guide based on geth and lodestar](https://github.com/ephemery-testnet/ephemery-scripts/blob/master/manual/setup-geth-lodestar.md). Because of a deep desire to develop [client diversity](https://clientdiversity.org] I strongly suggest that people use a different execution client, but because Ephemery is still in development, I'm using what's available.

### Install dependencies

```
sudo apt install golang-go yarn curl nodejs git default-jre make gcc
```

### Download the Ephemery tesntet configuration files

Download the `testnet-all.tar.gz` file for the [latest release of the Ephemery testnet](https://github.com/ephemery-testnet/ephemery-genesis/releases) to this directory using `wget`. Then unzip inside this folder. Note that the link in the example is likely to be outdated.

```
cd ~
mkdir testnet-all
cd testnet-all
wget https://github.com/ephemery-testnet/ephemery-genesis/releases/download/ephemery-138/testnet-all.tar.gz #this is likely to be an outdated resource
tar -xzf testnet-all.tar.gz
```

### Generate a jwt token to allow Eth1 and Eth2 clients to communicate.
The following command will generate a secret to ensure secure communication between the Execution Client and the Consensus client at `/tmp/jwtsecret`. Be mindful that using a jwt may require additional flags to be provided.

```
openssl rand -hex 32 | tr -d "\n" > "/tmp/jwtsecret"
```

### Download geth

```
cd ~
wget https://gethstore.blob.core.windows.net/builds/geth-linux-amd64-1.14.11-f3c696fa.tar.gz
tar xvf geth-linux-amd64-1.14.11-f3c696fa.tar.gz
sudo mv geth-linux-amd64-1.14.11-f3c696fa/geth /usr/local/bin/
rm -rf ~/geth-linux-amd64-1.14.11-f3c696fa*
```
### Initialize Geth with Ephemery settings

```
cd ~
geth init --datadir "~/datadir-geth" ~/testnet-all/genesis.json
```




## 4. Consensus Client

## 5. Setting up MetaMask

## 6. Getting Ephemery Ether

## 7. Creating the validator keys and deposit data

## 8. Importing the validator keys

## 9. Making the deposit

## 10. Monitoring progress
