# Privacy Policy for SMS Forwarding: AutoRelay

**Last updated:** 2026-05-30

SMS Forwarding: AutoRelay ("the App") is an Android application that
forwards incoming SMS messages to user-configured destinations
(webhooks, Telegram bots, email addresses). This Privacy Policy
describes what data the App handles, how it is stored, and what
choices you have.

## Who we are

The App is developed and maintained by an individual developer. Contact:
**urbandevapp@gmail.com**.

## Data the App handles

The App processes the following data **on your device only**:

- **SMS messages** received by your device while the App is running:
  sender address, message body, timestamp, SIM slot, delivery status,
  optionally a parsed one-time password (OTP) code, and optionally a
  recognised service name (e.g., "Sberbank", "Google") derived from the
  sender header.
- **Contact display name** for the SMS sender, only when you have
  granted `READ_CONTACTS` permission (off by default). The lookup
  happens on-device against your address book; no contact data is
  uploaded by the App. If permission is not granted, the App never
  reads your contacts.
- **Forwarding destinations** that you configure in the App: webhook
  URLs, Telegram bot tokens and chat IDs, SMTP credentials and recipient
  email addresses, and any sender filter rules (whitelist, blacklist,
  or whitelist/blacklist by contact name).

The App does not collect your phone number, location, device
identifiers, or any other personal information beyond what is listed
above.

## Where data is stored

All data is stored **locally on your device** in the App's private
storage (Android sandbox), in a Room database encrypted with
[SQLCipher](https://www.zetetic.net/sqlcipher/). This includes SMS
message history and all forwarding destination configurations (webhook
URLs, Telegram bot tokens, SMTP credentials). Data is protected both
by Android's application sandbox and by database-level encryption at
rest.

The App does **not** upload, sync, or back up your SMS messages or
destination configurations to any server operated by the developer.

## How data is shared

When a new SMS arrives and matches your filter rules, the App forwards
the message **directly from your device** to the destinations you have
configured:

- **Webhook destinations** — sent over HTTPS (or HTTP, if you configure
  an HTTP URL) as a JSON POST request to the URL you provide.
- **Telegram destinations** — sent via the Telegram Bot API
  (`api.telegram.org`) using the bot token you provide.
- **Email destinations** — sent via the SMTP server you configure
  (host, port, username, password) to the recipient address you choose.

The developer does not operate any intermediate server. Forwarded data
travels directly from your device to the third-party services you
choose. Those services have their own privacy policies and terms which
apply to the data once it leaves your device.

## Third-party services

The App itself does **not** include analytics SDKs, crash reporting
services, advertising libraries, or any other third-party data
collection. The only third-party services involved are those **you
explicitly configure** as forwarding destinations (Telegram, your SMTP
provider, your webhook endpoints).

## Permissions and why we need them

The App requests the following Android permissions:

- `RECEIVE_SMS`, `READ_SMS` — to receive and read incoming SMS messages
  for forwarding. This is the App's core function.
- `INTERNET` — to deliver forwarded messages to webhooks, Telegram, and
  SMTP servers.
- `FOREGROUND_SERVICE`, `POST_NOTIFICATIONS` — to keep the forwarding
  service running reliably and show its status in the notification
  area.
- `RECEIVE_BOOT_COMPLETED` — to automatically resume forwarding after
  your device restarts.
- `READ_CONTACTS` *(optional, off by default)* — to look up the display
  name for an SMS sender in your address book and include it in the
  forwarded payload and on-device history. You can enable or disable
  this feature in the App's settings; the App functions normally
  without it.

The App does not request `ACCESS_FINE_LOCATION` or any other sensitive
permission unrelated to SMS forwarding.

## Data retention and deletion

- All App data is removed when you **uninstall** the App.
- You can clear all App data at any time via Android Settings → Apps →
  SMS Forwarding: AutoRelay → Storage → Clear data.
- Inside the App, you can delete individual destinations and your SMS
  history.

The developer cannot delete your data on your behalf because no data is
held on developer-controlled servers.

## Children

The App is not directed at children under 13 and is not designed to
collect data from children.

## Security

The App stores all data in a SQLCipher-encrypted Room database,
providing encryption at rest for SMS history and destination
credentials. The Android sandbox additionally prevents other apps from
accessing App storage without root access.

Network communications to webhooks, Telegram, and SMTP servers use the
transport security configured by those services (typically HTTPS / TLS).
You are responsible for the security of the destinations you configure
(for example, using HTTPS webhooks rather than plain HTTP, and
protecting your Telegram bot token and SMTP credentials).

## Changes to this policy

If the App's data handling practices change in any material way (for
example, adding analytics or sending data to a developer-operated
server), this policy will be updated and the change will be announced
in the App or on the project page before the change takes effect.

## Contact

Questions about this Privacy Policy: **urbandevapp@gmail.com**.
