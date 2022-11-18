DockerWithGui
=============
This repo will provide you a container with the XFCE graphical interface.

It's based on accetto/ubuntu-vnc-xfce, that you can find on him repository at https://github.com/accetto

Inside the container, you can install any graphical app. By the way, you can use the version with Wine to install a Windows application.

It's use XFCE4, a very lightweight graphical interface for linux, and NoVNC, a http server with VNC protocol.

<br>

Screenshots
------------
<img src="https://github.com/hudsonventura/DockerWithGui/raw/main/screenshots/screen1.png" height="100%" title="hover text">
<img src="https://github.com/hudsonventura/DockerWithGui/raw/main/screenshots/screen2.png" height="100%" title="hover text">

<br>

Requirements
------------
<li>A distro Linux;
<li>Docker and Docker Compose
<li>A browser to access NoVNC via http or a VNC client.
<li>Some knowledg about VNC and Wine (if you use the Wine version)

<br>

See docker-compose.yml file.
----------------------------

  

``` yaml
version: '3'
services:

  gui:
    #build: .
    image: hudsonventura/dockerwithgui:latest
    #image: hudsonventura/dockerwithgui:latest_withwine
    restart: always
    ports:
      # port for connect via VNC app
      - "5901:5901"
      #port for conect via noNVC (via http browser like http://localhost:6901)
      - "6901:6901"
    environment:
      # the password must be up to 8 charactrers. This is limited by VNC Protocol
      - "VNC_PW=DWGui"
```
<br>


To operate the container

```bash
sudo docker compose up
sudo docker compose down
```

<br>


If you want to compile you image ...
------------------------------------

Change docker compose file to get local image:

Uncomment #build: . from docker-compose file.
  

``` bash
sudo docker compose --build
```

<br>

Inside container ...
------------------------------------
``` bash
apt update
apt install firefox
```

<br>

To remember
-----------

If you want to persist some information, you must use volumes.

When you destroy the container with command sudo docker compose down, all information inside the container also will be destroyed.

<br>

To personalize
--------------

If you want to create a image with some apps installed, edit the Dockerfile or create a new Dockerfile and put the image hudsonventura/dockerwithgui:latest or hudsonventura/dockerwithgui:latest_withwine in FROM.

<br>

Documentation
--------------
Full documentation is available at https://github.com/hudsonventura/DockerWithGui.

Credits: https://github.com/accetto