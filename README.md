# Minecraft Server Basics

A simple guide to get you started on hosting your very own Minecraft server (Java/Bedrock compatible) on your own device. Invite your friends and play together in any version, vanilla or modded.

### Getting Started

There are a few things to do before you can host a server on your device locally:

1. Installation of **Java Development Kit (JDK)**

   Java Development Kit or JDK is required to host/run a Minecraft Server on your device. You can download JDK's from [Oracle](https://www.oracle.com/in/java/technologies/downloads/ "Oracle Downloads"). Here is a list of popular Minecraft versions along with the **minimum** required JDK versions:

   | Minecraft Version | JDK Version (minimum) |
   |:----:|:------:|
   | 1.8  | JDK 8  |
   | 1.12 | JDK 8  |
   | 1.16 | JDK 8  |
   | 1.17 | JDK 16 |
   | 1.18 | JDK 17 |
   | 1.20 | JDK 17 |
   | 1.21 | JDK 21 |

   **_Note_:** _These JDK versions are a minimum requiredment for the respective Minecraft version. And JDK is only required to HOST a Minecraft server._

2. **Multiplayer Support**

   There are a few ways to enable multiplayer support in your server, for users sharing the same network (WiFi) it's possible to access the server by typing `0` in the "Server Address" or "Direct Connection" in game (The below mentioned method can also be used).

   For users who do not share the same network, using [ngrok](https://ngrok.com/) is the easiest way to allow users to connect. Here's how: 
   * Sign up or log in to [ngrok](https://ngrok.com/) (**Its free**)
   * Download the zip folder by following the instructions provided on your ngrok dashboard
   * Extract the zip folder and run the `ngrok.exe` file, a cmd window will popup
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

Now lets get into setting up your actual Minecraft server.