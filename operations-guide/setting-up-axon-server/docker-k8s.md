# Axon Server Enterprise in containers 

> **Note**
>
> This section describes Axon Server Enterprise version 4.3 onwards.
>
To run Axon Server Enterprise in containers you can use the axonserver-enterprise docker image. 
This docker image starts Axon Server with the following properties predefined:

````bash
axoniq.axonserver.event.storage=/eventdata
axoniq.axonserver.snapshot.storage=/eventdata
axoniq.axonserver.controldb-path=/data
axoniq.axonserver.pid-file-location=/data
axoniq.axonserver.replication.log-storage-folder=/data/replicationlog
logging.file=/data/axonserver.log
logging.file.max-history=10
logging.file.max-size=10MB
````
The directories /eventdata and /data are volumes outside of the image. The data directory is relatively small, it 
contains the controldb, the transaction logs for replication and the application log files of AxonServer. The eventdata 
directory contains the event store so it may become much larger. 

If you want to configure any other properties you can either define them in an axonserver.properties
file that you mount in /config/axonserver.properties or pass them through environment variables.  

Axon Server Enterprise needs a license file to start. As this is not part of the docker image, it must be made available
to the container upon creation. You can do this by mounting the license file to a specific location, for instance /config/axoniq.license, 
and then pass the environment variable AXONIQ_LICENSE=/config/axoniq.license to the docker container.

If you want to enable access control for you will have to start Axon Server with a known system token. This system token 
is required to perform administrative tasks on the Axon Server cluster through the command line. Axon Server generates a new
system token on each restart of a node by default, but if you provide a file with a system token, this will be used.
You will also have to set the internal-token property for all nodes.
```bash
axoniq.axonserver.accesscontrol.enabled=true
axoniq.axonserver.accesscontrol.internal-token=this-is-the-internal-token-for-axonserver
axoniq.axonserver.accesscontrol.systemtokenfile=/config/systemtoken
```
     

