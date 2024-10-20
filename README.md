# DAML Smart Contract (Cash Contract)

## Description: 
The Cash smart contract is built using DAML (Digital Asset Modeling Language) and represents a digital cash asset with functionalities for transferring ownership, updating the exchange rate, and swapping currency values based on an exchange rate. This contract can be utilized in a decentralized finance or trading platform where different parties interact with digital cash assets.

## Structure
### Template: Cash
### Fields:

**amount:** Decimal - The amount of cash.
**currency:** Text - The currency type (e.g., USD, GBP).
**issuer:** Party - The party that issues the cash.
**holder:** Party - The party holding the cash.
**exchange:** Party - The exchange party responsible for currency exchange.
**exchangeRate:** Decimal - The rate used for converting the currency.
**Parties:**

**signatory:** The issuer of the cash.
**observer:** The exchange party.
**Ensure:**

The amount must be greater than zero.
Controllers and Actions
Controller: issuer

Transfer:** Allows the issuer to transfer the ownership of the Cash contract to a new holder.
**Input:**
**newHolder:** The party who will become the new holder.
**Output:** A new Cash contract instance with the holder updated.
**Controller:** holder

**UpdateExchangeRate:** Allows the holder to update the exchange rate for the cash.
**Input:**
**newExchangeRate:** The new exchange rate value.
**Output:** A new Cash contract instance with the exchangeRate updated.
**Controller:** exchange

**Swap:** Allows the exchange party to swap the currency and update the amount based on the new exchange rate.
**Input:**
**newcurrency:** The new currency type.
**newExchangeRate:** The new exchange rate, which must be greater than 1.0.
**Output:** A new Cash contract instance with the currency, amount, and exchangeRate updated.

## Test Script (test)
A script (test) is provided to simulate the interactions between different parties (issuer, holder, and exchange) with the Cash contract. The script includes the following steps:

## Party Allocation:

Allocate party1 as the issuer.
Allocate party2 as the holder.
Allocate party3 as the exchange.


## Contract Creation:

The Cash contract is created by party1 with the following details:
amount: 100.0
currency: "USD"
issuer: party1
holder: party2
exchange: party3
exchangeRate: 0.0

## Transfer Ownership:

party1 (issuer) transfers the ownership of the contract to party2 (holder) using the Transfer choice.
Update Exchange Rate:

party2 (holder) updates the exchange rate to 1.2 using the UpdateExchangeRate choice.
Currency Swap:

party3 (exchange) swaps the currency to "GBP" and updates the exchange rate to 1.5 using the Swap choice.

## Setup and Configuration
DAML.yaml File Details:

**SDK Version:** 1.15.0
**Name:** test
**Source Directory:** daml
**Initialization Script:** Main:cwTest
**Version:** 1.0.0
**Dependencies:**
daml-prim
daml-stdlib
daml-script

**Notes:**
The Cash contract enforces that the amount must be greater than zero.
The Swap choice ensures the new exchange rate must be greater than 1.0 to perform the currency conversion.
The provided script (test) demonstrates a full lifecycle of interactions between different parties to validate the functionality of the Cash template.
This README provides an overview and understanding of how to work with and test the Cash smart contract in the project. Make sure to run the script in a DAML environment with appropriate configurations as per the daml.yaml file.
