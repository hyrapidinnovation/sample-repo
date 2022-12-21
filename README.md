# JungleNFT Marketplace

A digital marketplace for crypto collectables and non-fungible tokens (NFTs). Buy, sell, and discover exclusive digital items.

## Project Description

The platform will be an NFT marketplace that will allow users to explore different NFTs available on the platform. It will enable users to create and sell their own NFTs on the platform. Users will be able to buy and sell NFTs by using fixed-price or auction functions on the platform. This platform enables users to create and mint their own NFTs by uploading their files or connecting with Instagram.  

It uses the concept of lazy minting. The NFTs are created off-chain and minted on-chain later, at the time of sale/transfer.  
This platform uses the Wyvern Protocol, to facilitate the exchange/buy/sell of NFTs.

## Contract Used

* AssetContractShared
    * This is the main NFT contract of the platform from which all the NFTs created on the Jungle platform will be minted and transferred. 
    * Supports Lazy minting at the time of transfer. 
    * Supports EIP712 for MetaTransactions.
    * Supports EIP2981 for royalty. <br/><br/>

* Exchange Contract 
    * All sales happen through this contract. When an NFT is listed, a signature is created by the user, and that signature is verified in the contract and the NFT sale is executed.
    * Supports Fixed Price Sale, Dutch Auction, English Auction.  
    * Supports EIP712 for MetaTransactions.

<br/>

* TokenTransferProxy Contract 
    * The user will be approving this contract only for the first time, to eliminate the gas fee for future transactions for ERC20 token transfers.

<br/>

* ProxyRegistry Contract 
    * The user will be initializing the contract only for the first time to communicate with the exchange contract on behalf of the user.
    * Supports EIP712 for MetaTransactions.

<br/>

* MerkleValidator Contract 
    * To verify and transfer NFTs from seller to buyer.

<br/>

* Atomicizer Contract 
    * To decode and execute bundle sale. It can transfer differen type of NFTs from diferent NFT contracts in one transaction.

<br/>

* Relayer Contract 
    * This contract acts as a User to buy NFTs on behalf of Jungle users
       and automatically transfer it to the user in the same transaction.

<br/>


## Deployed Contracts

* Currently deployed on **Rinkeby**, **Goerli**, and **Mumbai** chain.
* To be deployed on **Ethereum** and **Polygon** chain.

