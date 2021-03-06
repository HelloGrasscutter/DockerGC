# DockerGC
DockerGC is a container that runs Grasscutter (*some anime game* server reimplementation) with just a single command.<br>
[![dockeri.co](https://dockeri.co/image/siakbary/dockergc)](https://hub.docker.com/r/siakbary/dockergc)
## How to create a server:
- Install Docker + MongoDB
- Open Terminal and Enter:
```sh
# Network (just once)
docker network create gc
# Datebase (just once) (db:27017 change ip and delete this if you already have a database)
docker run --rm -it --network gc --name db -d mongo &
# Game server (just once download resources with -f 'yes' after that you can set -f 'no')
docker run --rm -it --network gc -v resources:/home/Grasscutter/resources -p 22102:22102/udp -p 443:443/tcp siakbary/dockergc:debian-dev-3.6 -d 'mongodb://db:27017' -b 'localhost' -f 'yes'
```
or (if you have compose)
```sh
"docker compose up" or "docker-compose up"
```
- Then type "account create yourusername" if there is a new response open the game.
- done 🙂

## How to connect: (PC)
- Before starting, open game first and then logout if you have logged in before and then exit again.
- Install Fiddler then Open Fiddler then click Tools -> Options -> HTTPS -> Check "Capture Https" and "Decrypt Https" then click "Actions" then click "Trues Root" then click yes if a popup appears.
- In Fiddler in "FiddlerScript" tab, copy script from [directed.cs](directed.cs) then click save.
- Login with your username then password with random then login. 🙂

 ## How to connect: (Android) (Fiddler)
- Open Fiddler then click Tools -> Options -> HTTPS -> Check "Capture Https" and "Decrypt Https".
- After you follow it, Go to Tools -> Options -> Connection -> Check "Allow remote computer to connect" and make sure the windows firewall is off and don't forget to change the port other than 8888 (change it like 8887) - [more info](https://www.telerik.com/blogs/how-to-capture-android-traffic-with-fiddler)
- In Fiddler in "FiddlerScript" tab, copy script from [directed.cs](directed.cs) then click save.
- On Phone (Android 7+), Install Magisk+MagiskTrustUserCerts - [more info](https://platinmods.com/threads/intercepting-https-traffic-from-apps-on-android-7-and-above-root.131373/)
- Change proxy on wifi settings with your server ip
- Login with your username then password with random then login. 🙂

## Bro, I don't want to make a server, so can I just join to your server?
Yes, Simple way is to just change localhost in file in pastebin to address server you want to connect to.<br>
For server list please join:<br>
[![DockerGC](https://discordapp.com/api/guilds/964119462188040202/widget.png?style=banner2)](https://discord.gg/tRYMG7Nm2D)

## HELP
| Func | Info |
| ------ | ------ |
| d | is ip address for your database server , note: use computer ip if you want to run on your own pc, no "localhost" because it is ip in container |
| b | ip public server |
| v | ip private server |
| m | Chat Welcome message |
| e | Email Welcome when registering for the first time |
| f | re-download resources if you type "yes" this is useful if you already have a resources folder but there is latest update |
| p | running proxy, if "yes" |

## Port
| Port | Info |
| ------ | ------ |
| 80 | Web Server for HTTP. (Not required) |
| 443 | Web Server for HTTPS. (required) |
| 22102 | Game Communication (udp) (required) |
| 8080 | Mitmproxy (Not required) |

Power by Grasscutter ❤️<br>
> https://github.com/Melledy/Grasscutter