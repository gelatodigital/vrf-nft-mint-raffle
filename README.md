# VRF NFT Mint Raffle

A smart contract implementation for conducting fair and transparent NFT raffles using Gelato's Verifiable Random Function (VRF) service.

## Overview

This contract allows NFT project creators to conduct verifiably random raffles among NFT holders. It uses Gelato's VRF service to ensure that winner selection is provably fair and cannot be manipulated.

## Features

- **Verifiable Randomness**: Uses Gelato VRF to generate provably fair random numbers
- **Configurable Winners**: Set the number of winners to be selected in the raffle
- **Flexible Timing**: Configure when the minting period ends and when the raffle can be executed
- **Owner Controls**: Only the contract owner can initiate the raffle and change parameters
- **Transparent Results**: All winning token IDs and their owners are publicly accessible

## Smart Contract

The `NFTRaffle` contract implements the raffle logic by extending the abstract `GelatoVRFConsumerBase` contract which provides the interface for consuming randomness from Gelato VRF. The implementation is entirely contained within this single Solidity file.

## Usage

1. Deploy the NFTRaffle contract with:
   - The address of the NFT contract
   - The address of the Gelato VRF operator
   - A timestamp for when minting is considered complete

2. Once minting is complete (after the specified timestamp), the owner can call `startRaffle()` to request randomness from Gelato VRF.

3. When Gelato VRF fulfills the randomness request, the contract automatically selects winners based on the provided random number.

4. After the raffle is complete, anyone can view the results using:
   - `getWinningTokenIds()`: Returns an array of winning token IDs
   - `getWinningAddresses()`: Returns an array of addresses that own the winning tokens
   - `getRaffleResults()`: Returns both winning token IDs and their owners

## Security Considerations

- The contract implements proper access controls to ensure only authorized parties can initiate the raffle
- The randomness provided by Gelato VRF ensures the selection process is fair and cannot be manipulated
- Error handling is implemented to gracefully handle edge cases


## ⚠️ Security Warning ⚠️

**IMPORTANT**: This contract has not undergone a comprehensive security audit by a professional auditing firm. It is provided as-is without any warranties or guarantees.

- **NOT PRODUCTION READY**: This code should not be used in production without a thorough security audit.
- **USE AT YOUR OWN RISK**: Any use of this contract for managing real assets is done at your own risk.
- **AUDIT RECOMMENDED**: Before deploying to a production environment or using with valuable assets, it is strongly recommended to:
  1. Have the code professionally audited by a reputable smart contract auditing firm
  2. Conduct thorough testing on testnets
  3. Implement proper monitoring and emergency procedures

The developers assume no liability for any losses incurred from using this code.
