# emule-docker
eMule over wine, "daemonized" inside a docker

`docker run -p 8080:8080 -p 23732:23732 -p 23733:23733 -v emule_data:/app/config --name emule darioragusa/emule`

## Tags
- `0.72a` (beta)
- `0.70b`, `latest`
- `0.70a`

## Environment variables

- **UID:** UNIX user ID used to create files (Default: `root`)
- **GID:** UNIX group ID used to create files (Default: `root`)
- **DISPLAY_WIDTH:** Web VNC desktop width (Default: `1024`)
- **DISPLAY_HEIGHT:** Web VNC desktop height (Default: `768`)
- **SLEEP_SECONDS:** Wait before run eMule (Default: `5`)
- **EMULE_NICK:** User nickname (Default: `https://emule-project.net`)
- **EMULE_MAX_UPLOAD:** Max upload speed (Default: `1024`, 1 MB/s)
- **EMULE_TCP_PORT:** TCP port (Default: `23732`)
- **EMULE_UDP_PORT:** UDP port (Default: `23733`)
- **EMULE_LANGUAGE:** UI language code. (Default: `1033`)
- **EMULE_CAP_UPLOAD:** Upload capacity (Default: `2048`, 2 MB/s)
- **EMULE_CAP_DOWNLOAD:** Download capacity (Default: `16384`, 16 MB/s)
- **EMULE_RECONNECT:** Automatic reconnect (Default: `1`)
- **EMULE_UPDATE_FROM_SERVER:** Update server list from other servers (Default: `1`)
- **EMULE_HOSTNAME:** Server hostname (Default: )
- **WEB_PASS:** Web UI password hash (Default: `19A2854144B63A8F7617A6F225019B12`, admin)
- **WEB_PORT:** Web UI port (Default: `4711`)

## Ports

- `4711/tcp`: Web control panel (Optional)
- `8080/tcp`: Web VNC desktop
- `23732/tcp`: Edonkey network
- `23733/udp`: Kad network

## Volumes

- `/data/download`: Complete downloads
- `/data/tmp`: Incomplete downloads
- `/app/config`: Emule data

## Credits

This project provides a dockerized environment for running eMule.

eMule is maintained by [irwir](https://github.com/irwir) and available [here](https://github.com/irwir/eMule).

<!--
docker build emule-docker -t darioragusa/emule:latest
docker image prune --filter="dangling=true"
docker run --rm -p 127.0.0.1:8080:8080 darioragusa/emule:latest
docker push darioragusa/emule:latest

docker build emule-docker -t darioragusa/emule:0.72a
docker image prune --filter="dangling=true"
docker run --rm -p 8080:8080 darioragusa/emule:0.72a
docker push darioragusa/emule:0.72a

docker compose lxc:
    security_opt:
      - seccomp=unconfined
-->
