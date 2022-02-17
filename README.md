# Osmosis Web Interface
Frontend React app for Osmosis AMM.

## Install global dependencies
To run or build the app, first, need to install `Node.js` and `Yarn` globally;

First Install Node (recommend 14.x.x LTS version) from;

https://nodejs.org/

Then install Yarn;
```bash
npm install -g yarn
# OR
sudo npm install -g yarn
```

## Install project dependencies
First clone the repo;
```bash
git clone https://github.com/anthonymq/osmosis-frontend.git && cd osmosis-frontend
```

Then install project dependencies;
```bash
yarn
```

## Build
To build the static assets;
```bash
yarn build:css && yarn build
```
This should produce `prod` folder with static assets.

Currently, Osmosis frontend app is SPA with entry point: `prod/index.html`

## Development
To spin up the local dev server;
```bash
yarn build:css && yarn dev
```
The app should be live at http://localhost:8081

## Deploy a new version on the Internet Computer
The first time, you need to configure the upstream (osmosis-labs own repository) to be able to retrieve the last version of the code
```bash
git remote add upstream https://github.com/osmosis-labs/osmosis-frontend.git
```
Then, everytime you want to update the app, you have to update our branch "master" with the last code
```bash
git checkout master 
git fetch upstream
git pull --rebase upstream master
dfx deploy --network=ic
```
The app should be live at https://ate7l-riaaa-aaaaf-qae3q-cai.raw.ic0.app/

Note that if you need to authorize a new principal to this canister you should :
```bash
dfx canister --network=ic call osmose_assets authorize '(principal "NEW_PRINCIPAL_ID")'
```

## License

This work is dual-licensed under Apache 2.0 and MIT.
You can choose between one of them if you use this work.

`SPDX-License-Identifier: Apache-2.0 OR MIT`
