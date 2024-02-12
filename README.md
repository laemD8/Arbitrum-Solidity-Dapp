# Arbitrum Workshop Session 1: Decentralized Cupcake Vending Machine

This guide is based on the official [Arbitrum Quickstart Guide](https://docs.arbitrum.io/for-devs/quickstart-solidity-hardhat). We extend our gratitude to Arbitrum for providing comprehensive resources. Our project focuses on enhancing the learning experience and simplifying the execution of their tutorial.

## Overview

This project serves as a hands-on guide for "Arbitrum Workshop Session 1," a collaborative initiative by the [Blockchain Acceleration Foundation (BAF)](https://twitter.com/TheBAFNetwork) and [Arbitrum](https://twitter.com/arbitrum). In this workshop, we aim to explore the creation of a decentralized application using Arbitrum's cutting-edge technology. This guide represents a harmonious blend of Arbitrum's technology and BAF's commitment to advancing Web3 adoption on a global scale. Participants will gain insights into Ethereum scalability, smart contract development, and the practical implementation of blockchain solutions. This workshop acts as a launching pad for individuals eager to explore the vast possibilities and contribute to the evolving landscape of blockchain technology.

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) installed (Version 20.11.0 is recommended to mitigate potential errors)
- [Yarn](https://yarnpkg.com/) package manager
- [MetaMask](https://metamask.io/) browser extension

## Deployment

### Configure your project directory
  1. Clone the Repository: `git clone https://github.com/laemd8/decentralized-cupcakes.git`
  2. Change into the Project Directory: `cd decentralized-cupcakes`
  3. Install Dependencies: `yarn install`

> [!NOTE]
> The Solidity-written smart contract compiles into EVM bytecode, allowing deployment across multiple Ethereum-compatible blockchains such as Ethereum mainnet, Arbitrum One, and Arbitrum Nova.

  4. Compile the Smart Contract: `yarn hardhat compile`

> [!WARNING]
> Anticipate the initial compilation to encounter errors. Proceed by following the instructions provided, then execute yarn hardhat compile repeatedly until it completes successfully.

One common error you may encounter when running yarn hardhat compile is due to missing dependencies required by the @nomicfoundation/hardhat-toolbox plugin.

To address this issue, follow these steps:

* Install the missing dependencies by executing the following command in your terminal:
     ```
     npm install --save-dev "@nomicfoundation/hardhat-chai-matchers@^2.0.0" "@nomicfoundation/hardhat-ethers@^3.0.0" "@nomicfoundation/hardhat-network-helpers@^1.0.0"     
     "@nomicfoundation/hardhat-verify@^2.0.0" "@typechain/ethers-v6@^0.5.0" "@typechain/hardhat@^9.0.0" "@types/chai@^4.2.0" "@types/mocha@>=9.1.0" "chai@^4.2.0" "hardhat-gas- 
     reporter@^1.0.8" "solidity-coverage@^0.8.1" "ts-node@>=8.0.0" "typechain@^8.3.0" "typescript@>=4.5.0"
     ```
* Once the dependencies are installed, attempt to run `yarn hardhat compile` again.
  
This should resolve the issue and allow you to compile your project successfully.

> [!NOTE]
> After successful compilation, you should find the compiled artifacts at `decentralized-cupcakes/artifacts/contracts/VendingMachine.sol`
     
- [x] **Congratulations! You've successfully deployed the Cupcake Vending Machine smart contract to the Arbitrum Sepolia testnet** 😼🫵

### Deploy the Smart Contract Locally

1. We'll utilize the first terminal window to initiate Hardhat's integrated local Ethereum node.
2. Following that, we'll set up a wallet for interaction with our smart contract once it's deployed to (1).
3. Finally, in the second terminal window, we'll proceed with deploying our smart contract to the node in (1).

🔹 **Run a Local Ethereum Network and Node:**

1. Open a terminal window in your `decentralized-cupcakes` directory.
2. Execute the following command to initiate Hardhat's integrated local Ethereum network `yarn hardhat node`.
4. You should observe output indicating the HTTP and WebSocket JSON-RPC server at http://127.0.0.1:8545/. Additionally, test accounts with generated ETH balances will be displayed.
     ```
     ...
     Account #0: 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 (10000 ETH)
     Private Key: 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
     ...
     ```
     
> [!CAUTION]
> **NEVER SHARE YOUR PRIVATE KEYS:**
> Your Ethereum Mainnet wallet's private key serves as the password to all of your funds. Never disclose it to anyone and refrain from copying it to your clipboard to maintain security.

🔹 **Configure Metamask for Localhost 8545:**

  1. Open Metamask and create or import a wallet.
  2. By default, Metamask connects to the Ethereum mainnet. To switch to our local "testnet," enable test networks by clicking "Show/hide test networks" from the network selector   dropdown.
  3. Select "Custom RPC" to add a new network manually.
  4. Enter the following details for Localhost 8545:

     ```
     Network Name: Localhost 8545
     New RPC URL: http://127.0.0.1:8545
     Chain ID: Leave it blank for local testing.
     Currency Symbol: ETH
     ```
     
  5. Click "Save" or "Add Network" to confirm the configuration.
  6. Select the Localhost 8545 network.
     
> [!IMPORTANT]
> Your mainnet wallet won't have a balance on the local testnet's node. To access 10,000 fake ETH, let's import one of the test accounts into Metamask.

  7. Copy the private key of one of the test accounts generated by Hardhat (e.g., 0xac0..f80) from the first terminal, and then, import it into Metamask.

> [!NOTE]
> You should now see a balance of 10,000 ETH. Keep your private key handy; we'll use it again shortly. 

🔹 **Deploy the Smart Contract to Your Local Testnet:**

1. From another terminal instance, install additional dependencies for contract deployment: `yarn add --dev @nomicfoundation/hardhat-ethers ethers hardhat-deploy hardhat-deploy-ethers`
2. Deploy your smart contract to the local testnet's node: `yarn hardhat run scripts/deploy.js --network localhost`

> [!IMPORTANT]
> This command initiates the deployment of your smart contract to the local testnet. After successful deployment, you will see an output similar to: `Cupcake vending machine deployed to 0xe7f1725E7734CE288F8367e1Bb143E90bb3F0512`
> 
> The address (e.g., 0xe7...512) is the location of your smart contract on the local testnet.

3. Ensure that the "Localhost" network is selected within Metamask.
4. Copy the contract address `(e.g., 0xe7...512)` from the deployment output.
5. Visit the [Arbitrum Quickstart Guide](https://docs.arbitrum.io/for-devs/quickstart-solidity-hardhat#deploy-the-smart-contract-to-your-local-testnet) Interface and paste your contract address into the provided field.

- [x] **Click on "Get cupcake!". This action will prompt you to sign a transaction using Metamask, allowing you to receive a cupcake from the deployed smart contract** 🤠🧁

### Deploy the Smart Contract to the Arbitrum Sepolia Testnet

🔹 **Configure Metamask for Arbitrum Sepolia:**
1. Click Metamask's network selector dropdown, then click "Add Network."
2. Choose "Add a network manually" and provide the following information:
   
     ```
     Network Name: Arbitrum Sepolia
     New RPC URL: https://sepolia-rollup.arbitrum.io/rpc
     Chain ID: 421614
     Currency Symbol: ASPL
     ```
     
🔹 **Update Hardhat Configuration:**
1. Open hardhat.config.js in your project.
2. Locate the line with const `SEPOLIA_TESTNET_PRIVATE_KEY = '';` and replace the empty string with the private key of your test account (e.g., 0xac0..f80).
3. Uncomment the line `accounts: [SEPOLIA_TESTNET_PRIVATE_KEY];`.

     ```
     // hardhat.config.js
     // ...
     const SEPOLIA_TESTNET_PRIVATE_KEY = ''; // <- Replace with the actual private key
     // ...
     accounts: [SEPOLIA_TESTNET_PRIVATE_KEY]; // <- Uncomment this line
     // ...
     ```

🔹 **Acquire Testnet $ETH on L1 Sepolia:**
1. Visit [sepoliafaucet.com](sepoliafaucet.com) to access the L1 Sepolia $ETH faucet.
2. Follow the instructions on the faucet website to request testnet $ETH.
3. Ensure that you have received the testnet $ETH in your L1 Sepolia wallet.

🔹 **Bridge $ETH from L1 Sepolia to Arbitrum L2 and Acquire $ASPL:**
1. Go to the [Arbitrum bridge](https://bridge.arbitrum.io/?destinationChain=arbitrum-sepolia&sourceChain=sepolia).
2. Connect your wallet to the bridge interface.
3. Choose "L1 Sepolia" as the source chain and "Arbitrum" as the destination chain.
4. Enter the amount of $ETH you want to bridge and complete the bridging process.
5. Wait for the bridge confirmation, and make sure the funds are available on Arbitrum L2.
6. After bridging, visit the Arbitrum Sepolia token bridge or a supported exchange to swap your bridged $ETH for $ASPL.
7. Follow the platform's instructions to complete the token swap and ensure that you now have $ASPL tokens in your Arbitrum L2 wallet.

🔹 **Deploy the Smart Contract:**
1. Open a terminal window in your project directory.
2. Run the following command to deploy the smart contract to the Arbitrum Sepolia testnet: `yarn hardhat run scripts/deploy.js --network arbitrumSepolia`
3. You should see output similar to: `Cupcake vending machine deployed to 0xff825139321bd8fB8b720BfFC5b9EfDB7d6e9AB3`
   
> [!NOTE]
> Congratulations! You have successfully deployed business logic and data to Arbitrum Sepolia.

🔹 **View Smart Contract on Blockchain Explorer:**
1. Visit the [Arbiscan Explorer](https://sepolia.arbiscan.io/).
2. Replace `0x...B3` in the URL with the full address of your deployed smart contract to view it.

🔹 **Test the Smart Contract with Metamask:**
1. Open Metamask and select "Arbitrum Sepolia" from the network dropdown.
2. Copy again the contract address `(e.g., 0xe7...512)` from the deployment output.
3. Visit the [Arbitrum Quickstart Guide](https://docs.arbitrum.io/for-devs/quickstart-solidity-hardhat#deploy-the-smart-contract-to-the-arbitrum-sepolia-testnet) interface and paste your contract address into the provided field.
   
- [ ] **Click on "Get cupcake!". This action will prompt you to sign a transaction using Metamask, allowing you to receive a cupcake from the deployed smart contract** 😆🧁

## Contributing
Contributions are welcome! Feel free to open issues or submit pull requests.

## License
This project is licensed under the [MIT License](LICENSE).