| Contract | Address |  
| --- | --- |  
|WyvernProxyRegistry | [0xfe2A0F0196E0c9E4F6ec606Aba273581dA7f32f8](https://goerli.etherscan.io/address/0xfe2A0F0196E0c9E4F6ec606Aba273581dA7f32f8)|  
|WyvernTokenTransferProxy | [0x13A0DFf0B5401dDB8F972Dda8F37A4F3db14cD77](https://goerli.etherscan.io/address/0x13A0DFf0B5401dDB8F972Dda8F37A4F3db14cD77)|  
|NFT Contract | [0xAfB2DfEcc7F4A193b8a28CE0AB0D90BD411BC171](https://goerli.etherscan.io/address/0xAfB2DfEcc7F4A193b8a28CE0AB0D90BD411BC171)|  
|WyvernExchangeWith  | [0x06fda5DdD566e4C543CD06dE862061EAfab0231a](https://goerli.etherscan.io/address/0x06fda5DdD566e4C543CD06dE862061EAfab0231a)|  
|WyvernAtomicizer | [0x500f26FF68fe8D15fab5b25CF5936CD9dC28c44D](https://goerli.etherscan.io/address/0x500f26FF68fe8D15fab5b25CF5936CD9dC28c44D)|  
|MerkleValidator | [0x124F0BfF12Efc731908f9a4D92d3bac6C75b40cd](https://goerli.etherscan.io/address/0x124F0BfF12Efc731908f9a4D92d3bac6C75b40cd)|  
|JungleRelayer | [0xac79E8EfCFB4af86C6747Bb6C85713Fe2ae9D602](https://goerli.etherscan.io/address/0xac79E8EfCFB4af86C6747Bb6C85713Fe2ae9D602)|  

## Installation

These instructions will get you a local copy of the project up and running on your local machine for development and testing purposes.
Clone the git repo.

```
git clone https://github.com/JungleMarketplace/smart-contracts.git
```

Install dependencies.

```
cd smart-contracts
npm install
```


Setup an env file by replicating env.example with valid values


* PRIVATE_KEY 
    * The private key which will be used for deployment. It must hold Native tokens(ETH/Matic) depending on which chain the deployment is being done)

    * The address corresponding to this private key will be the owner, and this address will also be set as the Fee recipient in NFT contract to receive Platform Minting fee and Royalty fee
    
<br/>

* ETHEREUM_MAINNET_URL
    * RPC URL for Ethereum Mainnet 
    
<br/>

* MATIC_MAINNET_URL
    * RPC URL for Matic Mainnet
    
<br/>

* RINKEBY_URL
    * RPC URL for Rinkeby Testnet
    
<br/>

* MUMBAI_URL
    * RPC URL for Mumbai Testnet
    
<br/>

* GOERLI_URL
    * RPC URL for Goerli Testnet
    
<br/>

* ETHERSCAN_API_KEY
    * API KEY for Etherscan used for verification
    
<br/>

* POLYGONSCAN_API_KEY
    * API KEY for Polygonscan used for verification
    
<br/>

* NFT_NAME 
    * Name for NFT Contract (e.g. Jungle-NFT)
    
<br/>

* NFT_SYMBOL
    * Symbol for NFT Contract (e.g. JUNGLE)
    
<br/>

* PLATFORM_MINTING_FEE
    * Platform Minting fee to be set in NFT contract in basis points. (e.g. 250 for 2.5%)
    * Multiply percentage by 100 to get in basis points. Supports only upto 2 decimal places.
    * Should be less than 10000 (100%)
    
<br/>

* RELAYER_FEES
    * Relayer Fees to be charged while selling other platform NFTs. (e.g. 50 for 0.5%)
    * Multiply percentage by 100 to get in basis points. Supports only upto 2 decimal places.
    * Should be less than 10000 (100%)

<br/>

* RELAYER_CASHBACK
    * Cashback to be given while selling other platform NFTs. (e.g. 50 for 0.5%)
    * Multiply percentage by 100 to get in basis points. Supports only upto 2 decimal places.
    * Should be less than 10000 (100%)

<br/>

* DEFAULT_FEE_CONTROLLER
    * The Address that can control/modify the different fees on the platform.

<br/>

* FULLFILLBASICORDER_SIG
    * Function Signature of FullfilBasicOrder() from Seaport contract.

<br/>

* SEAPORT_ADDRESS
    * Seaport contract address for OpenSea.

<br/>

* SEAPORT_APPROVAL_ADDRESS
    * Address to give ERC20 approval to Seaport contract address for OpenSea.

<br/>

* FEE_RECIPIENT
    * The Address that will recieve the royalty fee.

<br/>

* VERIFY_CONTRACTS
    * To verify all contracts on explorer, set it to true
    
    
<br/>

### Running Test Cases

Compile and test the contracts by running the following commands.

```
npx hardhat compile
npx hardhat test
```

### Generating Test Case Coverage Report

Compile, test and generate coverage report for the contracts by running the following commands.

```
npx hardhat coverage --solcoverjs /.solcover.js
```

### Deploying Smart Contracts

Compile and deploy the contracts by running the following commands.

```
npx hardhat compile
```

For Ethereum Mainnet

```
npx hardhat run scripts/deploy.js --network ethereum
```

For Matic Mainnet

```
npx hardhat run scripts/deploy.js --network matic
```

For Rinkeby Testnet

```
npx hardhat run scripts/deploy.js --network rinkeby
```

For Mumbai Testnet

```
npx hardhat run scripts/deploy.js --network mumbai
```

For Goerli Testnet

```
npx hardhat run scripts/deploy.js --network goerli
```

For Local deployment

```
npx hardhat run scripts/deploy.js
```

### Verifing contracts on explorers  

NETWORK can be ethereum, matic

Verify Proxy Registry Contract
```
npx hardhat verify --contract contracts/WyvernProxyRegistry.sol:WyvernProxyRegistry <CONTRACT_ADDRESS> --network <NETWORK>
```

Verify Token Transfer Proxy Contract
```
npx hardhat verify --contract contracts/WyvernTokenTransferProxy.sol:WyvernTokenTransferProxy <CONTRACT_ADDRESS> --network <NETWORK>
```
Verify AssestContractShared Contract
```
npx hardhat verify --contract contracts/AssetContractShared.sol:AssetContractShared <CONTRACT_ADDRESS> --network <NETWORK>
```
Verify WyvernExchange Contract
```
npx hardhat verify --contract contracts/WyvernExchange.sol:WyvernExchangeWithBulkCancellations <CONTRACT_ADDRESS> --network <NETWORK>
```
Verify WyvernAtomicizer Contract
```
npx hardhat verify --contract contracts/WyvernAtomicizer.sol:WyvernAtomicizer <CONTRACT_ADDRESS>  --network <NETWORK>
```
Verify MerkleValidator Contract
```
npx hardhat verify --contract contracts/MerkleValidator.sol:MerkleValidator <CONTRACT_ADDRESS>  --network <NETWORK>
```
Verify JungleRelayer Contract
```
npx hardhat verify --contract contracts/JungleRelayer.sol:JungleRelayer <CONTRACT_ADDRESS> --network <NETWORK>
```

## Technology & Standards Used

* Wyvern Protocol
* Solidity
* Ethereum
* Polygon
* Hardhat
* ERC1155
* EIP712
* EIP2981
