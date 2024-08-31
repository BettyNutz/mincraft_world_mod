Install docker and docker compose

Download your world data to (this must match exacly to line 48 & 50):
/home/yourusername/Downloads/minecraft_packs

Unzip your dl'd world data into minecraft_packs directory
Note that some data in some zip files is in different dir structure inside the zip.

If necessary create world dir inside your unziped pack dir (eg see below greek city)

If necessary move the data into the world dir - You are laying the bed for the docker container to find all the world data as it starts

Create docker network so all your mc servers are in one place: 
docker network create minecraft_net

create compose file
nano docker-compose.yml
add this:

services:
  minecraft:
    # Specifies the Minecraft server service
    image: itzg/minecraft-server:stable
    # Ensures the container always restarts in case of failure
    restart: always
    # Sets the container's name to Greek_City
    container_name: Greek_City
    ports:
      # Maps port 25566 on the host to port 25565 in the container (roll to 25567 if you reuse this code to add another server)
      - "25566:25565"
    environment:
      # Accepts the Minecraft EULA (End User License Agreement)
      EULA: "TRUE"
      # Specifies the world name for the server
      LEVEL_NAME: Greek_City
      # Sets the server's display name
      SERVER_NAME: Greek_City
      # Configures the game mode to creative
      GAMEMODE: creative
      # Sets the difficulty level to easy
      DIFFICULTY: easy
      # Specifies the Minecraft server version so you can change to suit UltimMC
      VERSION: 1.20.4
      # Disables online mode, allowing cracked versions to connect
      ONLINE_MODE: FALSE
    volumes:
      # Maps the world directory on the host to the container
      - /home/yourusername/Downloads/minecraft_packs/Greek_City/world:/data/world
      # Maps the entire Greek_City directory on the host to the container's /data directory
      - /home/yourusername/Downloads/minecraft_packs/Greek_City:/data/
    # Runs the container as user ID 1000 and group ID 1000
    user: "1000:1000"
    networks:
      # Connects the container to an external network named minecraft_net
      - minecraft_net    
networks:
  minecraft_net:    
    external: true

Start container:
docker compose up -d

Wait for it to start
