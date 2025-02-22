# VSCode devcontainer environment for Tasmota builds

Based on [docker-tasmota](https://github.com/tasmota/docker-tasmota).

Open in VSCode as remote container (Reopen in container). See more [Developing inside a Container](https://code.visualstudio.com/docs/devcontainers/containers).

## Requirements

- Tasmota has to be cloned in ./Tasmota in workspace root. Check out the specific tag required.

### Checking out specific tag from Tasmota

```shell
# Initialize Tasmota code repo
git clone https://github.com/arendst/Tasmota.git ./Tasmota
# In Tasmota directory
cd Tasmota
# Pulls version 13.4.0 code
git checkout --force v13.4.0
```

## build.sh

This bash script makes compiling a lot easier without the need to type lengthy commands each time. Create configuration in `./configs/my-config` with your version of `platformio_override.ini` and `user_config_override.h`.

Build your Tasmota with `./build.sh my-config`. Output images will be in `./Tasmota/build_output/firmware/`.

