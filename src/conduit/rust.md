# rust setup

before you continue please make sure all devices are on the same shadow. see [quickstart/shadows](/quickstart/shadows.html)

building your conduit in rust will help performance alot in high throughput scenarios but requires rust knowledge.
If you do not know rust, please refer to
[the official getting started guide](https://www.rust-lang.org/learn/get-started)

create a new project and add carrier as a dependency to Carrier.toml

```bash
$ cargo new conduit-myproject
Created binary (application) `conduit-myproject` package
$ cd conduit-myproject
$ edit Cargo.toml
```

```toml
[dependencies]
carrier="0.10"
```



in main.rs you would do this:


```rust
use carrier::{self, conduit, Identity};

pub fn main() {
    // load ~/.devguard/carrier.toml
    let config = carrier::config::load().unwrap();
    let conduit = conduit::Builder::new(config).unwrap();
    // start peer discovery
    conduit.start(move |identity: Identity, broker: &mut conduit::ConduitState| {

        // connect to the discovered peer
        let mut peer  = broker.connect(identity.clone());

        // open a sysinfo stream
        let headers = carrier::headers::Headers::with_path("/v2/carrier.sysinfo.v1/sysinfo");

        // if it is closed, reopen in 10 seconds.
        // sysinfo always closes after one message, because it is sync.
        // polling a channel is MUCH cheaper than polling http
        // because it is inside an established connection, like http2
        peer.schedule(std::time::Duration::from_secs(10), headers,
            // for each message
            move |identity: &Identity, msg: carrier::proto::Sysinfo|{
                println!("{}: {:?}", identity, msg);
            }
        );
    });
}
```
