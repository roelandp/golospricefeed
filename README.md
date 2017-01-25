## Golos Price Feed
monitoring the golos trades on the market(s) and publishing the golos pricefeed

This script is based upon [@clayop's steemfeed script](https://github.com/clayop/steemfeed)


### Supported Exchanges
* Livecoin
* Liqui
* Bittrex
* Kuna
* Openledger (Not listed yet)
* Poloniex (Not listed yet)


### Preparation
To use this price feed script, the following dependencies and packages should be installed.

    sudo apt-get install libffi-dev libssl-dev python3-dev python3-pip
    sudo pip3 install python-dateutil
    sudo pip3 install websocket-client

    $ git clone https://github.com/GolosChain/python-goloslib
    $ cd python-goloslib
    $ python3 setup.py install --user

In addition, you should run cli_wallet by using the following command,

    cli_wallet --server-rpc-endpoint=ws://127.0.0.1:9090 --rpc-http-endpoint=127.0.0.1:9091 --rpc-http-allowip 127.0.0.1


### Installation
Copy the code in [this link](https://github.com/roelandp/golospricefeed/blob/master/golospricefeed.py) and paste as `golospricefeed.py` in your server.


### Configuration
Then, edit the `golospricefeed.py` to configure. We have some items under Config category in the code.

* `interval`: Interval of publishing price feed. The default value is one hour (3600 seconds)
* `freq`: Frequency of parsing trade history. Please be noticed that it can parse only 200 last trading history (Bittrex), so as trading is active you may need to decrease this frequency value.
* `min_change`: Minimum price change percentage to publish feed
* `max_age`: Maximum age of price feed
* `manual_conf`: Maximum price change without manual confirmation. If price change exceeds this, you will be asked to confirm
* `use_telegram`: If you want to use Telegram for confirmation, enter 1
* `telegram_token`: Create your Telegram bot at @BotFather (https://telegram.me/botfather)
* `telegram_id`: Get your telegram id at @MyTelegramID_bot (https://telegram.me/mytelegramid_bot)
* `bts_ws` : List of BitShares Websocket servers
* `rpc_host`: Your RPC host address
* `rpc_port`: Your RPC host port
* `witness`: Enter ***YOUR WITNESS ID*** here
* `walletpassword`: Enter ***YOUR WALLET PASSWORD*** here or unlock your wallet after executing the `cli_wallet` command stated above and comment all `walletlock()` calls in the code


### Run
Then, run this code in a separate screen

    screen -S golospricefeed
    python3 ./golospricefeed.py
