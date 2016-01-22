# ripple-commander
A command line client for ripple trading. Now ripple-commander is using Ripple REST API.

If you appreciate the work, welcome donate some xrp to `rscxz5PqRrmUaMigyb1mP32To1rQDygxAq` .

## Usage
1. Install nodejs (>=4.0.0).
2. Checkout out the source code.

        git clone https://github.com/kuyur/ripple-commander.git

3. Download necessary node modules.

        npm install

4. Before running the commander, you should copy `config.json.sample` and rename the new file to `config.json`. Use a text editor to open `config.json`, edit the `server` field to your private or trusted server. If you trust Ripple Labs 100%, you still can use the default configuration(`https://api.ripple.com/v1`) until it is shutdown.
 
5. Run commander. Account (ripple address) and secret will be required for the first time.

        node start-commander.js

6. Type **help** to see available commands. Press **Ctrl+C** to exit.

## Commands
**Generate a new wallet**

        new-wallet

**Get balance of current wallet**

        get-balance

**Get trustlines of current wallet**

        get-trustlines

**Grant or remove a trustline**, set limit to 0 for removing.

        grant-trustline <issuer> <currency> <limit> [ --allow-rippling ]

**Send money**, for example, `send rscxz5PqRrmUaMigyb1mP32To1rQDygxAq 20+XRP`.

        send <destination> <amount+currency+issuer> [ --source-tag=<source_tag> ] [ --destination-tag=<destination_tag> ] [ --invoice-id=<invoice_id> ]

**Send money to bridge**, for example `send-to-bridge zfb@ripplefox.com 100`, you will be asked for detail later.

        send-to-bridge <destination> <amount>

**Get payment detail**

        get-payment <resource_id>

**Get detail of recent payments**

        get-payments

**Get orders**

        get-orders

**Place an order**, type can be `sell` or `buy`.

        place-order <type> <amount1+currency1+issuer1> <amount2+currency2+issuer2>

**Cancel an order**

        cancel-order <sequence>

**Get orderbook of currency pair**, notice that orders generated by auto-bridge are not contained in the list.

        get-orderbook <currency1+issuer1> <currency2+issuer2> [ --limit=<limit> ]

**Get transaction status**

        get-transaction <hash>

**Show list of trusted issuers**, Data is from [https://ripple.com/knowledge_center/gateway-information/](https://ripple.com/knowledge_center/gateway-information/). You can add custom gateways by editing `config.json`.

        show-issuers [ --keyword=<issuer_name> ]

**Show all accounts in wallet**, the top one is the account currently in use.

        show-accounts [ --show-secret ]

**Add an account into wallet**

        add-account [ <address> ]

**Change the activated account (account currently in use)**

        change-account [ <address> ]

**Remove an account from wallet**

        remove-account [ <address> ]

**Encrypt wallet**, Use AES to protect the wallet file. Afte encryption, wallet.txt will be removed and wallet.dat will be generated.

        encrypt-wallet

**Decrypt wallet**

        decrypt-wallet

## Tasks done

* Trading. (grant trustline, send money, place order, cancel order, etc.)
* Federation protocol supported. You can withdraw money by sending IOU to automatic bridge.
* Wallet protection.
* Account management.

## Remaining tasks

* Command auto-complete.
* Pipe.
* Generate new ripple account offline.
* Offline signature and discard REST api.
