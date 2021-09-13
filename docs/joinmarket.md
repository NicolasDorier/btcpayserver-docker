# Joinmarket support

JoinMarket is software to create a special kind of bitcoin transaction called a CoinJoin transaction. Its aim is to improve the confidentiality and privacy of bitcoin transactions.

You will be able to use your bitcoin to help other protect their privacy, while earning a yield for this service.

See [the documentation of the joinmarket project](https://github.com/JoinMarket-Org/JoinMarket-Docs/blob/master/High-level-design.md) for more details.

This is a very advanced functionality, and there is no easy way to recover if something go wrong.

For hardcore bitcoiners only.

## How to use

```bash
BTCPAYGEN_ADDITIONAL_FRAGMENTS="$BTCPAYGEN_ADDITIONAL_FRAGMENTS;opt-add-joinmarket"
. btcpay-setup.sh -i
```

Then you need to setup your joinmarket wallet:

```bash
jm.sh wallet-tool-generate
jm.sh set-wallet <wallet_file_name> <password>
```

Once done, you will need to send some money to the joinmarket wallet:

```bash
jm.sh wallet-tool
```

## How to fine tune?

In the [README](../README.md), follow the instruction in `How can I customize the generated docker-compose file?`.
Then pass as environment variable the attribute you want to modify, prefixed by `jm_`.

Our system is using the default configuration of joinmarket, then replace the values your specify like this.

Example:

```yml
services:
  joinmarket:
    environment:
      jm_gaplimit: 3000
      jm_txfee: 300
      jm_cjfee_a: 500
```

## How to send payments or use any other scripts?

You need to connect to the container, and use joinmarket python scripts such as:

```bash
jm.sh bash
sendpayment.py wallet.jmdat ...
```

You might get the following error:

```
Failed to load wallet, error message: RetryableStorageError('File is currently in use (locked by pid 12822). If this is a leftover from a crashed instance you need to remove the lock file `/root/.joinmarket/wallets/.wallet.jmdat.lock` manually.')
```

This is because the yield generator is running.