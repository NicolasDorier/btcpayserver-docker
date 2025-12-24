# Vaultwarden

[Vaultwarden](https://github.com/dani-garcia/vaultwarden) is an open source
implementation of the Bitwarden protocol.

## Installation

Set the hostname and enable the fragment from a root login shell:

```bash
export VAULTWARDEN_HOST='vaultwarden.example.com'
btcpay-fragments add opt-add-vaultwarden
```

Setup generates a 64-character admin key once, stores it in
`secrets/vaultwarden_admin_token`, and mounts it into the container as a Compose
secret. Display the key from a root login shell with:

```bash
cat "$BTCPAY_BASE_DIRECTORY/btcpayserver-docker/secrets/vaultwarden_admin_token"
```

Browse to `https://vaultwarden.example.com/admin` and enter that key. Treat the
secret file and Docker access as privileged.

To rotate the key, replace the file contents and restart the `vaultwarden`
service.

## Recommended Settings

Once in the admin panel:

1. Disable signups under **General settings > Allow new signups**.
2. Configure SMTP and send a test email.
3. Invite users from the **Users** tab.
