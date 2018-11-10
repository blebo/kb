# Docker

## General

### List docker volumes by container

From https://www.commandlinefu.com/commands/view/24283/list-docker-volumes-by-container

    docker ps -a --format '{{ .ID }}' | xargs -I {} docker inspect -f '{{ .Name }}{{ printf "\n" }}{{ range .Mounts }}{{ printf "\n\t" }}{{ .Type }} {{ if eq .Type "bind" }}{{ .Source }}{{ end }}{{ .Name }} => {{ .Destination }}{{ end }}{{ printf "\n" }}' {}

## Networking

### macvlan setup

    sudo docker network create \
    -d macvlan \
    --subnet=10.4.4.0/24 \
    --ip-range=10.4.4.64/27 \
    --gateway=10.4.4.1 \
    -o parent=eth0 \
    macvlan0

Example switches to be added to `docker run` command

    --net=macvlan0 \
    --ip=10.4.4.32 \