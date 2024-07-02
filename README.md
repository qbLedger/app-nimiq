# Nimiq app for the Ledger Nano S and Ledger Nano X

## Introduction

This is a wallet app for the [Ledger Nano S](https://www.ledgerwallet.com/products/ledger-nano-s) and [Ledger Nano X](https://shop.ledger.com/pages/ledger-nano-x) that makes it possible to store your [Nimiq](https://nimiq.com/)-based assets on those devices.

A companion [Javascript library](https://github.com/LedgerHQ/ledgerjs) is available to communicate with this app.

To learn how to use this library you can take look at the [demo project](https://github.com/jeffesquivels/ledgerjs-nimiq).

## Building and installing

To build and install the app on your Nano S or Nano X you must set up the Ledger Nano S or X build environment. Please follow the Getting Started instructions at the [Ledger Nano S github repository](https://github.com/LedgerHQ/ledger-nano-s).

Alternatively, you can set up the Vagrant Virtualbox Ledger environment maintained [here](https://github.com/fix/ledger-vagrant). This sets up an Ubuntu virtual machine with the Ledger build environment already set up. Note that if you are on a Mac, at the time of this writing this seems to be the only way to build and load the app.

The command to compile and load the app onto the device is:

```$ make load```

To remove the app from the device do:

```$ make delete```

## Testing

The `./unit-tests` directory contains files for testing the transaction parser and some printing utilities. To build and execute the tests run `./test.sh`. They are currently outdated though.

## Key pair validation

The operation to retrieve the public key implements an optional keypair verification method. Along with the request to retrieve the public key a small message is sent that is to be signed by the device. Back on the host the returned signature can be checked against the returned public key. This is to guard against incompatibility between the keypairs generated by the Ledger device and the ones expected by the Nimiq network, whatever the reason for this might be. The extra precaution prevents users from sending funds to an address they are not able to sign transactions for.
