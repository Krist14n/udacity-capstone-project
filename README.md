# Udacity Blockchain Capstone

The capstone will build upon the knowledge you have gained in the course in order to build a decentralized housing product. 

## Install

`npm install`

## Compile

`cd` into `eth-contracts/` directory and execute:

`truffle compile`

## Test

Execute:

`truffle test test/TestERC721Mintable.js`  
`truffle test test/TestSquareVerifier.js`  
`truffle test test/TestSolnSquareVerifier.js`  

or 

`truffle test` to run all tests 


## ZoKrates (generate zk-Snarks Validator)

#### Step 1: Run ZoKrates in Docker
``` 
docker run -v <path to your project folder>:/home/zokrates/code -ti zokrates/zokrates:0.3.0 /bin/bash
```

#### Change directory
``` 
cd code/zokrates/code/square/
``` 

#### Step 2: Compile the program written in ZoKrates DSL
``` 
../../../../zokrates compile -i square.code
``` 

#### Step 3: Generate the Trusted Setup
``` 
../../../../zokrates setup
```

#### Step 4: Compute Witness
``` 
../../../../zokrates compute-witness -a 3 9
```

#### Step 5: Generate Proof
```
../../../../zokrates generate-proof
```

#### Step 6: Export Verifier
```  
../../../../zokrates export-verifier
```

# Deploy to Rinkeby

To deploy the contract, get an Infura API key, and deploy with Truffle:

Update <**your infura key**> and <**your metamask seed**> in 
`/eth-contracts/truffle-config.js` before migrate to Rinkeby Network. 

Run:

`truffle deploy --network rinkeby`

for more information look at: https://docs.opensea.io/docs/1-structuring-your-smart-contract#section-deploying-your-contract

After deploy:

`Token: 0x1637C2f66B26EA5e69e25384Dce1c4648BEE8EC0`
`Verifier:  0xc494d91825b5FA03f10D4B0aa406a17A2543FBF9`

## ABI's 

Contracts ABI's can be found at:
`eth-contracts/build/contracts/SolnSquareVerifier.json`
`eth-contracts/build/contracts/SquareVerifier.json`
`eth-contracts/build/contracts/Verifier.json`

## Mint tokens

After deploying to the Rinkeby network, there will be a contract on Rinkeby that will be viewable on Rinkeby Etherscan (0x1637C2f66B26EA5e69e25384Dce1c4648BEE8EC0). You can find the address of the deployed contract in the output of the deployment command and find it on Etherscan by hitting the URL: https://rinkeby.etherscan.io/address/0x1637C2f66B26EA5e69e25384Dce1c4648BEE8EC0.

 You should set this contract address and the address of your MetaMask account as environment variables when running the minting script:

```
export OWNER_ADDRESS="<my_address>"
export NFT_CONTRACT_ADDRESS="<deployed_contract_address>"
node scripts/mint.js
```

for more information look at: https://docs.opensea.io/docs/1-structuring-your-smart-contract#section-minting-your-tokens

After mint is complete your OpenSea exchange should list items:

https://rinkeby.opensea.io/category/realestateexchangev5

# Project Resources

* [Remix - Solidity IDE](https://remix.ethereum.org/)
* [Visual Studio Code](https://code.visualstudio.com/)
* [Truffle Framework](https://truffleframework.com/)
* [Ganache - One Click Blockchain](https://truffleframework.com/ganache)
* [Open Zeppelin ](https://openzeppelin.org/)
* [Interactive zero knowledge 3-colorability demonstration](http://web.mit.edu/~ezyang/Public/graph/svg.html)
* [Docker](https://docs.docker.com/install/)
* [ZoKrates](https://github.com/Zokrates/ZoKrates)

