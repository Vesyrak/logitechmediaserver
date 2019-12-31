# docker-logitechmediaserver

Docker image for Logitech Media Server (SqueezeCenter, SqueezeboxServer, SlimServer)


Supports airplay function and local squeezelite client!

The host networking mode is required for at least the airplay and spotify functionality (mDNS, zeroconf)

Run with:

```
docker run -t -i --rm=true --net="host" \
      -v "/mnt/user/appdata/LogitechMediaServer":"/config":rw \
	  -v "/mnt/music":"/music":ro \
	  -v "/var/run/dbus":"/var/run/dbus":rw \
      -v "/etc/localtime":"/etc/localtime":ro \
      vesyrak/logitechmediaserver
```

docker-compose:

```
version: "3"
  lms:
    image: vesyrak/logitechmediaserver
    volumes:
      - /etc/localtime:/etc/localtime:ro
      - <music folder>:/music:ro
      - <config folder>:/config:rw
      - /var/run/dbus:/var/run/dbus:rw 
    network_mode: host 
    devices:
      - /dev/snd
    restart: unless-stopped
```

