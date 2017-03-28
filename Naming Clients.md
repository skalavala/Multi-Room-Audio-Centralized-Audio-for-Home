## Giving custom names in the Server

After installing snapcast client software, and connected to the server, the server assigns default names to each client. The default names can be changed by editing the following file:
/var/lib/snapcast/server.json

Before edit the file, make sure you shut down the snap server first, otherwise the changes will be overwritten by the server.

To shut down the snapcast server, run the following command
sudo service stop snapserver

vi /var/lib/snapcast/server.json

Change the names of each client in the JSON file: config -> name
