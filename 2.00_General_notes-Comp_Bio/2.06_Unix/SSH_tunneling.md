
# SSH_tunneling
Topic: #Unix #ComputerScience #Informatics
Date: 2022-07-14

---

## Summary
This is a note of SSH tunneling

## Notes
- *SSH client* is a program for logging into a remote machine  and execute commands on that machine. Provides *secure* and *encrypted* communication. 
- Usually a destination is provided as *[user@]hostname*.
- Useful flags are:
		- *-L* : which binds addresses, either *TCP ports* or *Unix sockets* on the local (client) host are to be forwarded to the given host and port, or Unix socket, on the remote site. Briefly, it allocates a socket to listen to either a *TCP port* on the local side or a *Unix socket*. When the connection is made, it's forwarded over the secure channel, and a connection is made to *host port hostport* or *Unix socket remote_socket*, from the remote machine.
		- *-N*: Do not execute a remote command, usefull for forwarding ports.
- Quick example: When i open up Rstudio the following ssh tunneling is required
```
ssh -N -L 8787:cn12.cluster.loc:47348 ieoID@remoteServer
```
This one connects my *Host* (cn12....) and  *Port* (47348) location to my *ID* and remote server *hostname* aka our PBS cluster to which i'm tunneling to.

## Questions
- Item



