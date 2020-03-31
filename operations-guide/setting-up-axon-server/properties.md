# Properties for Axon Server

## Node/Cluster setup

| Property| Default Value | Description |
| --- | --- | ---| 
| axoniq.axonserver.name| | Node name of this axonserver platform node, if not set defaults to the hostname|
| axoniq.axonserver.hostname| | Hostname of this node as communicated to clients, defaults to the result of hostname command|
| axoniq.axonserver.internal-hostname| | Hostname as communicated to other nodes of the cluster. Defaults to hostname |
| axoniq.axonserver.domain | | Domain of this node as communicated to clients. Optional, if set will be appended to the hostname in communication with clients|
| axoniq.axonserver.internal-domain| | Domain as communicated to other nodes of the cluster. Optional, if not set, it will use the domain value|
| server.port| 8024| HTTP port for the Axon Server console|
| axoniq.axonserver.port| 8124| gRPC port for axonserver platform|
| axoniq.axonserver.internal-port| 8224| gRPC port for communication between messing platform nodes|
| axoniq.axonserver.tags| | Key/value pairs of tags for tag based connections for clients.|
| axoniq.axonserver.devmode.enabled| false| SE only. Development mode (allows deleting all events from event store).|
| axoniq.axonserver.autocluster.first| | For autocluster option, set the internal hostname of the first node in the cluster|
| axoniq.axonserver.autocluster| | For autocluster option, defines the list of contexts to create/connect to.|
| axoniq.axonserver.recoveryfile| recovery.json| Start up with a recovery file to update node names in the controldb|
| axoniq.axonserver.set-web-socket-allowed-origins| false| Set WebSocket CORS Allowed Origins|
| axoniq.axonserver.max-message-size| 4MB| Maximum size of message to be sent to Axon Server|

## File locations

| Property | Default Value | Description |
| --- | --- | ---| 
| axoniq.axonserver.controldb-backup-location| .| Location where the control DB backups are created|
| axoniq.axonserver.pid-file-location| .| Location where AxonServer creates its pid file|
| axoniq.axonserver.event.storage| ./data| Location for segment files. Will create subdirectory per context.|
| axoniq.axonserver.snapshot.storage| ./data| Location for segment files. Will create subdirectory per context.|
| axoniq.axonserver.replication.log-storage-folder|./log| Directory where the transaction logs for replication are stored.|
| axoniq.axonserver.controldb-path| ./data| Directory where control DB is created|
| axoniq.axonserver.accesscontrol.token-dir| ./security| Directory where token is stored on startup|

## SSL configuration:

| Property | Default Value| Description|
| --- | --- | ---| 
| axoniq.axonserver.ssl.enabled| false| Indicates that SSL is enabled and gRPC servers should start in SSL mode. |
| axoniq.axonserver.ssl.cert-chain-file| | File containing the full certificate chain|
| axoniq.axonserver.ssl.internal-cert-chain-file| | File containing the full certificate chain to be used in internal communication between Axon Server nodes.|
| axoniq.axonserver.ssl.internal-trust-manager-file | | Trusted certificates for verifying the other AxonServer's certificate|
| axoniq.axonserver.ssl.private-key-file| | File containing the private key |

## Access control:

| Property| Default Value| Description|
| --- | --- | ---| 
| axoniq.axonserver.accesscontrol.enabled| false| Indicates that access control is enabled for the server|
| axoniq.axonserver.accesscontrol.cache-ttl| 300000| Timeout for authenticated tokens|
| axoniq.axonserver.accesscontrol.internal-token| | Token used to authenticate Axon Server instances in a cluster (only used by Enterprise Edition) |
| axoniq.axonserver.accesscontrol.token| | Token to be used by client applications connecting to Axon Server (only used by Standard Edition)|
| axoniq.axonserver.accesscontrol.systemtokenfile| | File containing a predefined system token|

## Performance:

