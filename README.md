# NTP configuration
NTP configuration for a local NTP server and NTP clients.

Install
=======
On all the NTP hosts (server or clients) :
```
sudo apt-get install ntp ntpdate
```

Configuration
=============

NTP Server
----------
Create or modify the NTP configuration file:

```
vim /etc/ntp.conf
```

In this way:

```
# ntp server list

# remote
server 0.us.pool.ntp.org
server 1.us.pool.ntp.org
server 2.us.pool.ntp.org
server 3.us.pool.ntp.org

# local
server 127.127.1.0
fudge  127.127.1.0 stratum 10
```

We specify a list of remote servers(we assume that our NTP local server is connected to the internet) and the local server using the loopback address 127.127.1.0

For any details about the ntp.conf file you can check (ntp.conf man)[https://www.freebsd.org/cgi/man.cgi?query=ntp.conf&sektion=5].

On the server we are ready to start the NTP deamon:
```
sudo ntpd
```

NTP clients
-----------

In each of the clients create or modify the NTP configuration file:

```
vim /etc/ntp.conf
```

In this way:

```
server LOCAL_SERVER_IP_ADDR
```

In this way we can synchronize the clients to the local NTP server simply executing:

```
sudo ntpdate-debian
```

