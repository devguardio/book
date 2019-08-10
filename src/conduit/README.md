# Conduit

carrier conduit is how you automate devices at scale.

This document will guide you step by step through building your own conduit,
which will connect to your fleet and collect sysinfo stats.
Usually you would process those stats further, for example write them into a database available to webservices.

Conduit runs on your systems, and establishes end to end encrypted channels to your devices.
We at devguard do not offer querying your device data via rest interfaces, because this
would compromise the principle of end to end encryption.

You can however, implement your http interfaces inside conduit, should they be more suitable for your workflow.
