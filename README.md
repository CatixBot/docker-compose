# 🎬 Docker compose

_It is upposed that the steps of [Getting started guide](https://github.com/CatixBot/getting-started-guide) were finished successfuly_

## Deploying nodes

1. Connect to Raspberry Pi via SSH (user: catix, password: catix)
2. Clone this repository
    ```
    $ git clone https://github.com/CatixBot/docker-compose.git && cd docker-compose
    ```
3. Build and run dockerized nodes
    ```
    $ COMPOSE_FILE=docker-compose.deployable-nodes.yml docker-compose up -d
    ```
4. Stop the nodes
    ```
    $ COMPOSE_FILE=docker-compose.deployable-nodes.yml docker-compose down
    ```

## Camera calibration

1. Print checkerboard pattern 'checkerboard_297x210_7x9_25.pdf' on an A4 paper list
2. Attach the pattern to a hard backing (e.g. thick cardboard) to avoid its distortions
3. [Setup X11 forwarding](#Running-GUI-applications-over-SSH-(windows-10))
4. Build and run dockerized nodes
    ```
    $ COMPOSE_FILE=docker-compose.calibration-camera.yml docker-compose up -d
    ```
5. Stop the nodes
    ```
    $ COMPOSE_FILE=docker-compose.calibration-camera.yml docker-compose down
    ```

### Running GUI applications over SSH (windows 10)

1. Install [VcXsrv Windows X Server](https://sourceforge.net/projects/vcxsrv/files/vcxsrv/1.20.9.0/vcxsrv-64.1.20.9.0.installer.exe/download?use_mirror=jztkft&download=&failedmirror=kumisystems.dl.sourceforge.net)
2. Start VcXsrv as a client with default settings
3. In user settings located by path 'C:\Users\%YOUR_USER_NAME%\.shh\config' add your Raspberry Pi if not present and enable X11
    ```
    Host %YOUR_RASPBERRYPI_HOSTNAME%
    HostName %YOUR_RASPBERRYPI_HOSTNAME%
    User catix
    ForwardAgent yes
    ForwardX11 yes
    ForwardX11Trusted yes
    ```
4. Add `DISPLAY` system environment variable with value `localhost:0.0` on your host machine and reboot
5. Now you could simply run any GUI application over SSH using [Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) extensions for VS Code
