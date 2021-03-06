Forward2Docker
===
Simple utility for auto forwarding ports from Docker container in boot2docker VM to the host.

How it works?
---------
When it started it will listen for Docker events (start and die) and reconfigure port forwarding rules for your boot2docker VirtualBox VM.

Why?
---------
Currently even with Boot2Docker you wouldn't get all Docker experience on your OS X host because
your Docker daemon will run in VM, not on localhost, which means that you will have to use
Boot2Docker VM's IP address instead of "localhost". It causes some fragmentation between native
and non-native Docker users. But we can solve it with "Port forwarding" feature in VirtualBox.

Install
---------
Tool is available in two options:

  1. Go distribution. Install by running 'go get github.com/bsideup/forward2docker'
  1. Binary download. You can download latest binaries here: https://github.com/bsideup/forward2docker/releases/

Usage
---------

  1. Run some Docker container: `$ docker run --name f2dtest -d -p 8000:80 nginx`
  1. Open terminal and run forward2docker: `$ forward2docker`
  1. Ensure that port is mapped to your host: `$ curl http://localhost:8000`
  1. Kill your container: `$ docker kill f2dtest`
  1. Ensure that port is unmapped (you should see 'Connection refused'): `$ curl http://localhost:8000`
  1. Run few more containers and verify that you can access them on localhost
