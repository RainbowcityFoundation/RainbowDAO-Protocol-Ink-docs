## Install Rust and the Rust toolchain

#####  1.Install `rustup` by running the following command: 

` curl https://sh.rustup.rs -sSf | sh `

##### 2.Configure your current shell to reload your PATH environment variable so that it includes the Cargo `bin` directory by running the following command: 

` source ~/.cargo/env `

##### 3.Configure the Rust toolchain to default to the latest `stable` version by running the following commands: 

`rustup default stable`

``rustup update`

##### 4. Add the `nightly` release and the `nightly` WebAssembly (`wasm`) targets by running the following commands: 

`rustup update nightly`

`rustup target add wasm32-unknown-unknown --toolchain nightly`

##### 5. Verify your installation by running the following commands: 

`rustc --version`
`rustup show`

## Setup RainbowDao Protocol Node

### 1. Installing The Substrate Contracts Node

 We need to use a Substrate node with the built-in `pallet-contracts` pallet. For this workshop we'll use a pre-configured Substrate node client. 

`cargo install contracts-node --git https://github.com/paritytech/substrate-contracts-node.git --tag v0.3.0 --force --locked`



## Setup Contracts

RainbowDao Protocol Contracts are provided in `https://github.com/RainbowcityFoundation/RainbowDAO-Protocol-Ink-milestone_1.git`. 

It's developed with ink!.

### Get contracts

```
git clone git@github.com:RainbowcityFoundation/RainbowDAO-Protocol-Ink-milestone_1.git
```



## Compile contracts from source code

The RainbowDAO-Protocolprovides script to simplify the contract compilation process while collecting the editing results into a unified directory to facilitate contract deployment and usage. Execute in the project root directory

```
bash ./build.sh
```

All contract compilation results are saved in the release directory.

### Compile  one by one 

##### update version

`cargo install cargo-contract --vers 0.15.0 --force --locked`

##### compile

In RainbowDAO-Protocol-Ink-milestone_1 project 

like cd erc20/        cargo +nightly contract build

erc20 > erc20_factory 

multisig>multisig_factory

role_manage > route_manage >users_manage > kernel > income_category

## Deploy

use `https://polkadot.js.org/apps/` upload target/ink .contract file to deploy contract

or Select the ABI and WASM files that required to deploy contract, click `Upload`, and `Submit and Sign`.



Select the initialization function call, fill in the initialization parameters, set the main contract administrator, and set the contract initial balance, click `Deploy` before set a proper endornment number, normally 500 is enough. Note that the deployment salt is used.

## Initialization

### Initialize main contract

The main contract manages the DAO templates and DAO instantiations. After the main contract is deployed, you need to initialize the template management function of Main, call the init function and set the code hash of the contract template manager.



### Add templates for DAO

For now, DAO templates can only be configured in the tool by calling the `addTemplate` function in the main contract, fill in the creator accountid and the code hash for each components in the template.

For example, we create a erc20_factory template with vault erc20 for the template.

After adding the erc20_factory template, you can create the erc20 through the `RainbowDao protocol frond-end`. Jump to the frontend which is served at `http://localhost:8080/`.



### Creating ERC20

After you create a template, you can create your own DAO from the template that you have set up.

# Setup RainbowDao Protocol Front-end

## Install `Polkadot JS Extension`

Please install `Polkadot JS Extension` before you start. You can get it from here https://polkadot.js.org/extension/

### Get source code

Please get the code from `https://github.com/RainbowcityFoundation/RainbowDAO-Protocol-Ink-UI-milestone_1.git`

```
git clone https://github.com/RainbowcityFoundation/RainbowDAO-Protocol-Ink-UI-milestone_1.git
```

### Config front-end

Please find the correct address for `` src/api/connectContract.js ``, and update the correct address in   ``` src/api/connectContract.js ```. And replace `src/api/httpConfig.js connectPath` to your connect path.

it should be `ws://127.0.0.1:9944` by default.

Please find the correct contractHash for `` src/utils/contractHash.json ``, and update the correct address in   `src/utils/contractHash.json`.

### Install dependencies

Run `npm install` to install packages needed for this App.

### Start front-end

`npm run serve` runs the app in the development mode.
Open http://localhost:8080 to view it in the browser.



## Way 2: Use the online version front-end test  deployed contract

##### entrance:

`https://www.rainbowdao.io/polkadot`

## Install `Polkadot JS Extension`

Please install `Polkadot JS Extension` before you start. You can get it from here https://polkadot.js.org/extension/

##### Get gas from ALICE

In `https://polkadot.js.org/apps` Account page, use account  send gas to your extension account.

##### Then

You can use `https://www.rainbowdao.io/polkadot` to create token/multisign wallet.  Test  Protocol Management.



