# Peer Discovery


you may have noticed we so far ignored two additional lines from the first carrier setup.

```
shadow: oT136mPPVYptwoMvnjb2AUXird6tsKsyQ2S46TCTNYr7WwH
shadow-secret: oWBx6jaNJo3XLCvs56EnwBb6uBhJZVEYbnXJNrz9nsFHyrf
```

they are also permanently stored in your ~/.devguard/carrier.toml
The public 'shadow' address is a subnet on which devices can discover each other.
Carrier is free to use for up to 10 peers per shadow.

In order to use massive managment features like conduit,
you must pick one of the shadow/secret pair and copy it over to all of your devices ~/.devguard/carrier.toml.

All your devices will then appear in carrier subscribe

```bash
$ carrier subscribe oT136mPPVYptwoMvnjb2AUXird6tsKsyQ2S46TCTNYr7WwH
+ oWDw4B1f88jiGj71qMCYTL8RCCdpRYfgbSNXQSDVByRVHV9
```

