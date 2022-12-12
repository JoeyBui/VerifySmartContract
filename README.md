# Deploy & Verify Smart Contract (Hardhat)

Faucet: 

https://faucets.chain.link/goerli

## Steps

### 1. Create new project

`mkdir new_project`

`cd new_project`

### 2. Install and Init Hardhat

`npm install --save-dev hardhat`

`npx hardhat`

### 3. Add network configuration


Goerli

Create an Infura account and create new project: https://infura.io

Export private key from MetaMask:
https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key

#### File: `hardhat.config.js`
```
module.exports = {
  solidity: "0.8.4",

  networks: {
    goerli: {
      url: "https://goerli.infura.io/v3/YOUR_PROJECT_ID",
      accounts: [metamask_private_key],
    },
    mainnet: {
      url: "https://mainnet.infura.io/v3/YOUR_PROJECT_ID",
      accounts: [metamask_private_key],
    },
  },
  
}
```


### 4. Deploy onto target network (Goerli)

Goerli

`npx hardhat run scripts/sample-scripts.js --network Goerli`

Mainnet (REAL ETH)

`npx hardhat run scripts/sample-scripts.js --network mainnet`

### 5. Verify and Publish

https://hardhat.org/plugins/nomiclabs-hardhat-etherscan.html

`npm install --save-dev @nomiclabs/hardhat-etherscan`

Add this to `hardhat.config.js`
```
require("@nomiclabs/hardhat-etherscan");
```

Add Etherscan API Key: https://etherscan.io/

```
module.exports = {
  networks: {
    mainnet: { ... }
  },
  etherscan: {
    // Your API key for Etherscan
    // Obtain one at https://etherscan.io/
    apiKey: "YOUR_ETHERSCAN_API_KEY"
  }
};
```

Verify contract:

`npx hardhat verify --network mainnet DEPLOYED_CONTRACT_ADDRESS "Constructor argument 1"`


