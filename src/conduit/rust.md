# rust setup

building a conduit requires basic rust knowledge. If you do not know rust, please refer to
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
