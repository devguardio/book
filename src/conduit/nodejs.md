# simple data collector with nodejs

before you continue please make sure all devices are on the same shadow. see [quickstart/shadows](/quickstart/shadows.html)


At scale, you will want an automated way to collect data from your systems.
building a data collector in nodejs is the easiest way to get started, if you already know javascript.


```bash
$ npm install --save devguard-conduit
```

we also recommend using protobufs. for this example you will need the file "carrier.sysinfo.v1.proto" from the carrier source code [here](https://github.com/devguardio/carrier/tree/master/proto)


```bash
$ npm install --save prorobufjs
```




```js
var carrier = require('devguard-carrier');
var protobuf = require("protobufjs");

console.log(carrier.identity());


// load the protobuf files
protobuf.load("carrier.sysinfo.v1.proto", function(err, root) {

    // we will call the sysinfo endpoint, which is this type
    var Sysinfo = root.lookupType("carrier.sysinfo.v1.Sysinfo");

    // create a new conduit
    const conduit = new carrier.Conduit();

    // whenever we find a new peer on the shadow
    conduit.on("publish", (identity, peer) => {
      console.log("watt");


        // we connect to it
        // note that we could also decide to only connect some peers,
        // this is useful if you want to black/whitelist something,
        // or for horizontal scaling when running multiple conduits in prallel
        peer.connect();

        // discover the services this peer has on offer
        peer.discover((disco) => {

            console.log("disco", identity, disco);

            // if the device has the sysinfo service
            if (disco.paths.includes("/v2/carrier.sysinfo.v1/sysinfo")) {


                let headers = {
                    ":path" : "/v2/carrier.sysinfo.v1/sysinfo",
                };

                // we poll it every 10 seconds
                // this is soft-realtime multiplexed into an established connection
                // so alot different than http polling.
                // some services may also continuously deliver messages
                // in which case the first integer arg is a reconnect delay,
                // should the connection drop for whatever reason

                peer.schedule(10, headers, (identity, message) => {
                    let sysinfo = Sysinfo.decode(new Uint8Array(message));
                    console.log(identity, sysinfo);
                });
            }
        });
    });

    // let's party
    conduit.start();

});
```





