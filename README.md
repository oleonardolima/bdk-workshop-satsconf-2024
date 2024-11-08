# SATSCONF 2024 - BDK Workshop

## What's new in BDK 1.0

* `bdk_wallet` crate built on new `bdk_chain` crate
  * `bdk_chain` monotone block data tracking functions, minimal dependencies
  * `bdk_wallet` handles higher level transaction monitoring, building and signing
  * can build unique wallet and non-wallet apps directly on `bdk_chain`
  * improved `no-std` support
  * built on latest `rust-bitcoin` (0.32) and `rust-miniscript` (12.0)

* Decoupled data syncing and storage crates from `bdk_wallet` and `bdk_chain`
  * can sync and read/write wallet and chain data with async or blocking methods
  * sync and store crates only need to implement simple traits
  * able use async or blocking I/O

* Improved blockchain sync clients
  * better electrum and esplora client performance and error handling
  * experimental block-by-block core RPC client
  * experimental compact block filter client based on `kyoto`

* Improved wallet and chain data stores
  * blocking SQLite store based on `rusqlite`
  * experimental async PostgreSQL and SQLite `sqlx` based stores
  * experimental blocking flat file based store

## Purpose of Workshop

The purpose of this workshop is to demonstrate how to build a simple, pure Rust [bdk-wallet 1.0](https://github.com/bitcoindevkit/bdk/releases) based app using the [Axum](https://github.com/tokio-rs/axum) web framework, the [rust-esplora-client](https://github.com/bitcoindevkit/rust-esplora-client) blockchain client, and a SQLite embedded database.

## Quick Start ⚡

### Setup

1. [Git](https://github.com/git-guides/install-git)
2. [Rust](https://www.rust-lang.org/tools/install)
3. [SQLite](https://medium.com/@techwithjulles/part-5-how-to-install-sqlite-on-your-machine-windows-linux-and-mac-simple-version-f05b7963b6cd)
4. Editor (eg. [RustRover](https://www.jetbrains.com/rust/), *Vim, [VSCode](https://code.visualstudio.com/docs/languages/rust), [Zed](https://zed.dev/), etc.)

### Build/Run 🏗️

1. Clone this repo
   ```
   git clone git@github.com:oleonardolima/bdk-workshop-satsconf-2024.git
  . Build & Run
   ```
   cd bdk-workshop-satsconf-2024
   cargo
1. Change DB file URL (optional)
   ```aiignore
   export WALLET_DB_URL="sqlite://YOUR_CUSTOM_NAME.sqlite?mode=rwc`
   ```

## Code Walkthrough 🔎

1. Cargo dependencies
2. Create Esplora client
3. Create database connection pools
4. Create key store
5. Load or create and store secret key
6. Create BIP86 taproot descriptors
7. Load or create and store a new wallet
8. Create web app state
9. Configure web server routes
10. Start the web server

## Chose your own adventure 🏰

Imagine turning this project into an easy to install (single binary) testnet faucet. What features would you like to add?

### Small

- amounts in SATs or BTC
- amounts also in USD
- list utxos
- make it prettier (ie. [htmx](https://htmx.org/) and [tailwinds](https://tailwindcss.com/docs/installation))
- only allow spending if balance available
- custom genesis (eg. testnet4)
- sync with electrum or esplora
- store data in postgreSQL
- simple captcha to spend

### Medium

- manual utxo selection
- sync with CBF [bdk-kyoto](https://github.com/bitcoindevkit/bdk-kyoto)
- PoW captcha to spend (see [alpenlabs](https://github.com/alpenlabs/faucet-api))

### Large

- send/receive payjoins [rust-payjoin](https://github.com/payjoin/rust-payjoin)
- store data in [redb](https://github.com/cberner/redb)
- nostr bot

## BDK Project Links

* [Home](https://bitcoindevkit.org)
* [Repo](https://github.com/bitcoindevkit/bdk)
* [API docs for `bdk_wallet`](https://docs.rs/bdk_wallet/latest/bdk_wallet/)
* [Discord](https://discord.gg/dstn4dQ)
* [Nostr](https://primal.net/p/npub13dk3dke4zm9vdkucm7f6vv7vhqgkevgg3gju9kr2wzumz7nrykdq0dgnvc)
* [bdk-ffi (Kotlin,Swift,Python)](https://github.com/bitcoindevkit/bdk-ffi)
* [WIP "Book of BDK"](https://bitcoindevkit.github.io/book-of-bdk/)

