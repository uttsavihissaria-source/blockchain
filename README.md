# Task 1: SavingsBank Smart Contract

## Overview
This project implements a **SavingsBank** smart contract on the Ethereum blockchain. It functions as a personal digital vault, allowing the contract owner to store Ether securely while permitting deposits from any external address.

This contract demonstrates fundamental Solidity concepts including:
* State variables and visibility.
* Constructors for initialization.
* Access control (`require` statements).
* `payable` functions for handling Ether.

## Features
* **Ownership Assignment:** The account that deploys the contract is automatically assigned as the `owner`.
* **Public Deposits:** Any user or contract can deposit Ether into the SavingsBank.
* **Restricted Withdrawals:** Only the `owner` can withdraw funds. Attempts by other addresses will revert with an "Access Denied" error.
* **Balance Tracking:** View the current Ether balance held within the contract.

## Technical Details
* **Solidity Version:** `^0.8.0`
* **License:** MIT (Implied/Open)

## Contract Functions

### 1. `constructor()`
* Initializes the contract.
* Sets `msg.sender` as the `owner`.

### 2. `deposit()`
* **Type:** `public payable`
* Allows the contract to receive Ether. The value sent with the transaction is added to the contract's balance.

### 3. `withdraw(uint _amount)`
* **Type:** `public`
* **Parameters:** `_amount` (in Wei).
* Allows the owner to transfer Ether from the contract to their wallet.
* **Checks:**
    1.  Is the caller the owner?
    2.  Does the contract have sufficient balance?

### 4. `getBalance()`
* **Type:** `public view`
* Returns the current balance of the contract in Wei.

## Security Considerations
* This contract uses `transfer()` for withdrawals. For production environments handling complex interactions, `call{value: amount}("")` is recommended to prevent gas limit issues with smart contract wallets.
