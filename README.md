# Simple Fund Me Contract

Example Eth Brownie project that can be deploy on dev network, rinkeby and mainnet fork .

## Env variables

Create .env file from .env-local 

```
cp .env-local .env
```

PRIVATE_KEY - your eth private key, get it on metamask/ganache

WEB3_INFURA_PROJECT_ID - create a project in Infura then get the project id
[https://infura.io](https://infura.io)

ETHERSCAN_TOKEN -  get api key on etherscan.io to programatically verified your smart contract upon deploying on testnet and mainnet
[https://etherscan.io](https://etherscan.io)

## Add ganache network to Brownie's Ethereum networks to generate build codes 

```
brownie networks add Ethereum ganache-local host=http://0.0.0.0:8545 chainid=1337
```

Open your ganache app to know the required details for host and chainid

```
brownie run scripts/deploy.py -—network ganache-local
```

## Two ways to add custome brownie mainnet for
### Infura
```
brownie networks add development mainnet-fork-dev cmd="ganache-cli" host=http://127.0.0.1 fork=‘https://mainnet.infuro.io/v3/$WEB3_INFURA_PROJECT_ID' accounts=10 mnemonic=brownie port=8545
```

### Alchemy

```
brownie networks add development mainnet-fork-dev cmd=“ganache-cli” host=http://127.0.0.1 fork=‘https://eth-mainnet.alchemyapi.io/v2/1YmrU5Y9l0yfws6pS-uJLKxE-pmLsuCV’ accounts=10 mnemonic=brownie port=8545
```

## Brownie Commands

Compile smart contract

```
brownie compile
```

Deploy to chosen network

```
brownie run scripts/deploy.py
brownie run scripts/deploy.py —-network rinkeby
brownie run scripts/deploy.py —-network mainnet-fork-dev
```

