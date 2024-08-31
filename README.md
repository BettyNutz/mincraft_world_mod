---

# Minecraft Server Setup with Docker Compose

## Prerequisites

1. **Install Docker and Docker Compose**

   Ensure that you have Docker and Docker Compose installed on your system. You can follow the official Docker installation guide for your operating system.

## Setup Instructions

### 1. Download World Data

- Download your world data zip file to the following directory:
  ```
  /home/yourusername/Downloads/minecraft_packs
  ```
  > **Note:** Ensure this path matches exactly with lines 29 and 30 in the `docker-compose_minecraft_mod.yml` file.

### 2. Unzip the World Data

- Unzip your downloaded world data into the `minecraft_packs` directory.
  
  > **Important:** Some zip files may have different directory structures. If necessary, create a `world` directory inside your unzipped pack directory (e.g., `greek_city`). If your directory structure is incorrect, the server will default to a vanilla setup.

### 3. Organize the World Data

- If required, move the necessary data into the `world` directory. This step is crucial for ensuring the Docker container can locate all the world data when it starts.

### 4. Create Docker Network

- Create a Docker network to keep all your Minecraft servers in one place:
  ```bash
  docker network create minecraft_net
  ```

### 5. Create and Edit Docker Compose File

- Create the Docker Compose file using the following command:
  ```bash
  nano docker-compose_minecraft_mod.yml
  ```
- Paste the necessary code into the `docker-compose_minecraft_mod.yml` file.

### 6. Start the Container

- Start the Minecraft server container with the following command:
  ```bash
  docker compose -f docker-compose_minecraft_mod.yml up -d
  ```

### 7. Wait for the Server to Start

- The container will take a several minutes to start. Once it's up, your Minecraft server will be ready to use.

---
