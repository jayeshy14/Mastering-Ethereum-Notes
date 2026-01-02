# Ethereum Basics

This chapter introduces the fundamental concepts required to interact with Ethereum: currency units, wallets, networks, and the basics of smart contracts.

## Ether Currency Units

Ethereum's currency is **Ether** (ETH). It is subdivided into smaller units, the smallest being **Wei**.

- **Ethereum vs. Ether:** Ethereum is the system; Ether is the currency.
- **Internal Representation:** The EVM processes all values as integers in Wei.

### Common Denominations

| Common Name | SI Name | Value (Wei) | Description |
| :--- | :--- | :--- | :--- |
| **Wei** | Wei | $1$ | The smallest atomic unit |
| **Gwei** | Gigawei | $10^9$ | Used to calculate Gas prices |
| **Ether** | Ether | $10^{18}$ | The base unit of currency |

## Wallets

A **wallet** is a software application that manages your Ethereum account. It serves as a gateway to the Ethereum system, holding your keys and creating/broadcasting transactions.

### Control and Responsibility

- **Private Keys:** Control access to funds and smart contracts. One private key = One account.
- **Mnemonic Phrase:** A 12-24 word sequence used to back up and recover private keys (seed phrase).
- **Security Best Practices:**
    - Never store private keys or seed phrases digitally.
    - Use physical paper backups stored securely.
    - Losing the private key means losing the funds forever (no central reset).

### Wallet Implementations

- **MetaMask:** Browser extension and mobile wallet; standard for interacting with dApps.
- **Hardware Wallets:** Physical devices that provide the highest security by keeping keys offline.

## Ethereum Networks

Wallets can connect to different networks. The address and private key remain the same across networks, but the balances and state are distinct.

- **Mainnet:** The main public Ethereum blockchain. Real value, real consequences.
- **Sepolia:** A Proof-of-Stake (PoS) testnet. Mirrors mainnet environment but uses worthless test-ETH.
- **Holesky:** Testnet focused on infrastructure and staking protocol development.
- **Localhost:** A private blockchain node running locally on your machine for development (e.g., Anvil, Hardhat).

## Accounts

There are two distinct types of accounts in Ethereum:

### 1. Externally Owned Accounts (EOA)
- Controlled by a **private key**.
- Can initiate transactions.
- Costs Gas to send transactions.
- Example: Your MetaMask wallet.

### 2. Contract Accounts
- Controlled by **smart contract code**.
- **No private key**; owned by the logic of the code.
- Cannot initiate transactions (can only react to incoming transactions).
- Has an address and a balance, just like an EOA.

## Transactions and Gas

Transactions are messages that change the state of the Ethereum network.

- **Gas:** The fee paid to the network to process a transaction.
- **Gas Limit:** The maximum amount of computation a transaction is allowed to consume (Basic transaction = 21,000 gas).
- **Gas Price:** The cost per unit of gas, usually measured in **Gwei**.
- **Formula:** $Total Cost = Gas Used \times Gas Price$

## Introduction to Smart Contracts

A Smart Contract is a program that runs on the Ethereum Virtual Machine (EVM).

- **EVM:** A global singleton computer; every node runs a local copy to validate execution.
- **Solidity:** The most popular high-level language for writing smart contracts.
- **compilation:** Solidity code is compiled into **Bytecode** (machine-readable instructions) for the EVM.

### Life Cycle of a Contract
1. **Write:** Code the logic in Solidity (`.sol`).
2. **Compile:** Convert to EVM bytecode.
3. **Deploy:** Send a special transaction (with no recipient address) containing the bytecode. This creates the contract on-chain and generates a specific **Contract Address**.
4. **Interact:** Users or other contracts send transactions to this address to trigger functions.

### Example: A Simple Faucet Contract

A basic contract that holds funds and allows users to withdraw a limited amount.

```solidity
pragma solidity 0.8.26;

contract Faucet {
    // Function to give out ether
    function withdraw(uint256 _amount, address payable _to) public {
        // 1. Check Precondition (Limit withdrawal)
        require(_amount <= 1000000000000);

        // 2. Perform Action (Transfer ETH)
        _to.transfer(_amount);
    }

    // Fallback/Receive functions to accept incoming Ether
    receive() external payable {}
    fallback() external payable {}
}