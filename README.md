Ethereum Network Stats with POA and POW support
===============================================
[![Build Status][travis-image]][travis-url] [![dependency status][dep-image]][dep-url]

This is a visual interface for tracking proof-of-work ("mainnet") and proof-of-authority ("testnet") network status. It uses WebSockets to receive stats from running nodes and output them through an angular interface. It is the front-end implementation for [ethstats-client](https://github.com/goerli/ethstats-client).

## Proof-of-Authority
![Screenshot](src/images/screenshot-poa.png "Screenshot POA")

* Demo: https://stats.goerli.net/
* Demo: https://kotti.goerli.net/

#### Prerequisite
* node
* npm

#### Installation
Make sure you have node.js and npm installed.

Clone the repository and install the dependencies:

```bash
git clone https://github.com/goerli/ethstats-server
cd ethstats-server
sudo npm install -g --unsafe-perm=true --allow-root
npm install
sudo npm install -g grunt-cli
```

#### Build
In order to build the static files you have to run grunt tasks which will generate dist directories containing the js and css files, fonts and images.

```bash
grunt poa
```

To build the static files for a network other than Ethereum copy and change src/js/defaultConfig.js and run the following command.

```bash
grunt poa --configPath="src/js/someOtherConfig.js"
```
#### Configure
Define some setting to environment file (.env)

```bash
PORT=3030
WS_SECRET=beta-net-stats-has-a-secret
```


#### Run (Test)
Start a node process and pass the websocket secret to it.

```bash
WS_SECRET="asdf" npm start
```

#### Run (Production)
Start a node process and pass the websocket secret to it.

```bash
pm2 start npm --name "beta-stats-server" -- start
```
Find the interface at http://localhost:3030



## Proof-of-Work (Legacy)

![Screenshot](src/images/screenshot-pow.png "Screenshot POW")

* Demo: https://mordor.dash.fault.dev/

Same as above, just run the `pow` build task in Grunt.

```bash
grunt pow
WS_SECRET="asdf" npm start
```

:-)

[travis-image]: https://travis-ci.org/goerli/ethstats-server.svg
[travis-url]: https://travis-ci.org/goerli/ethstats-server
[dep-image]: https://david-dm.org/goerli/ethstats-server.svg
[dep-url]: https://david-dm.org/goerli/ethstats-server

## PM2
PM2 is a Production Process Manager for Node.js applications  with a built-in Load Balancer.

                Start and Daemonize any application:
                $ pm2 start app.js

                Load Balance 4 instances of api.js:
                $ pm2 start api.js -i 4

                Monitor in production:
                $ pm2 monitor

                Make pm2 auto-boot at server restart:
                $ pm2 startup

                To go further checkout:
                http://pm2.io/


