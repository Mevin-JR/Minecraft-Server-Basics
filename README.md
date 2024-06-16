# Minecraft Server Basics

A simple guide to get you started on hosting your very own Minecraft server (Java/Bedrock compatible) on your own device. Invite your friends and play together in any version, vanilla or modded.

### Getting Started

There are a few things to do before you can host a server on your device locally:

1. Installation of **Java Development Kit (JDK)**

   Java Development Kit or JDK is required to host/run a Minecraft Server on your device. You can download JDK's from [Oracle](https://www.oracle.com/in/java/technologies/downloads/ "Oracle Downloads"). Here is a list of popular Minecraft versions along with the **minimum** required JDK versions:

   | Minecraft Version | JDK Version (minimum) |
   |:----:|:------:|
   | 1.8  | [JDK 8](https://www.oracle.com/in/java/technologies/javase/javase8-archive-downloads.html)  |
   | 1.12 | [JDK 8](https://www.oracle.com/in/java/technologies/javase/javase8-archive-downloads.html)  |
   | 1.16 | [JDK 8](https://www.oracle.com/in/java/technologies/javase/javase8-archive-downloads.html)  |
   | 1.17 | [JDK 16](https://www.oracle.com/java/technologies/javase/jdk16-archive-downloads.html) |
   | 1.18 | [JDK 17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) |
   | 1.20 | [JDK 17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html) |
   | 1.21 | [JDK 21](https://www.oracle.com/java/technologies/javase/jdk21-archive-downloads.html) |

   **_Note_:** _These JDK versions are a minimum requiredment for the respective Minecraft version. And JDK is only required to HOST a Minecraft server._

2. **Multiplayer Support**

   There are a few ways to enable multiplayer support in your server, for users sharing the same network (WiFi) it's possible to access the server by typing `0` in the "Server Address" or "Direct Connection" in game (The below mentioned method can also be used).

   For users who do not share the same network, using [ngrok](https://ngrok.com/) is the easiest way to allow users to connect. Here's how: 
   * Sign up or log in to [ngrok](https://ngrok.com/) (**Its free**)
   * Download the zip folder by following the instructions provided on your ngrok dashboard
   * Extract the zip folder into the server folder and run the `ngrok.exe` file, a cmd window will popup
   * Copy your auth code from the dashboard (It looks something like this `ngrok config add-authtoken "your-auth-token"`)
   * Execute the auth command in the cmd
   * If your ngrok account is authenticated successfully, you have done everything right

   Before allowing player connection into your server there are a few things to note, everytime ngrok is initialized a new IP address/ Port for the server will be created (This means that every time you run ngrok it will create a new server IP).
   * After authenticating your ngrok account lets create a server address for your server
   * Type in the command `ngrok tcp 25565`
   * A new window with IP details will be displayed, it will look something like this:
   ```
   Session Status             Online                    
   Account                    username (Plan: Free)
   Version                    3.11.0
   Region                     your-region
   Latency                    21ms
   Web Interface              http://127.0.0.1:4040
   Forwarding                 tcp://0.tcp.in.ngrok.io:10956 -> localhost:25565                 
   ```
   * The server address/IP is in the "Forwarding" line, for example in this case the server IP is `0.tcp.in.ngrok.io:10956`
   * Share this IP (along with its port) to other users to let them join your server
   * I recommend turning server whitelist **on** when using ngrok

### Setting up the Minecraft server

Now lets get into setting up your actual Minecraft server. It is advised to store all files related to your server in **one single folder**. 
The "Demo-Server" folder provided in this repo is a sample server set-up using `paper-1.20.6.jar` server software. You can use it to test run a Minecraft server.

1. Downloading server jar

   There are quite a few server jar's you can choose from, some of the most popular are:

   * ![](markdown/images/spigot-icon-16x11.png "Spigot Icon") [Spigot](https://getbukkit.org/download/spigot) - Spigot is a fork of Minecraft server software, known for its efficiency and optimizations. It supports a wide range of plugins and a wide range of customizations.

   * ![](markdown/images/papermc-icon-16x16.jpg "PaperMC Icon") [PaperMC](https://papermc.io/downloads) - PaperMC is a fork of Spigot that focuses on improving performance and fixing bugs. It is known for active development and support for a large number of plugins.

   * ![](markdown/images/forge-icon-16x16.jpg "Forge Icon") [Forge](https://files.minecraftforge.net/net/minecraftforge/forge/) - Forge is a modding platform for Minecraft that allows for extensive modification of the game through mods. Unlike plugins, which are limited to server side changes, Forge mods can affect both client and server, enabling deep alterations to the game mechanics and content.

   * ![](markdown/images/fabricmc-icon-16x16.png "Fabric Icon") [Fabric](https://fabricmc.net/) - Fabric is a lightweight, experimental modding toolchain for Minecraft. It provides modular and flexible platform for mod developers, Fabric is known for its simplicity and ease of use.

2. EULA Agreement

   After downloading the server jar, double-click on the jar file to run it. A few files and folders will appear, one of the file is `eula.txt`. You must agree to Minecrafts [EULA](https://aka.ms/MinecraftEULA) terms to run your server. 
   
   Open `eula.txt` and change the `eula=false` to `eula=true`, save and exit.

3. Launching the server

   Now we are ready to launch the Minecraft server.

   Right-click inside the server folder and create a new text document. Copy the below lines into the file:
   ```
   start cmd.exe /k "ngrok tcp 25565"
   java -Xmx4G -Xms4G -jar minecraft-server.jar nogui
   ```
   This will run both the server and the ngrok connection at the same time.

   * `start cmd.exe /k "ngrok tcp 25565"` will create a new cmd window and run the command "ngrok tcp 25565". 
   
      **Note:** This will only work if the `ngrok.exe` is placed inside the server folder (or the folder which contains the text file). You can exclude this line if you do not want to have an ngrok connection.

   * `java -Xmx4G -Xms4G -jar minecraft-server.jar nogui` will launch the Minecraft server. You can specify how much RAM will be taken up by the server, modify **-Xmx4G** and **-Xms4G** to increase or decrease the amount of RAM. **4G** represents the RAM (in this case 4 GB of RAM will be allocated to the server)