| Property| Default Value| Description|
| --- | --- | ---| 
| axoniq.axonserver.event.max-bloom-filters-in-memory| 100| Maximum number of bloom filters to keep in memory|
| axoniq.axonserver.event.max-indexes-in-memory| 50| Maximum number of indexes to keep open in memory|
| axoniq.axonserver.event.read-buffer-size| 32KB| Size of the buffer when reading from non-memory mapped files. (SE only)|
| axoniq.axonserver.snapshot.max-bloom-filters-in-memory| 100| Maximum number of bloom filters to keep in memory|
| axoniq.axonserver.snapshot.max-indexes-in-memory| 50| Maximum number of indexes to keep open in memory|
| axoniq.axonserver.evsnapshotent.read-buffer-size| 32KB| Size of the buffer when reading from non-memory mapped files. (SE only)|
| axoniq.axonserver.executor-thread-count| 16| Number of threads for executing incoming gRPC requests|
| axoniq.axonserver.command-thread| 1| Threads per client responsible for sending commands to the client.|
| axoniq.axonserver.query-thread| 1| Threads per client responsible for sending queries to the client.|
| axoniq.axonserver.cluster-executor-thread-count| 16| Number of threads for executing incoming gRPC requests for internal communication|
| axoniq.axonserver.cluster.query-threads| 1| Threads per connected Axon Server node responsible for forwarding queries to that node.|
| axoniq.axonserver.cluster.command-threads| 1| Threads per connected Axon Server node responsible for forwarding commands to that node.|
| axoniq.axonserver.grpc-buffered-messages| 500| The initial flow control setting for gRPC level messages. This is the number of messages that may may be en-route before the sender stops emitting messages. This setting is per-request and only affects streaming requests or responses. Application-level flow control settings and buffer restriction settings are still in effect|
| axoniq.axonserver.default-command-timeout| 300000| Timeout for commands sent to command handler|
| axoniq.axonserver.default-query-timeout| 300000| Timeout for queries sent to query handler|
| axoniq.axonserver.query.timeout| 300000| Timeout for ad-hoc queries|
| axoniq.axonserver.websocket-update.initial-delay| 10000||
| axoniq.axonserver.websocket-update.rate| 1000||

## Event Store:

| Property| Default Value| Description|
| --- | --- | ---| 
| axoniq.axonserver.event.bloom-index-fpp| 0.03| False-positive percentage allowed for bloom index. Decreasing the value increases the size of the bloom indexes|
| axoniq.axonserver.event.force-interval| 1000| Interval to force syncing files to disk (ms)|
| axoniq.axonserver.event.primary-cleanup-delay| 15| Delay to clear ByfeBuffers from off-heap memory for writable segments|
| axoniq.axonserver.event.secondary-cleanup-delay| 15| Delay to clear ByfeBuffers from off-heap memory for read-only segments|
| axoniq.axonserver.event.segment-size| 256Mb| Size for new storage segments|
| axoniq.axonserver.event.sync-interval| 1000| Interval (ms) to check if there are files that are complete and can be closed|
| axoniq.axonserver.event.validation-segments| 10| Number of segments to validate to on startup after unclean shutdown|
| axoniq.axonserver.snapshot.bloom-index-fpp| 0.03| False-positive percentage allowed for bloom index for snapshots. Decreasing the value increases the size of the bloom indexes|
| axoniq.axonserver.snapshot.force-interval| 1000| Interval to force syncing files to disk (ms)|
| axoniq.axonserver.snapshot.primary-cleanup-delay| 15| Delay to clear ByfeBuffers from off-heap memory for writable segments|
| axoniq.axonserver.snapshot.secondary-cleanup-delay| 15| Delay to clear ByfeBuffers from off-heap memory for read-only segments|
| axoniq.axonserver.snapshot.segment-size| 256Mb| Size for new storage segments|
| axoniq.axonserver.snapshot.sync-interval| 1000| Interval (ms) to check if there are files that are complete and can be closed|
| axoniq.axonserver.snapshot.validation-segments| 10| Number of snapshot segments to validate to on startup after unclean shutdown|
| axoniq.axonserver.query.limit| 200||
| axoniq.axonserver.new-permits-timeout| 120000| Timeout for event trackers while waiting for new permits.|
| axoniq.axonserver.blacklisted-send-after| 1000| Force sending an event on an event tracker after this number of blacklisted events. Ensures that the token in the client application is updated.|
| axoniq.axonserver.max-events-per-transaction| 32767| Maximum number of events that can be sent in a single transaction.|

