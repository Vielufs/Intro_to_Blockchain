# Proof of Authority Development Chain

For this assignment, you will take on the role of a new developer at a small bank.

Your mission, should you choose to accept it, will be to set up a testnet blockchain for your organization.

To do this, you will create and submit four deliverables:

* Set up your custom testnet blockchain.

* Send a test transaction.

* Create a repository.

* Write instructions on how to use the chain for the rest of your team.

## Background

You have just landed a new job at ZBank, a small, innovative bank that is interested in exploring what
blockchain technology can do for them and their customers.

Your first project at the company is to set up a private testnet that you and your team of developers
can use to explore potentials for blockchain at ZBank.

You have decided on setting up a testnet because:

There is no real money involved, which will give your team of developers the freedom to experiment.

Testnets allows for offline development.

In order to set up a testnet, you will need to use the following skills/tools we learned in class:

* Puppeth, to generate your genesis block.

* Geth, a command-line tool, to create keys, initialize nodes, and connect the nodes together.

* The Clique Proof of Authority algorithm.

Tokens inherently have no value here, so we will provide pre-configured accounts and nodes for easy setup.

After creating the custom development chain, create documentation for others on how to start it using the pre-configured
nodes and accounts. You can name the network anything you want, have fun with it!

Be sure to include any preliminary setup information, such as installing dependencies and environment configuration.

## Instructions

### Setup the custom out-of-the-box blockchain

* Create a new project directory for your new network. Call it whatever you want!

* Create a "Screenshots" folder inside of the project directory.

* Create accounts for two (or more) nodes for the network with a separate `datadir` for each using `geth`.

* Run `puppeth`, name your network, and select the option to configure a new genesis block.

* Choose the `Clique (Proof of Authority)` consensus algorithm.

* Paste both account addresses from the first step one at a time into the list of accounts to seal.

* Paste them again in the list of accounts to pre-fund. There are no block rewards in PoA, so you'll need to pre-fund.

* You can choose `no` for pre-funding the pre-compiled accounts (0x1 .. 0xff) with wei. This keeps the genesis cleaner.

* Complete the rest of the prompts, and when you are back at the main menu, choose the "Manage existing genesis" option.

* Export genesis configurations. This will fail to create two of the files, but you only need `networkname.json`.

* You can delete the `networkname-harmony.json` file.

* Screenshot the `puppeth` configuration once complete and save it to the Screenshots folder.

* Initialize each node with the new `networkname.json` with `geth`.

* Run the first node, unlock the account, enable mining, and the RPC flag. Only one node needs RPC enabled.

* Set a different peer port for the second node and use the first node's `enode` address as the `bootnode` flag.

* Be sure to unlock the account and enable mining on the second node!

* You should now see both nodes producing new blocks, congratulations!

### Send a test transaction

* Use the MyCrypto GUI wallet to connect to the node with the exposed RPC port.

* You will need to use a custom network, and include the chain ID, and use ETH as the currency.

![custom-node](Images/custom-node.png)

* Import the keystore file from the `node1/keystore` directory into MyCrypto. This will import the private key.

* Send a transaction from the `node1` account to the `node2` account.

* Copy the transaction hash and paste it into the "TX Status" section of the app, or click "TX Status" in the popup.

* Screenshot the transaction metadata (status, tx hash, block number, etc) and save it to your Screenshots folder.

* Celebrate, you just created a blockchain and sent a transaction!

![transaction-success](Images/transaction-success.png)

### Create a repository, and instructions for launching the chain

* Create a `README.md` in your project directory and create documentation that explains how to start the network.

* Remember to include any environment setup instructions and dependencies.

* Be sure to include all of the `geth` flags required to get both nodes to mine and explain what they mean.

* Explain the configuration of the network, such as it's blocktime, chain ID, account passwords, ports, etc.

* Explain how to connect MyCrypto to your network and demonstrate (via screenshots and steps) and send a transaction.

* Upload the code, including the `networkname.json` and node folders.

### Remember, *never* share your mainnet private keys! This is a testnet, so coins have no value here!

### Hints

* If you get stuck - try our step by step PoA Guide located [here](Resources/POA-Blockchain-guide.md).

* If you aren't seeing any movement in the wallet amounts in MyCrypto after sending/receiving transactions, try the following:
    * Terminate both nodes using `control+C` in the Node1 and Node2 terminal windows.
    * Change networks in MyCrypto to a Testnet such as Kovan.
    * Restart Node1 and Node2 in their terminal windows.
    * Reconnect to your network in MyCrypto.
    * Log into your wallet and refresh the amount.
    
* If that doesn't help make sure you are sending a large enough sum of ETH to see actual movement in the digits. You may have to click on the amount itself to see the full value down to the WEI.

    ![before_after_click_mycrypto](Images/before_after_click_mycrypto.png)

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
# Solution 

## Part One
* Creating my new wallet for my new test ETH blockchain. In this test example the main test account mnemonic phrase is: acid movie neglect organ health diagram blade neutral glue flush false pulp. Access both my public and privates keys under my test wallet. Public address is: " 0x845DE31F7001671287812Cb689DaC880200AB33b ". It is under the Ropsten testnet. 
* Then I created the two nodes that will be minig and completing the chains. Mining node is called miner and the second node is helper. Public address to miner is: 0x530545857c3216F45Cbd9cd32Db682CE790C6ebB . Helper node public key is:  0x6d155320fBa3706e513BD9CF47e9C7bD2C00a919. 
* The genesis block vim will have my accouunts prefunded (the miner and helper node). Json file was saved and now we have everything to begin mining.

## Part Two
* Part two we initialize the nodes to the gensis block. Following that we will then set them to mine. First starting with with NodeM we will start the mining process with " ./geth --datadir node1 --unlock "0x530545857c3216F45Cbd9cd32Db682CE790C6ebB" --mine --rpc --allow-insecure-unlock". Thn we follow up with nodeH iniatilize it with this code " ./geth --datadir node2 --unlock "0x6d155320fBa3706e513BD9CF47e9C7bD2C00a919" --mine --port 30304 --bootnodes "enode://aeedb912e6ccd4e7dc36041de7b43a732ccc7e4e65ccb280d915d984fc0e0b68b48136671d48f94a74fb8e0eb59f09fa44631774d15846b795fb25f7c749bae2@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock" this way they both mine. Then we check our Mycrypto and make sure to add your new network by creating a custom network in MyCrypto and you add your chain id, currency(ETH) and your local host address. Since we prefunded both accounts they automatically will have a large balance (self made rich :-D ).

##Part Three
* Start a transaction between both nodeM and nodeH. Monitor the transaction status until successful, I submitted a very big transaction and the mining process is taking longer than anticipated but eventually the transaction would be mined. Then done! Yout test network is completed please see the snap shots and follow this simple theoritical guide to take you there. Download all the files i have uploaded so you can execute your own testnet!