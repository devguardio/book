# Putting your thing on the network

Now that we have an identity, we can can expose services on the global bus.
carrier does not have user-definable names like domains. There is no central registry, instead everything is cryptographically tied to your identity.

for now we're going to use the default services exposed by the carrier cli

```bash
$ carrier publish
[INFO endpoint] identity: oWDw4B1f88jiGj71qMCYTL8RCCdpRYfgbSNXQSDVByRVHV9
[INFO endpoint] via udp 88.198.32.218
[INFO endpoint] via udp 5.9.122.66
[INFO endpoint] broker: oW9mVQjsTauUNjweCww5GMoXHKhpbM4CCAos1HSJSy8rkr3
[INFO endpoint] [:status = 200, ]
```

Congratulations, your machine is now on the carrier bus!

