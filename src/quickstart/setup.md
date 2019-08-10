# Quickstart





## Creating an identity

Carrier is built on eliptic curve identities, specifically ed25519.
Every device and every user in the system has an identity. We're going to generate yours now.

```bash
$ carrier setup
identity: oWDw4B1f88jiGj71qMCYTL8RCCdpRYfgbSNXQSDVByRVHV9
```
This is your identity that was generated out of randomness from your system. The carrier network will know your computer by this long number.
No registry with any provider is nessesary to create an identity and you may create as many as you want.
Unlike an api key, a carrier identity is not tied to a specific service.
you may use it in peer to peer communication, or talk to any other service on the carrier network without needing prior registration.

In addition to your identity, a secret is stored in ~/.devguard/carrier.toml .
Never share this file with anyone, but do make backups.
