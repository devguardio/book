# sysinfo

sysinfo is a powerful stats service, espcially when collected at scale using carrier conduit or nexus.

```bash
$ carrier sysinfo oWDw4B1f88jiGj71qMCYTL8RCCdpRYfgbSNXQSDVByRVHV9
[:status = 200, ]
Sysinfo {
    Uname {
        sysname: "Linux",
        release: "5.2.4-arch1-1-ARCH",
        machine: "x86_64",
    },
    Mem {
       free: 45266868,
    },
    Netdev {
        name: "eth0",
        macaddr: "fa:0c:fd:f9:a2:c6",
        addrs: [
            NetAddress {
                addr: "192.168.11.226:0",
                mask: "255.255.255.0:0",
                broadcast: "192.168.11.255:0",
            },

```
