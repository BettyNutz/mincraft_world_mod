Install docker and docker compose

Download your world data zip file to: (Note: This must match exacly to line 29 & 30 in the yml file):
/home/yourusername/Downloads/minecraft_packs

Unzip your dl'd world data into minecraft_packs directory
Note that some data in some zip files is in different dir structure inside the zip.
If necessary create world dir inside your unziped pack dir (eg see below greek city) if you get your dir struicture wrong you'll just build a vanilla server

If necessary move the data into the world dir - You are laying the bed for the docker container to find all the world data as it starts

Create docker network so all your mc servers are in one place: 
docker network create minecraft_net

create compose file
nano docker-compose_minecraft_mod.yml 

Paste in docker-compose_minecraft_mod.yml code

Start container:
docker compose -f docker-compose_minecraft_mod.yml up -d

Wait for it to start
