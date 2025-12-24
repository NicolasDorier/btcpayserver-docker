# VaultWarden

VaultWarden is an open source implementation of bitwarden protocol. [Github](https://github.com/dani-garcia/vaultwarden).

## Pre-requesite

First, you will need to configure your password for administrator access.
For getting, `VAULTWARDEN_ADMIN_TOKEN`, please run this.

```bash
docker run --rm -it vaultwarden/server /vaultwarden hash
```

After you chose your password, a token will be output.
Then setup `VAULTWARDEN_ADMIN_TOKEN` and `VAULTWARDEN_HOST`.

```bash
export VAULTWARDEN_ADMIN_TOKEN='<hash>'
export VAULTWARDEN_HOST='vaultwarden.example.com'
```

Add the docker fragment and install.

```bash
BTCPAYGEN_ADDITIONAL_FRAGMENTS="$BTCPAYGEN_ADDITIONAL_FRAGMENTS;opt-add-vaultwarden"
. btcpay-setup.sh -i
```

When it is started, browse to your domain (`vaultwarden.example.com/admin`).
You will be asked for your `Authentication key`, enter your chosen password from earlier.

## Recommended settings

Once in the admin panel:

1. Disable Signups. (`General settings ➡ Allow new signups`)
2. Enable SMTP and set up SMTP and send test email to yourself (there is test email button)
3. Invite your users in the Users Tab