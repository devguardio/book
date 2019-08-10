# Custom Publishers

when building IoT devices, you will inevitably want to build your own services can be called through carrier.
You can use the cli to call any service using "carrier get"

At the present time, the only way to do this is using the rust api, specifically the [PublisherBuilder](https://docs.rs/carrier/0.10.0/carrier/publisher/struct.PublisherBuilder.html)
For a fully functional example, check out [this example on github](https://github.com/aep/carrier-custom-service-example)


```rust
pub fn main() -> Result<(), Error> {
    env_logger::init();
    let poll            = osaka::Poll::new();
    let config          = carrier::config::load()?;
    let mut publisher   = carrier::publisher::new(config)
        .route("/v2/myorg.mything.v1/whodis",      None, whoami)
        .with_disco(NAME.to_string(), VERSION.to_string())
        .publish(poll);
    publisher.run()
}

pub fn whoami(
    _poll: osaka::Poll,
    _headers: carrier::headers::Headers,
    _identity: &carrier::identity::Identity,
    mut stream: carrier::endpoint::Stream,
) -> Option<osaka::Task<()>> {
    stream.send(carrier::headers::Headers::ok().encode());
    stream.message(proto::Helo{
        whodis: "peter".to_string()
    });
    None
}

```
