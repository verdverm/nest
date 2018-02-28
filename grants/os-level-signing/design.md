# Design Overview

Drawing on https://github.com/txthinking/brook


### High-level

Independent Golang application featuring:

- Binary Application:
  - OS installers
  - Electron UI for interacting with end-users
  - API Server for DApps to talk to


### Flow

- DApp comms with server on `127.0.0.1:<port>`
  - Cross browser support + other local applications
- On signing event
  - DApp -> server (request)
  - server -> user (UI notification)
  - user does thing (signing / new app approve)
  - server -> DAPP (success)



### Some considerations

- How to have verified / approved DApps for the user?
- How to secure user machine communication?
  - Https sites __are__ allowed to talk to `127.0.0.1`
  - i.e. we need TLS between the DApp and OS-Signer
  - but... browsers may barf on a self-signed cert
  - Other local applications _should_ be easier to manage in this regard