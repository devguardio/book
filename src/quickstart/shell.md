# Shell

one of the built in services is carrier shell. In a new terminal, open a shell on the publisher:

```sh
$ carrier shell oWDw4B1f88jiGj71qMCYTL8RCCdpRYfgbSNXQSDVByRVHV9
[:status = 200, ]
[aep@carrier]$
```

you can open a shell to any device on the network that your local identity is authorized for.
There's no need to configure any network, like open any ports.
In best case, carrier will find a direct peer to peer path, worst case it will relay your encrypted traffic
through the devguard carrier ring.