## File names:

| Property | Default Value| Description|
| --- | --- | ---| 
| axoniq.axonserver.event.bloom-index-suffix| .bloom| File suffix for bloom files|
| axoniq.axonserver.event.events-suffix| .events| File suffix for events files.|
| axoniq.axonserver.event.index-suffix| .index| File suffix for index files|
| axoniq.axonserver.snapshot.bloom-index-suffix| .sbloom| File suffix for snapshot bloom files|
| axoniq.axonserver.snapshot.events-suffix| .snapshots| File suffix for snapshot files|
| axoniq.axonserver.snapshot.index-suffix| .sindex| File suffix for index files for snapshots|
| axoniq.axonserver.replication.index-suffix| .index| File suffix for index files for transaction logs|
| axoniq.axonserver.replication.log-suffix| .log| File suffix for transaction log files|

## Keep alive:

| Property| Default Value| Description|
| axoniq.axonserver.keep-alive-time | 2500| Interval at which AxonServer will send timeout messages. Set to 0 to disbable gRPC timeout checks|
| axoniq.axonserver.keep-alive-timeout | 5000 | Timeout for keep alive messages on gRPC connections|
| axoniq.axonserver.min-keep-alive-time| 1000 | Minimum keep alive interval accepted by this end of the gRPC connection|
| axoniq.axonserver.client-heartbeat-timeout| 5000| Timeout on application level heartbeat between client and Axon Server.|
| axoniq.axonserver.client-heartbeat-check-initial-delay| 10000||
| axoniq.axonserver.client-heartbeat-check-rate| 1000||
| axoniq.axonserver.heartbeat.enabled| false||

## Not used:

| Property | Default Value| Description|
| --- | --- | ---| 
| axoniq.axonserver.event.number-of-segments| 5| Number of segments to keep in primary location (only for multitier storage option)|
| axoniq.axonserver.event.flags| 0| Extra flags to consider when writing/reading events to file|
| axoniq.axonserver.snapshot.number-of-segments| 5| Number of snapshot segments to keep in primary location (only for multitier storage option)|
| axoniq.axonserver.snapshot.flags| 0| Extra flags to consider when writing/reading snapshots to file|
| axoniq.axonserver.metrics-interval| 15| Expiry interval (minutes) of metrics|
| axoniq.axonserver.replication.flags| 0| Extra flags to consider when writing/reading log entries to file|
| axoniq.axonserver.replication.number-of-segments| 1000||

## Flow control:

| Property| Default Value| Description|
| --- | --- | ---| 
| axoniq.axonserver.cluster.command-flow-control.initial-permits| 10000| Initial number of permits granted in communication between Axon Server nodes.|
| axoniq.axonserver.cluster.command-flow-control.new-permits| 5000| Additional number of permits granted in communication between Axon Server nodes.|
| axoniq.axonserver.cluster.command-flow-control.threshold| 5000| Threshold at which the node will send another grant of new-permits to the connected node.|
| axoniq.axonserver.cluster.query-flow-control.initial-permits| 10000| Initial number of permits granted in communication between Axon Server nodes.|
| axoniq.axonserver.cluster.query-flow-control.new-permits| | Additional number of permits granted in communication between Axon Server nodes.|
| axoniq.axonserver.cluster.query-flow-control.threshold| | Threshold at which the node will send another grant of new-permits to the connected node.|

## GRPC metrics

| Property| Default Value| Description|
| --- | --- | ---| 
| axoniq.axonserver.metrics.grpc.enabled| false| Enables Axon Server gRPC metrics|
| axoniq.axonserver.metrics.grpc.jaeger-enabled| false| Enables exporter for Jaeger|
| axoniq.axonserver.metrics.grpc.jaeger-endpoint| | Endpoint to access Jaeger exporter. Will not be considered if jaeger-enabled is set to false.|
| axoniq.axonserver.metrics.grpc.jaeger-service-name| | Service name to be set to Jaeger exporter.|
| axoniq.axonserver.metrics.grpc.prometheus-enabled| false| Enables exporter for Prometheus.|
| axoniq.axonserver.metrics.grpc.z-paged-enabled| false| Enables ZPages for displaying traces/stats.|
| axoniq.axonserver.metrics.grpc.z-pages-port| 8888| HTTP port to access ZPages.|

