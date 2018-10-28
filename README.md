![The Lounge](https://raw.githubusercontent.com/thelounge/thelounge.github.io/master/assets/logos/logo/TL_Grey%26Yellow_Vertical_logotype_Transparent_Bg/TL_Grey%26Yellow_Vertical_logotype_Transparent_Bg.png)

#### Docker container for The Lounge, modern web IRC client designed for self-hosting

**[Website](https://thelounge.chat/) • [Docs](https://thelounge.chat/docs) • [Demo](https://demo.thelounge.chat/)**

[![#thelounge IRC channel on freenode"](https://img.shields.io/badge/freenode-%23thelounge-415364.svg?colorA=ff9e18&style=flat-square)](https://demo.thelounge.chat/) [![Total pulls on Docker](https://img.shields.io/docker/pulls/thelounge/thelounge.svg?style=flat-square)](https://hub.docker.com/r/thelounge/thelounge/)

---

### Overview

-   **Modern features brought to IRC.** Push notifications, link previews, new message markers, and more bring IRC to the 21st century.
-   **Always connected.** Remains connected to IRC servers while you are offline.
-   **Cross platform.** It doesn't matter what OS you use, it just works wherever Node.js runs.
-   **Responsive interface.** The client works smoothly on every desktop, smartphone and tablet.
-   **Synchronized experience.** Always resume where you left off no matter what device.

To learn more about configuration, usage and features of The Lounge, take a look at [the website](https://thelounge.chat).

### Running a container

One can get started quickly by using the example [`docker-compose.yml`](https://github.com/thelounge/docker-lounge/blob/master/docker-compose.yml) file. [What is docker-compose?](https://docs.docker.com/compose/)

```sh
$ docker-compose up --detach
```

or starting a container manually:

```
$ docker run --detach \
             --name thelounge \
             --publish 9000:9000 \
             --volume ~/.thelounge:/var/opt/thelounge \
             --restart always \
             thelounge/thelounge:3.0.0-pre.7
```

### Data directory

The Lounge reads and stores all of its configuration, logs and other data at `/var/opt/thelounge`.

_You will probably want to persist the data at this location by using [one of the means](https://docs.docker.com/storage/) to do so._

### Adding users

Users can be added as follows:

```sh
$ docker exec -it <container_name> thelounge add <username>
```

_Note: without [persisting data](#data-directory), added users will be lost when the container is removed._

### Changing the port that The Lounge will be available on

To change the port which The Lounge will be available on, one will have to
change the host port in the port mapping. To make The Lounge available on e.g. port 5000:

```sh
$ docker run --detach \
             --name thelounge \
             --publish 5000:9000 \ # Change host port to listen on port 5000
             --volume ~/.thelounge:/var/opt/thelounge \
             --restart always \
             thelounge/thelounge:3.0.0-pre.7
```

### Environment variables (advanced usage)

You can control how The Lounge is started through the following environment variables;

-   `HOST` (equivalent to the `-c host` CLI option)
-   `PORT` (equivalent to the `-c port` CLI option)
-   `BIND` (equivalent to the `-c bind` CLI option)
