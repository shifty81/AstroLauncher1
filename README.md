[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Downloads][downloads-shield]][downloads-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]

<br />
<p align="center">
  <img src="https://raw.githubusercontent.com/ricky-davis/AstroLauncher/master/assets/astrolauncherlogo.ico" width="128px">
  <h3 align="center">AstroLauncher - Dedicated Server Launcher</h3>
  <p align="center">
    An all-in-one server management tool for Astroneer Dedicated Servers.
  </p>

  <p align="center">
    <a href="https://github.com/ricky-davis/AstroLauncher/issues">AstroLauncher Bugs</a>
    ·
    <a href="https://github.com/ricky-davis/AstroLauncher/issues">Request Feature</a>
  </p>
</p>
<img src = "https://user-images.githubusercontent.com/48695279/88715011-3bf09e80-d0e3-11ea-9c3e-f14e6c1758fe.png">
<img src = "https://user-images.githubusercontent.com/48695279/88715683-896d0b80-d0e3-11ea-9a1e-e57e46430c6a.png">
<!-- TABLE OF CONTENTS -->

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Overview](#overview)
- [What does it do?](#what-does-it-do)
- [Quick Start Guide](#quick-start-guide)
  - [Method 1: Using the Pre-built Executable (Recommended for Most Users)](#method-1-using-the-pre-built-executable-recommended-for-most-users)
  - [Method 2: Running from Source](#method-2-running-from-source)
  - [Method 3: Using Docker](#method-3-using-docker)
- [First Time Setup](#first-time-setup)
- [Configuration Guide](#configuration-guide)
  - [INI File Options](#ini-file-options)
  - [Server Configuration](#server-configuration)
  - [Network Configuration](#network-configuration)
- [Web Interface Guide](#web-interface-guide)
  - [Accessing the Web Interface](#accessing-the-web-interface)
  - [Web Interface Features](#web-interface-features)
  - [Setting Up SSL (HTTPS)](#setting-up-ssl-https)
- [Advanced Features](#advanced-features)
  - [Automatic Backups](#automatic-backups)
  - [Scheduled Restarts](#scheduled-restarts)
  - [Discord Integration](#discord-integration)
  - [CPU Affinity](#cpu-affinity)
- [Troubleshooting](#troubleshooting)
  - [Common Issues](#common-issues)
  - [Port Forwarding Problems](#port-forwarding-problems)
  - [Server Not Appearing in Browser](#server-not-appearing-in-browser)
  - [Performance Issues](#performance-issues)
- [Frequently Asked Questions (FAQ)](#frequently-asked-questions-faq)
- [Getting Started (Developer Guide)](#getting-started-developer-guide)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Building an EXE](#building-an-exe)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Overview

This tool is perfect for you if you are hosting your own dedicated server for Astroneer. It has many features to make hosting a lot easier like automatic restarts, advanced logging, and a webinterface.

## What does it do?

1. Automatic initial download and updating of your server to the latest version!
2. Verifies your network settings to check for Port Forwarding/NAT Loopback
3. Automatically sets up the base Config files
4. Fixes the double server problem in the server list
5. Starts, and automatically restarts the server
6. Displays when users join/leave the server
7. Keeps a log of everything in the logs folder
8. Ability to send all logs to a Discord webhook!
9. Auto Restart every X hours
10. Backup Retention for X hours
11. Web Interface w/ login to monitor server data, force saves and restarts, and manage users (kick, ban, whitelist, admin)


## Quick Start Guide

This section provides step-by-step instructions for getting AstroLauncher up and running quickly.

### Method 1: Using the Pre-built Executable (Recommended for Most Users)

This is the easiest method and recommended for most users who just want to run a server.

1. **Download the Latest Release**
   - Go to the [Latest Release](https://github.com/ricky-davis/AstroLauncher/releases/latest) page
   - Download `AstroLauncher.exe`
   - Save it to a folder of your choice (e.g., `C:\AstroServer\`)

2. **First Run**
   - Double-click `AstroLauncher.exe` to run it
   - The launcher will automatically:
     - Download the Astroneer Dedicated Server files (this may take several minutes)
     - Create necessary configuration files
     - Set up the default server settings
   - **Note:** The first run will take longer as it downloads the server files (~2-4 GB)

3. **Configure Your Server** (Optional)
   - Close the launcher (press CTRL+C in the console window)
   - Edit `Astro\Saved\Config\WindowsServer\AstroServerSettings.ini` to customize your server name, password, etc.
   - Edit `Launcher\Config\AstroLauncherConfig.ini` to configure launcher settings (see [Configuration Guide](#configuration-guide))

4. **Start Your Server**
   - Run `AstroLauncher.exe` again
   - Your server should now be running!
   - Check the web interface at `http://localhost:5000` (default)

### Method 2: Running from Source

For developers or users who want more control over the launcher.

1. **Install Prerequisites**
   - Python 3.7 or higher ([Download Python](https://www.python.org/downloads/))
   - pip (comes with Python)

2. **Clone the Repository**
   ```sh
   git clone https://github.com/ricky-davis/AstroLauncher.git
   cd AstroLauncher
   ```

3. **Install Dependencies**
   ```sh
   pip install -r requirements.txt
   ```
   Or using pipenv:
   ```sh
   pip install pipenv
   pipenv install
   ```

4. **Run the Launcher**
   ```sh
   python AstroLauncher.py
   ```
   Or with pipenv:
   ```sh
   pipenv run python AstroLauncher.py
   ```

5. **Specify Custom Server Location** (Optional)
   ```sh
   python AstroLauncher.py --path "C:\Path\To\ASTRONEER Dedicated Server"
   ```

### Method 3: Using Docker

For users who prefer containerized deployments.

1. **Install Docker**
   - Download and install [Docker Desktop](https://www.docker.com/products/docker-desktop)

2. **Build the Docker Image**
   ```sh
   docker build -t astrolauncher .
   ```
   Or use the PowerShell script:
   ```powershell
   .\build_docker.ps1
   ```

3. **Run the Container**
   ```sh
   docker run -d -p 5000:5000 -p 8777:8777/udp -p 27015:27015/udp --name astroneer astrolauncher
   ```

4. **Access the Server**
   - Web Interface: `http://localhost:5000`
   - Game Server: Connect via your public IP on port 8777

## First Time Setup

After launching AstroLauncher for the first time, follow these steps:

1. **Wait for Server Download**
   - The launcher will automatically download the Astroneer Dedicated Server
   - This process can take 5-15 minutes depending on your internet speed
   - Watch the console output for progress

2. **Set Up Web Interface Password**
   - When prompted, set a password for the web interface
   - This password will be hashed and stored in `AstroLauncherConfig.ini`
   - Remember this password - you'll need it to access the web interface

3. **Configure Port Forwarding**
   - The launcher will check your network configuration
   - If port forwarding fails, see [Port Forwarding Problems](#port-forwarding-problems)
   - You need to forward these ports on your router:
     - **8777 UDP** - Game server port
     - **27015 UDP** - Steam query port (for server browser)

4. **Verify Server is Running**
   - Check the console for "Server started successfully" message
   - Access the web interface at `http://localhost:5000`
   - Look for your server in the Astroneer server browser (may take a few minutes to appear)

5. **Configure Server Settings**
   - Edit `Astro\Saved\Config\WindowsServer\AstroServerSettings.ini` to set:
     - Server name
     - Server password (optional)
     - Maximum players
     - Public IP (usually auto-configured)
   - Restart the server for changes to take effect

## Configuration Guide

### INI File Options

Below are the descriptions and defaults for the INI file options. Do not copy/paste this into the INI file, allow the INI file to be automatically generated. Every option must be present and set, and there must be no comments or extra options.

```python
# Enables/Disables Auto Update for the Launcher
AutoUpdateLauncherSoftware = True

# Enables/Disables Auto Update for the Server.
AutoUpdateServerSoftware = True

# Allows the launcher and server to auto update every time the server restarts
UpdateOnServerRestart = True

# Disable the server console popup window.
HideServerConsoleWindow = False

# Disable the Launcher console popup window.
HideLauncherConsoleWindow = False



# Specifies how often the launcher will check for players joining/leaving
ServerStatusFrequency = 2

# Specifies how often the launcher will check for server registration status
PlayfabAPIFrequency = 2

# How many times to allow Playfab to fail before restarting the server
HeartBeatFailRestartServer = 8



# Disable Backup Retention
DisableBackupRetention = False

# How many hours of saves should the launcher retain
BackupRetentionPeriodHours= 72

# Location to backup the save files to
BackupRetentionFolderLocation = Astro\Saved\Backup\LauncherBackups



# Enable auto restart
EnableAutoRestart = False

# Timestamp you want to synchronize with. 00:00 or "midnight" work for midnight. Disable with "False". No quotes.
# Example: If set to 03:35, with AutoRestartEveryHours set to 6, it will restart at 03:35, 09:35, 15:35, and 21:35 every day
AutoRestartSyncTimestamp = 00:00

# After the first restart specified above, how often do you want to restart?
AutoRestartEveryHours = 24



# Disable the Port Forward / NAT Loopback check on startup
DisableNetworkCheck = False

# Always Overwrite the PublicIP setting in AstroServerSettings.ini
OverwritePublicIP = True

# Enable/Disable showing server FPS in console. This will probably spam your console when playing are in your server
ShowServerFPSInConsole = True

# When launched in Administrator Mode, Astro Launcher will attempt to automatically configure the firewall settings
AdminAutoConfigureFirewall = True

# How long to keep server logs before removing them. This does not control debug logs.
LogRetentionDays = 7



# Discord Webhook URL to display AstroLauncher console data in a discord channel
DiscordWebHookURL: str = ""

# Discord Webhook Log Level, all / cmd / chat
DiscordWebHookLevel: str = "cmd"

# This is the URL the webserver serves to interact with the webhook.
RODataURL: str = secrets.token_hex(16)



# Disable the Web Management Server
DisableWebServer = False

# Set the port you want the Web Management Server to run on
WebServerPort = 5000

# Automatically generated SHA256 password hash for the admin panel in the webserver
WebServerPasswordHash =

# The Base URL that the Web Server hosts at. '/astroneer' would be https://example.com/astroneer/ . Must start with and end with a /
WebServerBaseURL = /

# Enable HTTPS for the webserver. If no/wrong Cert/Key files are specified, defaults to False
EnableWebServerSSL = False

# Port you want to use if SSL works
SSLPort = 443

# Paths to Cert and Key files
SSLCertFile =
SSLKeyFile =



# CPU Affinity - Specify logical cores to run on. Automatically chooses if empty.
# ex:
#  CPUAffinity=0,1,3,5,9
CPUAffinity =

```

### Server Configuration

The Astroneer server settings are stored in `Astro\Saved\Config\WindowsServer\AstroServerSettings.ini`. Here are the most important settings:

```ini
[/Script/Astro.AstroServerSettings]
; The name of your server as it appears in the server browser
ServerName=My Astroneer Server

; Password required to join (leave empty for no password)
ServerPassword=

; Maximum number of players (2-8 recommended, max depends on hardware)
MaxServerFramerate=30
MaxServerIdleFramerate=3

; Your public IP address (usually auto-configured by AstroLauncher)
PublicIP=

; Whether the server appears in the public server list
bDisableServerTravel=False

; Server owner name and nickname
OwnerName=ServerOwner
OwnerGuid=

; Denial of Service (DoS) protection settings
DenyUnlistedPlayers=False
VerbosePlayerProperties=True
AutoSaveGameInterval=900

; Backup settings
BackupSaveGamesInterval=7200
ServerAdvertisedName=
```

**Key Settings Explained:**

- **ServerName**: This is what players will see in the server browser. Make it descriptive!
- **ServerPassword**: Leave empty for a public server, or set a password for private servers
- **MaxServerFramerate**: Higher values = smoother gameplay but more CPU usage (30 is recommended)
- **PublicIP**: AstroLauncher usually sets this automatically. Only change if you have issues
- **AutoSaveGameInterval**: How often the game auto-saves (in seconds, 900 = 15 minutes)
- **BackupSaveGamesInterval**: How often to create backup saves (in seconds, 7200 = 2 hours)

### Network Configuration

For your server to be accessible from the internet, you need to configure your network properly.

**Required Ports:**
- **8777 UDP** - Main game traffic
- **27015 UDP** - Steam query port (for server browser)

**Port Forwarding Steps:**

1. **Find Your Local IP Address**
   - Windows: Open Command Prompt and type `ipconfig`
   - Look for "IPv4 Address" under your active network adapter
   - Example: `192.168.1.100`

2. **Access Your Router Settings**
   - Open a web browser and go to your router's IP (commonly `192.168.1.1` or `192.168.0.1`)
   - Log in with your router's admin credentials

3. **Set Up Port Forwarding Rules**
   - Find the "Port Forwarding" section (may be under Advanced Settings or NAT)
   - Create two rules:
     
     **Rule 1:**
     - Service Name: `Astroneer Game`
     - External Port: `8777`
     - Internal Port: `8777`
     - Protocol: `UDP`
     - Internal IP: Your local IP from step 1
     
     **Rule 2:**
     - Service Name: `Astroneer Query`
     - External Port: `27015`
     - Internal Port: `27015`
     - Protocol: `UDP`
     - Internal IP: Your local IP from step 1

4. **Configure Firewall**
   - If you run AstroLauncher as Administrator, it will automatically configure Windows Firewall
   - Otherwise, manually allow `AstroServer.exe` through Windows Firewall
   - Go to Windows Firewall → Allow an app → Add `Astro\Binaries\Win64\AstroServer-Win64-Shipping.exe`

5. **Find Your Public IP**
   - Visit [whatismyip.com](https://www.whatismyip.com) to find your public IP
   - This is the IP address players will use to connect to your server
   - Note: If you have a dynamic IP, it may change when your router restarts

**Testing Your Configuration:**

AstroLauncher automatically checks your network configuration on startup. If the check fails:
- Verify port forwarding rules are correct
- Restart your router
- Check if your ISP blocks server hosting (some ISPs do)
- Try using a VPN or port forwarding service like [ngrok](https://ngrok.com)

## Web Interface Guide

### Accessing the Web Interface

The web interface provides a powerful way to manage your server remotely.

1. **Default Access**
   - Local: `http://localhost:5000`
   - Remote: `http://YOUR_PUBLIC_IP:5000`

2. **Login**
   - Username: `admin` (default)
   - Password: The password you set during first run
   - If you forgot your password, delete the `WebServerPasswordHash` line from `AstroLauncherConfig.ini` and restart

3. **Changing the Port**
   - Edit `WebServerPort` in `AstroLauncherConfig.ini`
   - Default is `5000`, but you can use any available port
   - Remember to update your bookmarks/firewall rules

### Web Interface Features

The web interface is divided into several sections:

**Console Panel:**
- View real-time server logs
- See when players join/leave
- Monitor server status and errors
- Watch FPS and performance metrics

**Server Stats:**
- Current player count
- Server version
- Uptime
- Save game name
- Quick actions: Force Save, Restart Server

**Save Games:**
- List all available save games
- Load different save games
- Delete old saves (admin only)
- Download save files for backup

**Players Panel:**
- **Online Players**: Currently connected players
  - See player names and join time
  - Kick players (admin only)
  - Ban players (admin only)
  - Grant/revoke admin privileges
- **Offline Players**: Recently seen players
  - View player history
  - Pre-emptively ban players
  - Manage whitelist

**Whitelist:**
- Enable/disable whitelist mode
- Add players to whitelist
- Remove players from whitelist
- When whitelist is enabled, only listed players can join

**Admin Functions:**
- Force save the game
- Restart the server
- Manage all players (kick, ban, whitelist)
- Delete save games

### Setting Up SSL (HTTPS)

For secure remote access, you can enable HTTPS:

1. **Obtain SSL Certificates**
   - Use [Let's Encrypt](https://letsencrypt.org/) for free certificates
   - Or use a self-signed certificate (browser will show warning)

2. **Configure AstroLauncher**
   - Edit `AstroLauncherConfig.ini`:
     ```ini
     EnableWebServerSSL = True
     SSLPort = 443
     SSLCertFile = path/to/certificate.crt
     SSLKeyFile = path/to/private.key
     ```

3. **Access Via HTTPS**
   - Local: `https://localhost:443`
   - Remote: `https://YOUR_PUBLIC_IP:443`

4. **Port Forwarding**
   - If accessing remotely, forward the port specified in `SSLPort` on your router
   - If using the default port 443, forward `443 TCP`
   - If using a custom port (e.g., 8443), forward that port instead

## Advanced Features

### Automatic Backups

AstroLauncher can automatically manage save game backups:

**Configuration:**
```ini
DisableBackupRetention = False
BackupRetentionPeriodHours = 72
BackupRetentionFolderLocation = Astro\Saved\Backup\LauncherBackups
```

**How It Works:**
- Backups are created automatically when the game saves
- Backups older than `BackupRetentionPeriodHours` are automatically deleted
- Keeps your disk space under control while maintaining recent backups

**Best Practices:**
- Set `BackupRetentionPeriodHours` to at least 48 hours (2 days)
- Consider longer retention for important servers (72-168 hours)
- Regularly copy important backups to external storage
- Test backup restoration periodically

### Scheduled Restarts

Regular restarts can improve server stability and performance:

**Configuration:**
```ini
EnableAutoRestart = True
AutoRestartSyncTimestamp = 03:00
AutoRestartEveryHours = 24
```

**How It Works:**
- First restart happens at `AutoRestartSyncTimestamp` (3 AM in example)
- Subsequent restarts every `AutoRestartEveryHours` (every 24 hours)
- Example: With settings above, server restarts at 3:00 AM every day

**Advanced Scheduling:**
- Set `AutoRestartSyncTimestamp` to `midnight` or `00:00` for midnight restarts
- Use `AutoRestartEveryHours = 6` for restarts every 6 hours
- Set to `False` to disable synchronization (restarts from launcher start time)

**Tips:**
- Choose restart times when player activity is low
- Announce restart schedule to your players
- Server saves before restarting automatically

### Discord Integration

Send server logs and notifications to Discord:

**Setup:**

1. **Create a Discord Webhook**
   - In Discord, go to Server Settings → Integrations → Webhooks
   - Click "New Webhook"
   - Choose the channel for server logs
   - Copy the Webhook URL

2. **Configure AstroLauncher**
   ```ini
   DiscordWebHookURL = YOUR_WEBHOOK_URL_HERE
   DiscordWebHookLevel = cmd
   ```

3. **Log Levels**
   - `all` - Send all logs (can be spammy)
   - `cmd` - Send command logs (player joins/leaves, admin actions)
   - `chat` - Send chat messages only

**Example Discord Messages:**
- Player joined/left notifications
- Server start/stop events
- Save game events
- Admin actions
- Server errors and warnings

### CPU Affinity

Limit which CPU cores the server uses:

**Configuration:**
```ini
CPUAffinity = 0,1,2,3
```

**When to Use:**
- If you're running multiple game servers on one machine
- To reserve cores for other applications
- To work around CPU-related performance issues

**Examples:**
- `CPUAffinity = 0,1,2,3` - Use first 4 cores
- `CPUAffinity = 4,5,6,7` - Use cores 4-7 (good for multi-server setups)
- `CPUAffinity =` - Empty = use all available cores (default)

**Finding Your Core Count:**
- Windows: Task Manager → Performance → CPU
- Command line: `wmic cpu get NumberOfLogicalProcessors`

## Troubleshooting

### Common Issues

**Issue: "Server failed to start"**
- Check if ports 8777 and 27015 are already in use
- Run as Administrator to allow firewall configuration
- Check the logs in the `Logs` folder for specific errors
- Verify Astroneer Dedicated Server files downloaded correctly

**Issue: "Cannot access web interface"**
- Check if port 5000 is already in use by another application
- Try accessing via `http://127.0.0.1:5000` instead of `localhost`
- Check Windows Firewall settings
- Look for errors in the launcher console

**Issue: "Automatic updates not working"**
- Ensure `AutoUpdateServerSoftware = True` in config
- Check your internet connection
- Try manually updating: Delete server files and restart launcher
- Check if antivirus is blocking downloads

**Issue: "Players can't see my server"**
- Verify port forwarding is configured correctly
- Check that server has registered with Playfab (watch console logs)
- Wait 5-10 minutes for server to appear in browser
- Try direct connection via IP address

**Issue: "High CPU/Memory usage"**
- Lower `MaxServerFramerate` in AstroServerSettings.ini
- Enable CPU Affinity to limit core usage
- Consider upgrading hardware for more players
- Reduce `BackupRetentionPeriodHours` to save disk space

**Issue: "Launcher crashes or closes unexpectedly"**
- Check logs in `Logs` folder for error messages
- Ensure all required ports are available
- Run as Administrator
- Update to latest AstroLauncher version
- Verify Python dependencies are installed correctly (if running from source)

### Port Forwarding Problems

**How to Verify Port Forwarding:**

1. **Use Online Port Checker**
   - Visit [canyouseeme.org](https://canyouseeme.org)
   - Enter port `8777` and check if it's open
   - Repeat for port `27015`

2. **Common Problems:**
   - **Double NAT**: Your ISP provided router + your own router
     - Solution: Enable bridge mode on ISP router, or forward ports on both
   - **CGNAT**: ISP uses Carrier-Grade NAT (common with mobile internet)
     - Solution: Contact ISP for public IP, or use VPN/tunneling service
   - **Firewall Blocking**: Windows or antivirus blocking ports
     - Solution: Add exceptions for AstroServer.exe

3. **Alternative Solutions:**
   - Use [ngrok](https://ngrok.com) or similar tunneling service
   - Use a VPN service with port forwarding support (e.g., PIA, AirVPN)
   - Host on a VPS/cloud server (e.g., AWS, Azure, DigitalOcean)

### Server Not Appearing in Browser

**Step-by-Step Diagnosis:**

1. **Check Server Status**
   - Open web interface at `http://localhost:5000`
   - Verify "Server Status" shows as running
   - Check "Playfab Registration" status

2. **Wait for Registration**
   - Servers can take 5-10 minutes to appear in browser
   - Watch console for "Server successfully registered" message
   - If registration fails repeatedly, check network configuration

3. **Try Direct Connection**
   - In Astroneer, use "Join by IP"
   - Enter your public IP address
   - If this works but browser doesn't show server, it's a Playfab registration issue

4. **Check Server Settings**
   - Ensure `bDisableServerTravel = False` in AstroServerSettings.ini
   - Verify server name is set and not empty
   - Check that PublicIP is correct

5. **Playfab Issues**
   - Playfab services occasionally have problems
   - Check Astroneer Discord for reports of server browser issues
   - Try restarting the server
   - Verify system time is correct (Playfab requires accurate time)

### Performance Issues

**Optimizing Server Performance:**

1. **Adjust Server Settings**
   ```ini
   MaxServerFramerate = 30  ; Lower if CPU usage too high
   MaxServerIdleFramerate = 3  ; Lower when no players online
   ```

2. **Hardware Recommendations**
   - **Minimum**: 2 cores, 4GB RAM, 10GB storage
   - **Recommended**: 4 cores, 8GB RAM, 20GB storage
   - **Optimal**: 6+ cores, 16GB RAM, SSD storage

3. **Enable CPU Affinity**
   - Dedicate specific cores to the server
   - Prevents interference with other processes

4. **Regular Restarts**
   - Enable automatic restarts to clear memory leaks
   - Restart every 12-24 hours for best performance

5. **Backup Management**
   - Reduce `BackupRetentionPeriodHours` if disk space is limited
   - Store backups on separate drive if possible

6. **Network Optimization**
   - Use wired Ethernet instead of WiFi
   - Ensure adequate upload bandwidth (5+ Mbps recommended)
   - Close bandwidth-heavy applications

## Frequently Asked Questions (FAQ)

**Q: Do I need to own Astroneer on Steam to host a dedicated server?**
A: No, the dedicated server is free to download. You don't need to own the game to host.

**Q: Can I run the server on the same PC I play on?**
A: Yes, but ensure your PC meets the hardware requirements for both server and client.

**Q: How many players can join my server?**
A: The game supports 2-8 players. Performance depends on your hardware and network.

**Q: Can I transfer my single-player save to the dedicated server?**
A: Yes, copy your save file from `%localappdata%\Astro\Saved\SaveGames` to the server's save folder.

**Q: Will my server continue running if I close the launcher?**
A: No, the launcher manages the server process. Keep the launcher running.

**Q: Can I host multiple servers on one machine?**
A: Yes, but you'll need multiple IPs or use different ports for each server instance.

**Q: How do I update the server?**
A: If `AutoUpdateServerSoftware = True`, updates are automatic. Otherwise, delete server files and restart.

**Q: Can I run AstroLauncher as a Windows service?**
A: Not directly, but you can use NSSM (Non-Sucking Service Manager) to run it as a service.

**Q: Is there Linux support?**
A: The Astroneer dedicated server is Windows-only. However, you can run it on Linux using Docker (see Method 3 in Quick Start Guide), Wine, or a Windows VM.

**Q: How do I reset the web interface password?**
A: Delete the `WebServerPasswordHash` line from `AstroLauncherConfig.ini` and restart the launcher.

**Q: Can I customize the web interface?**
A: Yes, HTML/CSS files are in the `assets` folder. Modify at your own risk.

**Q: Does the server support mods?**
A: Astroneer doesn't officially support mods on dedicated servers.

**Q: How do I backup my server?**
A: Backups are automatic. Manual backups: copy `Astro\Saved\SaveGames` folder to safe location.

**Q: Can I run the server 24/7?**
A: Yes, that's what it's designed for! Enable auto-restarts for best stability.

**Q: What happens if the server crashes?**
A: AstroLauncher automatically restarts the server when it crashes.

**Q: Can players use their existing characters on my server?**
A: Yes, player progress is tied to their Steam/Xbox account, not the server.

**Q: How do I ban someone?**
A: Use the web interface to ban players. Bans are permanent until removed.

**Q: Can I whitelist specific players?**
A: Yes, use the whitelist feature in the web interface to restrict server access.

**Q: Does the server support crossplay between Steam and Xbox?**
A: Yes, Astroneer supports crossplay between all platforms.

<!-- GETTING STARTED -->

## Getting Started (Developer Guide)

This section is for developers who want to contribute to AstroLauncher or run it from source.

**Recommended: Most people will want to just run the .exe, check out the [Quick Start Guide](#quick-start-guide) or [Latest Release](https://github.com/ricky-davis/AstroLauncher/releases/latest) for a download of the executable.**


<br/>
For developers: To get a local "from-source" copy up and running follow these simple steps:
<br/>
<br/>

### Prerequisites

- Python 3.7
- pip / pipenv

### Installation

1. Clone the AstroLauncher repository

```sh
git clone https://github.com/ricky-davis/AstroLauncher.git
cd AstroLauncher
```

2. Install python modules using pip or pipenv

**Using pip:**
```sh
pip install -r requirements.txt
```

**Using pipenv:**
```sh
pip install pipenv
pipenv install
```

3. Run the launcher

**Using pip:**
```sh
python AstroLauncher.py
```

**Using pipenv:**
```sh
pipenv run python AstroLauncher.py
```

4. (Optional) Specify custom server location

```sh
python AstroLauncher.py --path "C:\steamapps\common\ASTRONEER Dedicated Server"
```

<br />

<!-- USAGE EXAMPLES -->

### Building an EXE

For developers who want to create a standalone executable:

1. Install pyinstaller using one of the following methods

**Using pip:**
```sh
pip install pyinstaller
```

**Using pipenv:**
```sh
pipenv install -d
```

2. Build the executable

**Option 1: Using pyinstaller directly**
```sh
pyinstaller AstroLauncher.py -F --add-data "assets;./assets" --icon=assets/astrolauncherlogo.ico
```

**Option 2: Using the BuildEXE script (recommended)**
```sh
python BuildEXE.py
```
This automatically cleans up build files afterwards.

3. Locate and use the executable
   - The executable will be in the `dist` folder
   - Move `AstroLauncher.exe` to your desired location
   - You can delete the `dist`, `build` folders and `.spec` file after moving the exe

4. Run the executable

```sh
AstroLauncher.exe
```

Or with custom server path:
```sh
AstroLauncher.exe --path "C:\steamapps\common\ASTRONEER Dedicated Server"
```

<br />

<!-- CONTRIBUTING -->

## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<!-- LICENSE -->

## License

Distributed under the MIT License. See `LICENSE` for more information.

<!-- CONTACT -->

## Contact

If you have any questions you can join the [Astroneer discord] (discord.gg/Astroneer) and ask in the #self_host_talk channel

Project Link: [https://github.com/ricky-davis/AstroLauncher](https://github.com/ricky-davis/AstroLauncher)

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[astroneer discord]: https://discord.com/invite/astroneer
[contributors-shield]: https://img.shields.io/github/contributors/ricky-davis/AstroLauncher.svg?style=flat-square
[contributors-url]: https://github.com/ricky-davis/AstroLauncher/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/ricky-davis/AstroLauncher.svg?style=flat-square
[forks-url]: https://github.com/ricky-davis/AstroLauncher/network/members
[downloads-shield]: https://img.shields.io/github/downloads/ricky-davis/AstroLauncher/total
[downloads-url]: https://github.com/ricky-davis/AstroLauncher/releases/latest
[stars-shield]: https://img.shields.io/github/stars/ricky-davis/AstroLauncher.svg?style=flat-square
[stars-url]: https://github.com/ricky-davis/AstroLauncher/stargazers
[issues-shield]: https://img.shields.io/github/issues/ricky-davis/AstroLauncher.svg?style=flat-square
[issues-url]: https://github.com/ricky-davis/AstroLauncher/issues
[license-shield]: https://img.shields.io/github/license/ricky-davis/AstroLauncher.svg?style=flat-square
[license-url]: https://github.com/ricky-davis/AstroLauncher/blob/master/LICENSE.txt
