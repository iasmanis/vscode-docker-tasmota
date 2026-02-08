# VSCode devcontainer environment for Tasmota builds

Based on [docker-tasmota](https://github.com/tasmota/docker-tasmota).

Open in VSCode as remote container (Reopen in container). See more [Developing inside a Container](https://code.visualstudio.com/docs/devcontainers/containers).

## Requirements

- Tasmota has to be cloned in `./Tasmota` in workspace root.

### Tasmota Versioning

You can pin a specific Tasmota version for your configuration by creating a file named `tasmota-tag` in your configuration directory (e.g., `configs/my-config/tasmota-tag`). The build script will automatically check out this tag/branch/commit before building.

Example content of `tasmota-tag`:
```
v14.0.0
```

If this file does not exist, you must manually manage the git state in the `Tasmota` directory.

```shell
# Initialize Tasmota code repo if empty
git clone https://github.com/arendst/Tasmota.git ./Tasmota
```

## build.sh

This bash script makes compiling a lot easier without the need to type lengthy commands each time. Create configuration in `./configs/my-config` with:

*   `user_config_override.h`: Your specific Tasmota C definitions.
*   `platformio_override.ini`: (Optional) Custom PlatformIO environment settings. If present, this overrides `Tasmota/platformio_override.ini`.
*   `tasmota-tag`: (Optional) The git tag/ref to build against.

### Usage

Build your Tasmota with `./build.sh <config_name> [pio_args]`.

Examples:

1.  **Standard Build:**
    ```bash
    ./build.sh my-config
    ```

2.  **Specific Environment (e.g., ESP32):**
    ```bash
    ./build.sh kc686-a16 -e tasmota32
    ```

Output images will be in `./Tasmota/build_output/firmware/`.

