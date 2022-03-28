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
    $ docker-compose up -d
    ```
4. Stop the nodes
    ```
    $ docker-compose down
    ```