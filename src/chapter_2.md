# Ethereum Basics

## Ether Currency Units

Ethereum's currency unit is called ether, identified also as ETH or with the symbols Ξ (from the Greek letter Xi that looks like a stylized capital E) or, less often, ♦: for example, 1 ether, 1 ETH, Ξ1, or ♦1.

>Tip: Use Unicode characters U+039E for Ξ and U+2666 for ♦.

### Table 2-1. Ether denominations and unit names**

| Value (in wei) | Exponent | Common name | SI name |
|---|---|---|---|
| 1 | 1 | Wei | Wei |
| 1,000 | 10^3^ | Babbage | Kilowei or femtoether |
| 1,000,000 | 10^6^ | Lovelace | Megawei or picoether |
| 1,000,000,000 | 10^9^ | Shannon | Gigawei or nanoether |
| 1,000,000,000,000 | 10^12^ | Szabo | Microether or micro |
| 1,000,000,000,000,000 | 10^15^ | Finney | Milliether or milli |
| *1,000,000,000,000,000,000* | *10^18^* | *Ether* | *Ether* |
| 1,000,000,000,000,000,000,000 | 10^21^ | Grand | Kiloether |
| 1,000,000,000,000,000,000,000,000 | 10^24^ | | Megaether |

## Externally Owned Accounts and Contracts

- Externally Owned Account: An EOA is basically a type of account on the Ethereum network that’s controlled by a person using a private key.
- Contract Account: A contract account has smart contract code, a contract account does not have a private key. Instead, it is owned (and controlled) by the logic of its smart contract code: the software program recorded on the Ethereum blockchain at the contract account's creation and executed by the EVM.

> Note: Because a contract account does not have a private key, it cannot initiate a transaction.