## Internal maintenance tasks:

| Property| Default Value| Description|
| --- | --- | ---| 
| axoniq.axonserver.cluster.connection-check-delay| 1000| |
| axoniq.axonserver.cluster.connection-check-interval| 1000| Interval between each run of the connection checker (in ms.)|
| axoniq.axonserver.cluster.connection-wait-time| 3000| Timeout for connection request (in ms.)|
| axoniq.axonserver.cluster.metrics-distribute-delay| 1000| Delay before the first run of the metrics distributor (in ms.)|
| axoniq.axonserver.cluster.metrics-distribute-interval| 1000| Interval between each run of the metrics distributor (in ms.)|
| axoniq.axonserver.cluster.rebalance-delay| 7| Delay before the first run of the rebalancer (in seconds)|
| axoniq.axonserver.cluster.rebalance-interval| 15| Interval between each run of the rebalancer (in seconds)|
| axoniq.axonserver.cluster.auto-balancing| true| Automatic rebalancing of client connections enabled.|
| axoniq.axonserver.cache-close-rate| 5000| Interval at which to check for timed out queries and commands.|
| axoniq.axonserver.cluster.connectionCheckRetries| 5| |
| axoniq.axonserver.cluster.connectionCheckRetryWait| 1000||

## Replication

| Property| Default Value | Description |
| --- | --- | --- |
| axoniq.axonserver.replication.flow-buffer | 1000 | Number of unconfirmed append entry messages that may be sent to peer. |
| axoniq.axonserver.replication.force-interval| 1000| Interval to force writes to disk.|
| axoniq.axonserver.replication.force-snapshot-on-join | true| Option to force new members to first receive a snapshot when they join a cluster|
| axoniq.axonserver.replication.heartbeat-timeout| 300| Leader sends a heartbeat to followers if it has not sent any other messages to a follower for this time.|
| axoniq.axonserver.replication.initial-election-timeout| 0| Extra time that follower waits initially before moving to candidate state.|
| axoniq.axonserver.replication.log-compaction-enabled| true| Deletes old log files when all the entries in the file are applied for more than log-retention-hours hour.|
| axoniq.axonserver.replication.log-retention-hours| 1| Time to keep log files after all entries have been applied.|
| axoniq.axonserver.replication.max-election-timeout| 2500| Maximal time (in ms.) that a follower waits before moving to candidate state, if it has not received any messages from a leader. Also, time that leader waits before stepping down if it has not heard from the majority of its followers.|
| axoniq.axonserver.replication.max-entries-per-batch| 10| Maximum number of append entry messages sent to one peer before moving to the next.|
| axoniq.axonserver.replication.max-indexes-in-memory| 10||
| axoniq.axonserver.replication.max-replication-round| 10||
| axoniq.axonserver.replication.max-snapshot-chunks-per-batch| 1000||
| axoniq.axonserver.replication.min-active-backups| 1| When active backup nodes are added to a context, this indicates on how many active backup nodes transactions must be confirmed before the transaction is ready for commit.|
| axoniq.axonserver.replication.min-election-timeout| 1000| Minimal time (in ms.) that a follower waits before moving to candidate state, if it has not received any messages from a leader.|
| axoniq.axonserver.replication.primary-cleanup-delay| 5| Windows only. Delay before forcing the primary segment file from memory when no longer in use.|
| axoniq.axonserver.replication.secondary-cleanup-delay| 30| Windows only. Delay before forcing the other segment files from memory when no longer in use.|
| axoniq.axonserver.replication.segment-size| 16MB| Size of a transaction log file.|
| axoniq.axonserver.replication.snapshot-flow-buffer| 50| Number of unconfirmed install snapshot messages that may be sent to peer.|
| axoniq.axonserver.replication.sync-interval| 1000| Interval to check for files that can be closed.|
| axoniq.axonserver.replication.wait-for-leader-timeout| -1| Timeout to wait for leader when requesting access to event store while leader change in progress, if not set defaults to maxElectionTimeout|
