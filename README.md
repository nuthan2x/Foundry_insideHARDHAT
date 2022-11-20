# Use Foundry in an existing Hardhat project
Suppose that you already have a Hardhat project with some dependencies such as @OpenZeppelin/contracts in directory node_modules/.

You can use Foundry test in this project in 4 steps.

Before we start, let's take a look at the directories:

Contracts are in contracts
Hardhat unit test is in test, and we will put Foundry test files in test/foundry
Hardhat puts its cache in cache, and we will put Foundry cache in forge-cache
4 steps to add Foundry test
Copy lib/forge-std from a newly-created empty Foundry project to this Hardhat project directory. A note: you can also run forge init --force to init a Foundry project in this non-empty directory and remove unneeded directories created by Foundry init.
Copy foundry.toml configuration to this Hardhat project directory and change src, out, test, cache_path in it:

[profile.default]
src = 'contracts'
out = 'out'
libs = ['node_modules', 'lib']
test = 'test/foundry'
cache_path  = 'forge-cache'

# See more config options https://book.getfoundry.sh/reference/config.html
Create a remappings.txt to make Foundry project work well with VS Code Solidity extension:

forge remappings > remappings.txt - You will need to re-run this every time you modify libraries in Foundry/ add new node_modules.

ds-test/=lib/forge-std/lib/ds-test/src/
forge-std/=lib/forge-std/src/
See more on remappings.txt and VS Code Solidity extension: Remapping dependencies, Integrating with VSCode

Make a sub-directory test/foundry and write Foundry tests in it.
Let's put the sample test file Contract.t.sol in this directory and run Foundry test


forge test
Now, Foundry test works in this existing Hardhat project. As the Hardhat project is not touched and it can work as before.

# finnaly

1. npm init -y

2. npm i --save -dev hardhat

3. npx hardhat (choose js and add all libraries recommended by this and when npx hardhat test is ran) 

4. add remappings.txt

5. forge remappings > remappings.txt

6. copy paste lib, foundry.toml from other foundry project to current directory

7. create folder named foundry inside test folder ( test/foundry) and write foundry tests inside them

8. forge test







# Sample Hardhat Project

This project demonstrates a basic Hardhat use case. It comes with a sample contract, a test for that contract, and a script that deploys that contract.

Try running some of the following tasks:

```shell
npx hardhat help
npx hardhat test
REPORT_GAS=true npx hardhat test
npx hardhat node
npx hardhat run scripts/deploy.js
```
