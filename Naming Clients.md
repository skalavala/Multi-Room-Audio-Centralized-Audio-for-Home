## Setting up Custom Snapcast Client Names

After setting up snapcast clients, they automatically connect to the server - as long as bth server and clients are in the same network/subnet. When a snapcast client gets connected to the snapcast server, the server automatically assigns "defaul"t names to each client. Those default names can be changed by editing the following file on the Raspberry Pi that is running Snapcast Server.

First, you need to stop Snapcast Server, otherwise the setting will be overridden by the server.

```
sudo service snapserver stop
```

```
vi /var/lib/snapcast/server.json
```

Change the names of each client in the JSON file: look for path `config` -> `name`

Start snapserver after making changes:

```
sudo service snapserver start
```

The clients will automatically connect when the server is available.

[Back to home page](README.md)
