# Dante proxy

Used [Dante](http://www.inet.no/dante/index.html) SOCKS server.
It's installed at [DigitalOcean](https://www.digitalocean.com/)(DO)

[Docker Machine](https://docs.docker.com/machine/overview/) is used. 
[Here](https://docs.docker.com/machine/examples/ocean/) is complete example how to run Docker container in DO droplet.

[vimagick/dante](https://hub.docker.com/r/vimagick/dante/) Docker image is used. Only custom configuration is added in a dockerfile. 

### Server config
In the server used 'username' auth method: auth by system user.

So, to add a new user:

```
$ docker exec -it dante_dante_1 bash
>>> sudo useradd --shell /usr/sbin/nologin proxyuser
>>> sudo passwd proxyuser
>>> [enter pass twice]
>>> exit

$ curl -x socks5h://username:password@<your_DO_ip_address>:1984 https://www.youtube.com
```