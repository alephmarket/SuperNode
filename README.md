# SuperNode
Super Node - Configuration instructions

## Preconfiguration
Digital Ocean > Droplet > 2gb ram 40GB space

local machine configuration.

If you have multiple ssh key, edit `~/.ssh/config` and to have:

```
...
Host super.node.ip.address
 HostName super.node.ip.address
 IdentityFile ~/.ssh/aleph_ssh_key
...

```

changing `aleph_ssh_key` to yours.


## configurations

```
sudo apt-get update
sudo apt-get upgrade

sudo apt-get install build-essential libssl-dev libdb-dev libdb++-dev libboost-all-dev git libssl1.0.0-dbg

sudo apt-get install libdb-dev libdb++-dev libboost-all-dev libminiupnpc-dev libminiupnpc-dev libevent-dev libcrypto++-dev libgmp3-dev
```

Download source code and compile the daemon
```
wget alefork1.zip from ...
unzip alefork1.zip
cd alefork/src/leveldb
chmod 755 *
cd ..
make -f makefile.unix RELEASE=1
```

* Configuring aleph.conf for each node
```
cd /root/.aleph/
vi aleph.conf
```
Paste this code in aleph.conf

```
rpcuser=rpc_hbridnode
rpcpassword=8cde5e64e7297b1cb4c495d1a
rpcallowip=127.0.0.1
rpcport=4210
listen=1
server=1
daemon=1
```

Then save it

*Running the daemon / node

```
cd ..
cd alefork/src
./alephd
```

you should get `Aleph server is starting`

for more information about it tyype: `./alephd getmininginfo`
