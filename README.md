# fleetctl Docker container

This is a Busybox-based fleetctl Docker container.
Designed to be small in size so you can quickly and easily run fleet commands
from other Docker containers without needing to install fleetctl in them.

## Usage

`docker run cap10morgan/fleetctl list-units`

## Inside other Docker containers

To use this from within other Docker containers running on a CoreOS host, you
need to let fleetctl talk to the fleet daemon running on the host.
You can run the parent container with `--net=host` or something like this:

`docker run -e FLEETCTL_TUNNEL=docker-bridge-ip cap10morgan/fleetctl list-units`

Either way you'll need to bind mount the host Docker socket on the host as a
volume inside the parent container so that it can run other docker containers.

## License

BSD
