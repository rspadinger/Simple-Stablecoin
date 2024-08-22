# Simple Stablecoin

## Requirements

-   [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
-   [foundry](https://getfoundry.sh/)

## Install dependencies

rm -rf lib

forge clean

forge install smartcontractkit/chainlink-brownie-contracts@0.6.1 foundry-rs/forge-std@v1.5.3 openzeppelin/openzeppelin-contracts@v4.8.3 cyfrin/foundry-devops@0.1.0 --no-commit

## Start a local node

anvil

## Deploy

### Set environment variables:

PRIVATE_KEY="ac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80"
DEFAULT_ANVIL_KEY="ac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80"

echo $DEFAULT_ANVIL_KEY

forge script script/DeployDSC.s.sol:DeployDSC --rpc-url http://localhost:8545 --private-key $DEFAULT_ANVIL_KEY --broadcast

forge script script/DeployDSC.s.sol:DeployDSC --rpc-url sepolia --private-key $PRIVATE_KEY --broadcast --etherscan-api-key sepolia --verify -vvvv

## Testing

forge test

forge coverage --report debug > coverage-report.txt
