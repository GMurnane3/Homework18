# **Proof of Authority Development Chain**

**Set up my custom testnet blockchain**

1. Created a project directory called Homework (C:\Users\gmurn\OneDrive\Documents\ASU FinTech\Homework\Homework18\Homework) for my new network.
2. Created a &quot;Screenshots&quot; folder inside of the project directory.
3. Created accounts for two nodes for the network with a separate datadir for each using geth.
   - ./geth account new --datadir node1 (Public address of the key: 0xaa885ff76eea3c232428c214357915e69b4f55e5)
   - ./geth account new --datadir node2 (Public address of the key: 0x34064e5666b1d6f5fd141121738f097d4449434e)
4. Ran puppeth, creating the Murnane network, and selected the option to configure a new genesis block.
5. Chose the Clique (Proof of Authority) consensus algorithm.
6. Paste both node&#39;s account addresses into the list of accounts to seal.
7. Pasted them again in the list of accounts to pre-fund.
8. Chose no for pre-funding the pre-compiled accounts with wei.
9. Next chose the &quot;Manage existing genesis&quot; option and exported genesis configurations, deleting the murnane-harmony.json file.
10. Initialize each node with the murnane.json with geth.
    - ./geth init Murnane.json --datadir node1
     - ./geth init Murnane.json --datadir node2
11. Ran the first node, unlocked the account, enabling mining and the RPC flag.
     - ./geth --datadir node1 --unlock &quot;0xaa885ff76eea3c232428c214357915e69b4f55e5&quot; --mine --rpc
12. Set a different peer port for the second node and used the first node&#39;s enode address as the bootnode flag.
     - ./geth --allow-insecure-unlock --datadir node2 --unlock &quot;0x34064e5666b1d6f5fd141121738f097d4449434e&quot; --port 30304 --bootnodes &quot;enode://6485277ddb7a7391732fd68a1f02705765e54805a00015d45e69f4c01d037a5f8d1a85d21a2ec9978d7be8133b197601a967b6ec81dbc0a807a8cd326e66ab7e@127.0.0.1:30303&quot; --ipcdisable
13. Both nodes are now producing new blocks.
14. Imported node 2&#39;s private key into MyCrypto by importing the keystore file from the node1/keystore directory.
15. Using the MyCrypto GUI wallet, connected to the node with the exposed RPC port (node 1), by creating a custom network (Murnane), identifying the chain ID (123), and using ETH as the currency.

**Send a test transaction**

Here I sent 1,000,000 ETH from Node 1 to Node 2:

![Send 1,000,000 ETH from Node 1 to Node 2](https://user-images.githubusercontent.com/70610967/107569551-aa8bda00-6ba5-11eb-803a-5a4fefc95874.PNG)

Here you can see it having been mined:

![Mining Transaction](https://user-images.githubusercontent.com/70610967/107569632-c8593f00-6ba5-11eb-9f88-a844befac242.PNG)

In checking the transaction status, one can see that the transaction was effected, however it would never move from a Pending status to Completed:

![Check Transaction Status](https://user-images.githubusercontent.com/70610967/107569852-022a4580-6ba6-11eb-9f8e-4c6ee099d1bc.PNG)

**Created a repository**

- Created a README.md in my project directory containing documentation that explains how to start my network.
- Included:
  - environment setup instructions
  - dependencies
  - all of the geth flags required to get both nodes to mine and explained what they mean.
- Explained the configuration of the network, it&#39;s blocktime, chain ID, account passwords, ports, etc.
- Explained how to connect MyCrypto to your network, demonstrating via screenshots and steps
- Uploaded the code, including the murnane.json and node folders.

**Instructions on how to launch the Murnane chain**

This network is configured for 5 second block times, and uses the Clique Proof of Authority consensus algorithm. The chain ID is 123.

The sealer node addresses are:

0xaa885ff76eea3c232428c214357915e69b4f55e5

0x34064e5666b1d6f5fd141121738f097d4449434e

The account password for both nodes is password

Run the first node and enable the mining/sealing

./geth --allow-insecure-unlock --datadir node1 --unlock &quot;0xaa885ff76eea3c232428c214357915e69b4f55e5&quot; --mine --rpc

We enable the --rpc flag on the first node to talk to it later. This defaults to port 8545. We need to unlock the node&#39;s account to enable it to sign blocks.

Copied the enode address from this node

enode://6485277ddb7a7391732fd68a1f02705765e54805a00015d45e69f4c01d037a5f8d1a85d21a2ec9978d7be8133b197601a967b6ec81dbc0a807a8cd326e66ab7e@127.0.0.1:30303

Use the first node&#39;s enode address as the bootnode for the second node and run on a separate port (disabling ipc)

./geth --allow-insecure-unlock --datadir node2 --unlock &quot;0x34064e5666b1d6f5fd141121738f097d4449434e&quot; --port 30304 --rpc --bootnodes &quot;enode://6485277ddb7a7391732fd68a1f02705765e54805a00015d45e69f4c01d037a5f8d1a85d21a2ec9978d7be8133b197601a967b6ec81dbc0a807a8cd326e66ab7e@127.0.0.1:30303&quot; --ipcdisable

Using the first node as a bootnode will enable the nodes to communicate with each other, and discover new nodes later.

Mining

You should now be mining/sealing blocks.

Send a test transaction

Open up MyCrypto and select Change network at the bottom left.

Select Add Custom Node and use http://127.0.0.1:8545 to connect to the first node (don't use https://), add a name, use chain ID 567 and save.

Your configuration should look like this:

You should now be connected to the local blockchain.

Click on the Keystore file option to access the first node&#39;s wallet and navigate to node1/keystore and select the keystore file, then enter password as the password.

You should now be able to send a transaction. Fill in the second node&#39;s account and send it one ETH.

Once confirmed, you can check the TX Status by clicking the button in the popup, or pasting the TX Hash into the TX Status section of the app.

**Description of Screenshots:**

Screenshot 2021-02-05 (#1) – Creating the 2 nodes and the network:

![Screenshot 2021-02-05 (#1)](https://user-images.githubusercontent.com/70610967/107152992-66d86c80-6928-11eb-95a3-96deaa3fb0c4.PNG)

Screenshot 2021-02-05 (#2) – Create the new network and Genesis block

![Screenshot 2021-02-05 (#2)](https://user-images.githubusercontent.com/70610967/107153023-9b4c2880-6928-11eb-9a33-c40563a33c82.PNG)

Screenshot 2021-02-05 (#3) – Export the Genesis configurations

![Screenshot 2021-02-05 (#3)](https://user-images.githubusercontent.com/70610967/107153037-b323ac80-6928-11eb-93c9-59c7e43ac5b7.PNG)

Screenshot 2021-02-05 (#4) – Initializing the 2 nodes

![Screenshot 2021-02-05 (#4)](https://user-images.githubusercontent.com/70610967/107153060-cc2c5d80-6928-11eb-9eaa-712486e86716.PNG)

Screenshot 2021-02-04 (#4) – Mining:

![Screenshot 2021-02-04 (#4)](https://user-images.githubusercontent.com/70610967/107153079-dea69700-6928-11eb-94fe-a6474e6fea83.PNG)

Screenshot 2021-02-05 (#5) – Setting up your custom node (this configuration did hot work as one needs to use 'http://', not 'https://'

![Screenshot 2021-02-05 (#5)](https://user-images.githubusercontent.com/70610967/107153094-ed8d4980-6928-11eb-8f32-14c088a8e32c.PNG)
