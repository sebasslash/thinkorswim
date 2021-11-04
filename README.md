# ThinkOrSwim Image

This repository provides a way to run TD Ameritrade's ThinkOrSwim in a Docker container.

## Requirements

- Docker
- X Server

## Build

This script builds your image.

```bash
./build.sh
```

## Run

This script brings up a container, allowing you to login to the application.

```bash
./run.sh
```

You'll have to run this (outside of your container), unless you've already added non-network connections to xserver's ACL:

```bash
xhost +local:$(id -un)
```

### If needed, Post-Installation Steps

I figured I could probably include a script in the image, but for now I'll highlight the steps here:

It looks like during the image build, thinkorswim doesn't install properly (or I simply found the binary after re-running the installer). So, after running `./run.sh`, as a sanity check:

```
cd /
./thinkorswim_installer.sh
```

You should see a window for the installer; follow the steps.

The ToS binary should be located in: `/usr/local/thinkorswim/`

Feel free to add it to your `$PATH`, and maybe a script that runs on shell login!

Happy Trading!
